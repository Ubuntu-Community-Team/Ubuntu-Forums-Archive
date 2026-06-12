---
title: "Local server with apache-phpmyadmin for joomla"
date: 2015-03-06
forum: General Help
---

### Post by simfomet on 2015-03-06
Hi,

    I'm using xubuntu 14.10 and I would like to install a local server with ***mysql-server**, **apache** y **phpmyadmin ***to built a website with joomla. I use first xampp but I have problems with the permissions on  opt/htpdocs directories. Surfing the website I found this info, it's in spanish but I thimk it's easy to understand:

[I]te sugiero que no uses XAMP, aunque ese no es el objetivo de tu pregunta, pero te explico porqué...
Linux ya trae predeterminadamente todo como para que montes un servidor  web en tu máquina, así que es mejor lo que trae él que usar otras  cosas... Para eso solo tienes que acceder al Gestor de Paquetes Synaptic  e instalas **mysql-server**, **apache** y **phpmyadmin** ellos solos se encargan de resolver las dependencias. Luego accedes normalmente a tu locahost y te saldrá una página que dice **It works**... que está en **/var/www/**  y a la cual solo puedes acceder a ver, porque está bajo permisos de  root, entonces lo que puedes hacer es en tu Home (/home/usuario/) creas  una carpeta donde guardarás todos tus proyectos y lo que haces es hacer  links desde **/var/www/ **hacia esa carpeta y supongamos que la nombras webserver, lo que tienes que hacer es esto desde un Terminal estando en **/var/www/** y teniendo previamente creada una carpeta en /home/usuario/webserver/misitio/
 [/I]* Código: *[LEFT][I]sudo ln -s /home/usuario/webserver/misitio/ misitio
// aquí te va a pedir el password de root
[/I][/LEFT]

[I]Esto te creará un link por el cual podrás acceder vía web de esta manera [http://localhost/misitio](http://localhost/misitio)
También podrás acceder a phpmyadmin normalmente [http://localhost/phpmyadmin](http://localhost/phpmyadmin)[/I]

It doesn't work for me. Moreover when I'm in phpmyadmin I have the message The control user connection failed in defined setting. I don't know what to do.

---

