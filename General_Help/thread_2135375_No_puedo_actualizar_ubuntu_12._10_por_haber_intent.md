---
title: "No puedo actualizar ubuntu 12. 10 por haber intentado instalar plugins unsuported"
date: 2013-04-14
forum: General Help
---

### Post by Majungatholus on 2013-04-14
[COLOR=#000000][FONT=sans-serif]Hola: [/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]Ya tenia instalado Compiz con plugins extra y he seguido el tutorial de el foro sobre como instalar plugins unsuported de compiz, introduje los siguientes comandos: [/FONT][/COLOR]

[COLOR=#000000][FONT=sans-serif]sudo add-apt-repository ppa:compiz [/FONT][/COLOR]

[COLOR=#000000][FONT=sans-serif]sudo apt-get update [/FONT][/COLOR]

[COLOR=#000000][FONT=sans-serif]sudo apt-get upgrade [/FONT][/COLOR]

[COLOR=#000000][FONT=sans-serif]Hasta aca todo correcto pero al ingresar el siguiente comando: [/FONT][/COLOR]

[COLOR=#000000][FONT=sans-serif]sudo apt-get install compiz-fusion-plugins-unsupported [/FONT][/COLOR]

[COLOR=#000000][FONT=sans-serif]me aparece en la terminal: [/FONT][/COLOR]

[COLOR=#000000][FONT=sans-serif]Leyendo lista de paquetes... Hecho [/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]Creando árbol de dependencias       [/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]Leyendo la información de estado... Hecho [/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]E: No se ha podido localizar el paquete compiz-fusion-plugins-unsupported [/FONT][/COLOR]

[COLOR=#000000][FONT=sans-serif]como puedo solucionar esto, ya que aparte no puedo actualizar ubuntu con el centro de actualizacion del software, ya que me aparece [/FONT][/COLOR]

[COLOR=#000000][FONT=sans-serif]Fallo al descargar la informacion del repositorio [/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]compruebe su coneccion a internet (internet esta conectado y todo bien) [/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]en detalles aparece:

[/FONT][/COLOR][COLOR=#000000][FONT=sans-serif]W:Failed to fetch [/FONT][/COLOR][http://ppa.launchpad.net/compiz/ppa/ubuntu/dists/quantal/main/source/Sources](http://ppa.launchpad.net/compiz/ppa/ubuntu/dists/quantal/main/source/Sources)[COLOR=#000000][FONT=sans-serif]  404  Not Found [/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif], W:Failed to fetch [/FONT][/COLOR][http://ppa.launchpad.net/compiz/ppa/ubuntu/dists/quantal/main/binary-amd64/Packages](http://ppa.launchpad.net/compiz/ppa/ubuntu/dists/quantal/main/binary-amd64/Packages)[COLOR=#000000][FONT=sans-serif]  404  Not Found [/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif], W:Failed to fetch [/FONT][/COLOR][http://ppa.launchpad.net/compiz/ppa/ubuntu/dists/quantal/main/binary-i386/Packages](http://ppa.launchpad.net/compiz/ppa/ubuntu/dists/quantal/main/binary-i386/Packages)[COLOR=#000000][FONT=sans-serif]  404  Not Found [/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif], E:Some index files failed to download. They have been ignored, or old ones used instead. [/FONT][/COLOR]


[COLOR=#000000][FONT=sans-serif]¿Como hago para solucionar esto, se que este problema se da por que no se instalaron los plugins unsupported por que no se encontraron? [/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]Desearia instalarlos, en caso contrario como hago para volver a como tenia mi compiz y centro de descargas antes [/FONT][/COLOR]

[COLOR=#000000][FONT=sans-serif]Agradesco de antemano su ayuda[/FONT][/COLOR]

---

### Post by Stonecold1995 on 2013-04-14
Este es un foro Inglés solamente.

It would probably be more helpful if you were to run your text through Google Translate so other people can understand you more easily.

Anyways, without knowing much about your problem, have you tried just using the compiz ppa ([https://launchpad.net/~compiz/+archive/ppa](https://launchpad.net/~compiz/+archive/ppa))?  In the Overview of published packages section, it says that "compiz-fusion-plugins-unsuppored" is one of the included packages already.

---

### Post by r-senior on 2013-04-14
> Already installed Compiz with extra plugins I have followed the forum tutorial on how to install compiz plugins unsuported, introduced the following commands:

```
sudo add-apt-repository ppa: compiz
```

That PPA is only showing distributions up to Maverick (Ubuntu 10.10):

*Eso PPA sólo se muestra la distribución hasta Maverick (Ubuntu 10.10).*

```
http://ppa.launchpad.net/compiz/ppa/ubuntu/dists/
```

---

### Post by Majungatholus on 2013-04-14
It means that i must write


sudo add-apt-repository ppa: compizand after in the terminal just put
[http://ppa.launchpad.net/compiz/ppa/ubuntu/dists/??????????????](http://ppa.launchpad.net/compiz/ppa/ubuntu/dists/??????????????)

---

### Post by Majungatholus on 2013-04-14
It means that i must write


sudo add-apt-repository ppa: compizand after in the terminal just put
[http://ppa.launchpad.net/compiz/ppa/ubuntu/dists/??????????????](http://ppa.launchpad.net/compiz/ppa/ubuntu/dists/??????????????)

---

