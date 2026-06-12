---
title: "Acroread not working"
date: 2005-03-23
forum: General Help
---

### Post by xy77 on 2005-03-23
Hi there.

I cannot start Adobe Acrobat Reader. It complaints that:
```
$ acroread
/usr/bin/acroread: line 12: /usr/lib/Acrobat5/bin/acroread: file or directory not found
```

What's wrong?

/usr/lib/Acrobat5/bin only contains acroread.sh, which when executed complaints with "ERROR: Cannot find installation directory"

Any help would be appreciated.

- David (xy77)

---

### Post by Nekrataal on 2005-03-23
[Acrobat solution](http://www.ubuntulinux.org/wiki/HacerQueFuncioneAdobeAcrobatReader) 

there you can find the solution to your problem...but ill recomend you to install Acrbat Reader 7.0 .... Read here: 
[Acrobat reader 7.0 linux](http://guia-ubuntu.org/doku.php?id=aplicaciones:oficina#como_instalar_adobe_reader_7) 

The links are in spanish, but both of the webpages can be translated...

---

### Post by xy77 on 2005-03-23
Hey, thank you!

here's the relevant stuff to repair Acroread 5 (not testet, I went for 7.0):
```

$ cd /usr/lib/Acrobat5/bin
$ mv acroread.sh acroread

```
edit /usr/lib/Acrobat5/bin/acroread
find "install_dir=REPLACE_ME" and set it to "install_dir=/usr/lib/Acrobat5/Reader"

installing adobe acrobat reader 7.0 on linux
```

$ wget ftp://ftp.adobe.com/pub/adobe/reader/unix/7x/7.0/enu/AdbeRdr70_linux_enu.tar.gz
$ tar xzvf AdbeRdr70_linux_enu.tar.gz
$ cd AdobeReader
$ sudo ./INSTALL
$ sudo ln -s[COLOR=Red]f[/COLOR] /usr/local/Adobe/Acrobat7.0/bin/acroread /usr/bin

```
(added f-flag to ln, because /usr/bin/acroread exists)

install browser plugin:
```

$ cd /usr/local/Adobe/Acrobat7.0/Browser
$ ./install_browser_plugin
[COLOR=Red]$ sudo ln -sf /usr/local/Adobe/Acrobat7.0/Browser/intellinux/nppdf.so /usr/lib/mozilla-firefox/plugins/nppdf.so[/COLOR]


```

it's still downloading (about 40Mb)

- David (xy77)

---

### Post by Technoviking on 2005-03-23
[QUOTE=Nekrataal][Acrobat solution](http://www.ubuntulinux.org/wiki/HacerQueFuncioneAdobeAcrobatReader) 

there you can find the solution to your problem...but ill recomend you to install Acrbat Reader 7.0 .... Read here: 
[Acrobat reader 7.0 linux](http://guia-ubuntu.org/doku.php?id=aplicaciones:oficina#como_instalar_adobe_reader_7) 

The links are in spanish, but both of the webpages can be translated...[/QUOTE]
Has any seen Acrobat 7 debs yet?

---

### Post by cutOff on 2005-03-23
[QUOTE=Mike Basinger]Has any seen Acrobat 7 debs yet?[/QUOTE]
Nope, I think.

[ftp://ftp.adobe.com/pub/adobe/reader/unix/7x/7.0/enu/](ftp://ftp.adobe.com/pub/adobe/reader/unix/7x/7.0/enu/)

---

### Post by c_dog on 2005-03-23
Alien works just fine at installing the RPM. Well, almost fine. First you have to uninstall acroread 5, then:
 
alien -i AdobeReader_enu-7.0.0-1.i386.rpm

When you're done you need to create a symlink from the /usr/local/Adobe/Acrobat7.0/bin/acroread file to /usr/bin/acroread for the menu link to work

If you don't have open LAP installed to may get a error about trying to load the PPKLite.api. Just rename the /usr/local/Adobe/Acrobat7.0/Reader/intellinux/plug_ins/PPKLite.api to some .tmp name. This plugin is not critical.

---

### Post by #Vizc@ch@ on 2005-04-03
I had the following output after I typed "sudo apt-get install acroread":

```
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias... Hecho
No se pudieron instalar algunos paquetes. Esto puede significar que
usted pidió una situación imposible o, si está usando la distribución
inestable, que algunos paquetes necesarios no han sido creados o han
sido movidos fuera de Incoming.

Como sólo solicito una única operación, es extremadamente posible que el
paquete simplemente no sea instalable y debería de rellenar un informe de
error contra ese paquete.
La siguiente información puede ayudar a resolver la situación:

Los siguientes paquetes tienen dependencias incumplidas:
  acroread: Depende: libglib2.0-0 (>= 2.6.0) pero 2.4.7-0ubuntu2 va a ser instalado
            Depende: libgtk2.0-0 (>= 2.6.0) pero 2.4.10-1ubuntu1 va a ser instalado
            Depende: libpango1.0-0 (>= 1.8.1) pero 1.6.0b-0ubuntu1 va a ser instalado
E: Paquetes rotos

```

It's in Spanish but it says that the following packages have unresolved dependancies:
 libglib2.0-0 (>= 2.6.0)
 libgtk2.0-0 (>= 2.6.0)
 libpango1.0-0 (>= 1.8.1)

I followed the instructions on the Ubuntu 4.10 Unofficial Starter Guide and this is what I got.
How can I solve the problem?
Thanks for your help

---

### Post by maqi on 2005-04-04
Upgrade those libraries: you seem to have the 2.4versions installed. Just add all the hoary repositories to your list and then search for the relevant packages. If you're using hoary 5.04 you should have the 2.6 versions installed automatically - try: apt-get install --dist-upgrade.

The other thing is - you could fownload the sources in the tar.gz archive at the adobe ftp link above and use the INSTALL script. This is what I did and it works beautifully.

---

### Post by #Vizc@ch@ on 2005-04-04
Yeah, that worked. Thanks  :)

---

### Post by Psquared on 2005-05-01
[QUOTE=c_dog]Alien works just fine at installing the RPM. Well, almost fine. First you have to uninstall acroread 5, then:
 
alien -i AdobeReader_enu-7.0.0-1.i386.rpm

When you're done you need to create a symlink from the /usr/local/Adobe/Acrobat7.0/bin/acroread file to /usr/bin/acroread for the menu link to work

If you don't have open LAP installed to may get a error about trying to load the PPKLite.api. Just rename the /usr/local/Adobe/Acrobat7.0/Reader/intellinux/plug_ins/PPKLite.api to some .tmp name. This plugin is not critical.[/QUOTE]

Is the correct command:

sudo rename /usr/local/Adobe/Acrobat7.0/intellinux/plug_ins/PPKLite.api /usr/local/Adobe/Acrobat7.0/intellinux/plug_ins/ppklite.tmp ???

Where can I get Open Lap for Hoary? (I had it in Warty)

---

