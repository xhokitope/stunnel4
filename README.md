# stunnel4
Conexion VPN por medio de STUNNEL4

# INICIO:

sudo su

cd

apt-get update && apt-get upgrade -y

apt-get install stunnel4 -y && apt-get install stunnel -y

# Descargar é Instalar El Certificado TLS:

openssl genrsa 1024 > stunnel.key && openssl req -new -key stunnel.key -x509 -days 1000 -out stunnel.crt && cat stunnel.crt stunnel.key > stunnel.pem && mv stunnel.pem /etc/stunnel/

* Darle [ENTER] a todo


# Crear el Archivo stunnel.conf:

Usar su Editor preferido NANO ó VIM

vim /etc/stunnel/stunnel.conf

nano /etc/stunnel/stunnel.conf

# Crear las siguientes lineas:

cert = /etc/stunnel/stunnel.pem

client = no

socket = a:SO_REUSEADDR=1

socket = l:TCP_NODELAY=1

socket = r:TCP_NODELAY=1

[stunnel]

connect = 127.0.0.1:22

accept = 443


* Guadar el Archivo con:

[CONTROL] + [X]
yes
[ENTER]

* Puede cambiar el puerto 443 por el puerto que quiera.

* Opcional: Puede Descargar el Archivo stunnel.conf Desde el Siguiente Link:

wget https://www.dropbox.com/s/4har70lyjpng2c3/STUNNEL.zip && unzip STUNNEL.zip && mv stunnel.conf /etc/stunnel && nano /etc/stunnel/stunnel.conf

# Editar el Archivo STUNNEL4:

nano /etc/default/stunnel4

Solo Cambiar el 0 por 1 en la siguiente linea del archivo:

ENABLED=0 (Cambiar por el numero 1)

ENABLED=1

Guardar el cambio:

[CONTROL] + [X]
yes
[ENTER]

* Opcional: Puede Descargar el Archivo stunnel4 Desde el Siguiente Link:

wget https://www.dropbox.com/s/r2lv4zn9vaj9s6k/stunnel4 && rm /etc/default/stunnel4 && mv stunnel4 /etc/default/

# Activar el Servicio STUNNEL4:

service stunnel4 restart

# Detener el Servicio STUNNEL4:

service stunnel4 stop

# Iniciar el Servicio STUNNEL4:

service stunnel4 start

# Ver el Estado del Servicio STUNNEL4:

service stunnel4 status

# Revizar los Puertos y Servicios Activos:

netstat -tnlp

@XhokitoPe

* Compatible con Ubuntu 14, 16, 18



















