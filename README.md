# C3 T14 Docker
## Links
- [Docker](https://www.docker.com/): Web oficial docker.
- [Docker HUB](https://hub.docker.com/): Para buscar imagenes.

## Comandos terminal
Busca imagenes en docker hub. Se muestran las oficiales con un *[OK]*
```powershell
docker search hello-world
```

Descarga la imagen seleccionada
```powershell
docker pull hello-world
```

Muestra las imagenes descargadas
```powershell
docker images
```

Crea un contenedor a partir de la imagen (no lo ejecuta)
```powershell
docker run hello-world
```

Muestra los contenedores activos
```powershell
docker ps -a
```

Crea contenedor con un nombre
```powershell
docker run --name ejemplo1 hello-world
```

Crear sesion interactiva
```powershell
docker run --name ub02 -it ubuntu bash
```

Sale del contenedor que teniamos iniciado
```powershell
exit
```

Iniciar imagen docker
```powershell
docker start ub02
```
## Diferencia docker pull y docker run
- **docker pull**: Este comando se utiliza para descargar una imagen de Docker desde un registro de contenedores, como Docker Hub.
- **docker run**: Este comando se utiliza para crear y ejecutar un nuevo contenedor basado en una imagen de Docker que ya tienes en tu máquina local, en caso de no tenerla, Docker intentará descargarla automáticamente.

## Crear contenedor MySQL
[Hub MySQL](https://hub.docker.com/_/mysql)

Estructura
```powershell
docker run --name some-mysql -e MYSQL_ROOT_PASSWORD=my-secret-pw -d mysql:tag
# El tag es la version, por defecto es la ultima
# (-e) -> Hace referencia a las variables de entorno
    # Ejemplo: -e MYSQL_ROOT_PASSWORD=my-secret-pw
```

Ejemplo
```powershell
docker run --name mysql-server -e MYSQL_ROOT_PASSWORD=root -d mysql
```

Configuración con puerto
```powershell
docker run -p 3306:3306 --name mysql-server -e MYSQL_ROOT_PASSWORD=root -d mysql
# (-p) -> Definimos que el puerto de docker y el nuestro es el mismo
# (--name) -> Definimos el nombre del contenedor "mysqul-server"
# Ingresamos la variable de entorno que queramos, en este caso la contraseña, que le hemos puesto (-e) es "root"
```
Ejemplo con otro puerto diferente
```powershell
docker run -p 33060:3306 --name mysql-server-2 -e MYSQL_ROOT_PASSWORD=root -d mysql
```

Parar contenedor
```powershell
docker stop mysql-server
```

Iniciar contenedor
```powershell
docker start mysql-server
```