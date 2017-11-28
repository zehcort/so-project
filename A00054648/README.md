## Miniproyecto Sistemas Operativos

**Universidad ICESI**  
**Curso:** Sistemas Operativos  
**Docente:** Daniel Barragán C.  
**Tema:**  Servicios web  

**Nombre del estudiante:** Luis Alejandro Tróchez / Diego Lamus  
**Código:** A00054648 / A00320776  
**Enlace repositorio:** https://github.com/zehcort/so-project

## Objetivos
* Desplegar una aplicación en un servidor que ejecuta el sistema operativo Linux
* Realizar los ajustes y depuración necesarios para desplegar una
aplicación en Linux
* Realizar aplicaciones para obtener información del sistema operativo

## Descripción
Para el despliegue de una aplicación en un servidor se requiere conocer los procedimientos necesarios relacionados con la configuracion de las interfaces de red, ajustes de seguridad, instalación de dependencias, usuarios y herramientas de depuracíon del sistema operativo.

El siguiente proyecto consiste en el despliegue de una aplicación web para obtener información del sistema operativo (La aplicación debe permitir consulta uso de CPU, memoria y espacio en disco). Para este propósito se debe emplear el sistema operativo Ubuntu Server 16.04, el microframework flask y ambientes virtuales.

<p align="center">
  <img src="vista-despliegue.png" alt="webservice architecture"/>
</p>

## Actividades
* Nombre y código de todos los integrantes del grupo (máximo 3) (5%)
* Ortografía y redacción (5%)
* Descripción breve de los pasos para cumplir con lo solicitado
  * Sistema operativo Ubuntu Server 16.04 (10%)
  * Configuración de interfaces de red (10%)
  * Configuración de puertos (10%)
  * Instalación de dependencias (10%)
  * Creación de ambientes virtuales (10%)
  * Aplicación en Python (10%)
  * Validación de la ejecución del servicio (netstat) (10%)
* Pruebas de la solución a través de capturas de pantalla. Puede emplear si lo desea una herramienta de captura de pantalla a formato .gif (10%)
* El informe debe ser entregado en formato pdf a través del moodle y el informe en formato README.md debe ser subido a un repositorio de github. El repositorio de github debe ser un fork de https://github.com/ICESI-Training/so-project y para la entrega deberá hacer un Pull Request (PR) respetando la estructura definida. El código fuente y la url de github deben incluirse en el informe (10%).  
  
## Desarrollo 

Como se solicita, en el siguiente informe se explicará y demostrará el montaje y funcionamiento de un servicio web que muestra la información del sistema, corrido sobre una máquina con sistema operativo Ubuntu Server.

**1. Instalación ubuntu server uy configuración de interfaces de red**

El primer paso para comenzar con la actividad es la instalación y configuración del servidor Ubuntu. Para ello creamos una maquina virtual e instalamos ubunto 16.04, como se evidencia en el ancabezado de la imagen a continuación. Luego, ajustamos los adaptadores de red en modo puente; lo hicimos antes de terminar la instalación de la maquina por lo que se crearon los archivos de configuración y solo fue necesario cambiar la siguiente linea:
    
     ONBOOT=yes


![][0]


**2. Configuración de puertos**

El siguiente paso que se realizó consiste en habilitar los puertos para que se puedan hacer solicitudes a los servicios correctamente. Se habilitó el puerto 8080, ya que va a ser el puerto por e cual se va a configurar el servicio. Para lograrlo se ejecutaron los siguientes comandos:

    firewall-cmd --zone=public --add-port=8080/tcp --permanent
    firewall-cmd --reload

**3. Instalación de dependencias**

A continuación, se procedió a instalar, configurar e iniciar el servidor SSH. Todo esto con el objetivo de poder conectarse de manera remota y trabajar con mayor facilidad desde un cliente SSH como PUTTY.

![][1]

![][2]

Una vez realizado lo anterior, se  revisó la dirección IP de la máquina y se procedió a establecer conexión desde PUTTY.

![][3]

![][4]

Posterior a esto, se comenzó a realizar la instalación de las librerías y aplicativos necesarios para montar el servicio web. 
En primer lugar, se instaló el instalador en lenguage python y se hizo un update a las librerías instaladas.

![][5]

![][6]

Después, se procedió a instalar el creador de entornos virtuales, con ayuda del instalador de python. Se hizo la actualización de versión que recomendó.

![][7]



**4. Creación de ambiente virtual**

Una vez instaladas estas librerías, se procedió a crear el ambiente virtual para la ejecución del proyecto, llamado elAmbiente. Seguido de esto, se activó.

![][8]

![][9]

Ya situados dentro del ambiente virtual creado, se instaló Flask dentro de él.

![][10]



**5. Aplicación en python**

Una vez terminados los pasos anteriores, ya está todo preparado para montar el servicio web solicitado en la actividad. Para tal fin, se crea un archivo .py que contiene el programa que se correrá para desplegar el servicio. En el se describen las direcciones donde se situará cada parte de la información del sistema. Este servicio se compone de una página de Bienvenida, acompañada de otras donde se mostrará la información de la CPU, el uso de la memoria, uso del disco y la información de la red. 

![][11]

![][12]

Una vez listo esto, ya podemos correr el servicio. En su ejecución se desplegarán todas las consultas HTTP que se realicen al servidor y la respuesta del mismo.

![][13]

Por último, se enseña el resultado de las consultas HTTP en el servicio WEB. Todo esto se realizó desde otra Máquina CentOS con el comando curl.

![][14]

![][15]

![][16]

![][17]


## Referencias
* https://askubuntu.com/questions/294946/how-to-change-root-password-in-ubuntu
* https://www.redeszone.net/gnu-linux/servidor-ssh-en-ubuntu/





[0]: 0.PNG
[1]: 1.PNG
[2]: 2.PNG
[3]: 3.PNG
[4]: 4.PNG
[5]: 5.PNG
[6]: 6.PNG
[7]: 7.PNG
[8]: 8.PNG
[9]: 9.PNG
[10]: 10.PNG
[11]: 11.PNG
[12]: 12.PNG
[13]: 13.PNG
[14]: 14.PNG
[15]: 15.PNG
[16]: 16.PNG
[17]: 17.PNG


