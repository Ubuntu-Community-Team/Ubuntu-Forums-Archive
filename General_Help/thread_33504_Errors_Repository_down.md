---
title: "Errors? Repository down?"
date: 2005-05-11
forum: General Help
---

### Post by ntrsfrml on 2005-05-11
I have tried installing several apps from with this: sudo apt-get install <package name>

but always get these errors..:(

[[IMG]http://img7.echo.cx/img7/3709/firestartererrors2im.th.jpg[/IMG]](http://img7.echo.cx/my.php?image=firestartererrors2im.jpg)

[[IMG]http://img7.echo.cx/img7/8065/knemoerrors4go.th.jpg[/IMG]](http://img7.echo.cx/my.php?image=knemoerrors4go.jpg)

Also tried running apt-get update but get this :( :

[[IMG]http://img142.echo.cx/img142/7363/aptgetupdate9ki.th.jpg[/IMG]](http://img142.echo.cx/my.php?image=aptgetupdate9ki.jpg)

---

### Post by DukeNuke2 on 2005-05-11
same here.... maybe the ftp server is down.... :-|

---

### Post by Sniffer on 2005-05-11
The problem you have is with Nerim Repos.

You need to add the GPG Key for use Nerim Packages, you can find this instructions on Ubuntu Unofficial Guide. Go on the terminal and do this:

gpg --keyserver wwwkeys.eu.pgp.net --recv-keys 1F41B907
gpg --armor --export 1F41B907 | sudo apt-key add -
sudo apt-get update


Or if you don't need Nerim Rep, just do sudo gedit /ect/apt/sources.list

and put a # on every ftp.nerim.net or just remove the lines.

---

### Post by DukeNuke2 on 2005-05-11
[QUOTE=Sniffer]The problem you have is with Nerim Repos.

You need to add the GPG Key for use Nerim Packages, you can find this instructions on Ubuntu Unofficial Guide. Go on the terminal and do this:

gpg --keyserver wwwkeys.eu.pgp.net --recv-keys 1F41B907
gpg --armor --export 1F41B907 | sudo apt-key add -
sudo apt-get update


Or if you don't need Nerim Rep, just do sudo gedit /ect/apt/sources.list

and put a # on every ftp.nerim.net or just remove the lines.[/QUOTE]
 the nerim repo works yesterday and i've the gpg key installed..... so i think its a problem on the other side of the line?!?!

---

### Post by Sniffer on 2005-05-11
In that case you are right :grin:

---

