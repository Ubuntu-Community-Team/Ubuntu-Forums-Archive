---
title: "Apt-get does not work"
date: 2008-01-30
forum: General Help
---

### Post by Lean 946 on 2008-01-30
Here's my story:
I have a Pentium 3 192MB and i use linux because its more lightweight. I've installed Kubuntu (the xubuntu installer doesn't work), then Xfce and then GNOME. I actually use GNOME. My problem: i cant install (or update) any package. Not even in the terminal. Here's the output of the terminal in the Updates Manager (traduced from spanish):
```
(reading database... dpkg: error in processing /var/cache/apt/archives/tzdata_2007k-0ubuntu0.7.04_all.deb (--unpack) :
fail in buffer_read(fd): the list of files of the package 'linux-restricted-modules-generic': Input/output error
there were errors on processing:
/var/cache/apt/archives/tzdata_2007k-0ubuntu0.7.04_all.deb
Process Stopped because there are too much errors
E: Sub-process /usr/bin/dpkg returned an error code (1)
There was not been able to install a package. Trying to recover:
```
And thats it. Remember its a traduction, it may have errors or not be exactly as yours.

---

### Post by taurus on 2008-01-30
What happens if you run these commands from a terminal?

```
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by Lean 946 on 2008-01-30
No, it doesn't work. The error is the same, but this time with the package
"/var/cache/apt/archives/mysql-common_5.0.38-0ubuntu1.2_all.deb"
I know its MySQL, and its a package that i had to de-check on the Update Manager because i dont need it.
Thanks for Your support

---

### Post by Rocket2DMn on 2008-01-30
Run
```
sudo apt-get clean
```
That will clean out your cache/archives.  Then you can run your original command again.  Post back if you still have problems!

---

### Post by Lean 946 on 2008-01-30
Oh! No! download AGAIN 166Mb with a 64k connection!?!?
is there another way? Like, reinstaling dpkg, apt or recompiling the kernel? in the message sais that its an issue with a module of the kernel 'linux-restricted-module' or something like that. If not, I'll try to install 1 package and see, but before i had to apgrade packages, i'd tryied to install something and didnt work either, i think its not packages issue, it comes the way from the kernel, or the binaries system, or i have to compile for the rest of my ubuntu life :(

---

### Post by Rocket2DMn on 2008-01-30
These files are just archives of the installers, if you've already installed them on your system, you don't need the archives anymore, apt-get just holds on to them by default.
If that worries you, you can try getting rid of just the packages that are giving you problems, say like moving them out of that directory
```
sudo mv /var/cache/apt/archives/tzdata_2007k-0ubuntu0.7.04_all.deb ~/Desktop/tzdata_2007k-0ubuntu0.7.04_all.deb
```
Repeat for each package that it complains about, this just puts them on your desktop for now.  You can delete them FROM your desktop with
```
cd ~/Desktop
sudo rm *packagename.deb*
```
or move them back when you're finished (though you will continue to get errors I imagine)

I don't see how reinstalling dpkg would help, it hasn't really shown that dpkg is messed up in any way. Apt and the kernel seem ok too...

---

### Post by Lean 946 on 2008-01-30
Ok, i've done as you said, tryied installing a small package, but i have this error output (again, tranlated from spanish):

```
root@lean:/home/lean# apt-get install vim
Reading Packages list... Done
Creating Dependencies Tree       
Reading State Imformation... Done
Suggested Packages:
  ctags vim-doc vim-scripts
These NEW Packages will be installed:
  vim
0 upgaded, 1 will be installed, 0 to erase y 116 not upgraded.
I need to download 738kB of files.
It will be used 1454kB of Disk space after de-packaging.
Down:1 http://ar.archive.ubuntu.com feisty-updates/main vim 1:7.0-164+1ubuntu7.2 [738kB]
Downloaded 738kB in 1m31s (8027B/s)                                           
Selecting Package vim previously not selected.
(Reading data Base ... dpkg: error in processing /var/cache/apt/archives/vim_1%3a7.0-164+1ubuntu7.2_i386.deb (--unpack):
failure in buffer_read(fd): the list of files of the package `linux-restricted-modules-generic': Input/output error
There were errors processing:
 /var/cache/apt/archives/vim_1%3a7.0-164+1ubuntu7.2_i386.deb
Process stopped for being too much errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@lean:/home/lean# 
```

---

### Post by Rocket2DMn on 2008-01-30
OK, well linux-restricted-modules-generic is giving us problems, so let's try to reinstall that package.  If you have your install cd, you can put that in the drive and go to System->Administration->Software Sources and enable the cd as a repository (so you don't have to download the package, it's like 20 MB or so).
```
sudo apt-get install --reinstall linux-restricted-modules-generic
```
Also, you don't need to bother translating anymore, I understand enough Spanish to see what's happening.

If that doesn't work, what happens when you try installing through Synaptic?

---

### Post by Lean 946 on 2008-01-30
Do Kubuntu live cd's work? Does it work if i mount the iso image of the cd and not insert the cd? i cant find it... i have Gmount-iso

---

### Post by Rocket2DMn on 2008-01-30
A Kubuntu LiveCD would probably work.  I'm not sure if this would work, but if you mount the cd image at /media/cdrom0 (or wherever your cd mount point is), it might just work.  Otherwise, just burn the ISO to a cd and try, or just try downloading it (thought it seems that would take awhile).

---

### Post by Lean 946 on 2008-01-30
You said I dont needed to translate and this is what the terminal shows up, but if you dont understand something, just say it:
```
root@lean:/home/lean# sudo apt-get install --reinstall linux-restricted-modules-generic
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo información de estado... Hecho
linux-restricted-modules-generic fijar a instalado manual.
0 actualizados, 0 se instalarán, 1 reinstalados, 0 para eliminar y 116 no actualizados.
Necesito descargar 24,5kB de archivos.
Se utilizarán 0B de espacio de disco adicional después de desempaquetar.
¿Desea continuar [S/n]? s
Des:1 http://ar.archive.ubuntu.com feisty-updates/restricted linux-restricted-modules-generic 2.6.20.16.28.1 [24,5kB]
Descargados 24,5kB en 10s (2430B/s)                      
(Leyendo la base de datos ... dpkg: error al procesar /var/cache/apt/archives/linux-restricted-modules-generic_2.6.20.16.28.1_i386.deb (--unpack):
 fallo en buffer_read(fd): el fichero de lista de ficheros del paquete `linux-restricted-modules-generic': Input/output error
Se encontraron errores al procesar:
 /var/cache/apt/archives/linux-restricted-modules-generic_2.6.20.16.28.1_i386.deb
Proceso detenido por haber demasiados errores.
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@lean:/home/lean# 

```
as you can note: its the same error, and the package lenght was 24,5 kb, not 20mb :/ can be and incorrect package

---

### Post by Rocket2DMn on 2008-01-30
Can you please post the contents of your sources.list file?
```
cat /etc/apt/sources.list
```
I would tell you to run upgrade at this time, but that would probably take you forever and still result in the same problem.
Also, I'm going to ask you to burn that Kubuntu LiveCD and boot it up.  Once there, run fsck on your root filesystem.  Although I hope it's not the case, this problem has sometimes been a result of messed up hard drives.

---

### Post by Lean 946 on 2008-01-30
Ok, i'll try it
PD: Cani use an Xubuntu LiveCD for the pc to run smoothly on the live cd mode?
The Sources.list file:
root@lean:/home/lean# cat /etc/apt/sources.list

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Google software repository
deb [http://dl.google.com/linux/deb](http://dl.google.com/linux/deb) stable non-free

deb [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) feisty restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) feisty-updates main restricted universe
deb-src [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) feisty-updates main restricted universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security restricted main multiverse universe #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates restricted main multiverse universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates restricted main multiverse universe #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable non-free
deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable non-free
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main
# Paquetes de Ubuntu (GPG key: 437D05B5)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-updates main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-proposed main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-proposed main restricted

# Paquetes de la comunidad de Ubuntu (GPG key: 437D05B5)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty universe multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-updates universe multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-security universe multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-proposed universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-updates universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-security universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-proposed universe multiverse

# Paquetes "backports" de Ubuntu (GPG key: 437D05B5)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-backports main restricted universe multiverse

# Repositorios comeriales de Canonical (Alojados en los servidores de Canonical, no los de Ubuntu)
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main

# Paquete de Seveas packages (GPG key: 1135D466)
deb [http://mirror.ubuntulinux.nl](http://mirror.ubuntulinux.nl) feisty-seveas all
deb-src [http://mirror.ubuntulinux.nl](http://mirror.ubuntulinux.nl) feisty-seveas all

# Paquetes de wine
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) feisty main
deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) feisty main

# Navegador Opera (GPG key: 6A423791)
deb [http://deb.opera.com/opera](http://deb.opera.com/opera) etch non-free

# Algunos paquetes más
deb [http://archive.czessi.net/ubuntu](http://archive.czessi.net/ubuntu) feisty main restricted universe multiverse preview
deb-src [http://archive.czessi.net/ubuntu](http://archive.czessi.net/ubuntu) feisty main restricted universe multiverse preview

# Paquetes No-oficales para Kubuntu Feisty Fawn de Achim
deb [http://www.mpe.mpg.de/~ach/kubuntu/feisty](http://www.mpe.mpg.de/~ach/kubuntu/feisty) ./
deb-src [http://www.mpe.mpg.de/~ach/kubuntu/feisty](http://www.mpe.mpg.de/~ach/kubuntu/feisty) ./


# uniklu: Paquetes nuevos
# uniklu-desktop: Paquetes de escritorio
# uniklu-intern: Paquetes modificados o paquetes no libres
# uniklu-nfsv4: Kernel nfsv4 y algunos paquetes más
# uniklu-vserver: Kernel vserver
# uniklu-testing: Paquetes que no estan listos para uso general!!!!
# Los repositorios comentados aun no estan para Feisty, asi que solo los comento, para ver si pronto ya estan.
deb [http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/](http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/) feisty uniklu
deb [http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/](http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/) feisty uniklu-intern
deb-src [http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/](http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/) feisty uniklu
deb-src [http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/](http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/) feisty uniklu-intern
##############Un poco inseguro######deb [http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/](http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/) feisty uniklu-testing
##############Un poco inseguro######deb-src [http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/](http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/) feisty uniklu-testing
##############Aun no estan para Feisty######deb-src [http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/](http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/) feisty uniklu-nfsv4
##############Aun no estan para Feisty######deb-src [http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/](http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/) feisty uniklu-vserver
##############Aun no estan para Feisty######deb-src [http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/](http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/) feisty uniklu-desktop
##############Aun no estan para Feisty######deb-src [http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/](http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/) feisty uniklu-desktop
##############Aun no estan para Feisty######deb [http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/](http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/) feisty uniklu-nfsv4
##############Aun no estan para Feisty######deb [http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/](http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/) feisty uniklu-vserver
##############Aun no estan para Feisty######deb [http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/](http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/) feisty uniklu-desktop

## Paquetes de SimplyMepis (distro basada en K-ubuntu)
deb [http://apt.mepis.org/6.0/](http://apt.mepis.org/6.0/) mepis main

# Ekiga y Debian pkg-voip
deb [http://pkg-voip.buildserver.net/ubuntu](http://pkg-voip.buildserver.net/ubuntu) feisty main

# repositorio de superml (mythtv y otros no-libres) (GPG key: 80DF6D58)
deb [http://home.eng.iastate.edu/~superm1](http://home.eng.iastate.edu/~superm1) feisty all
deb-src [http://home.eng.iastate.edu/~superm1](http://home.eng.iastate.edu/~superm1) feisty all

# Paquetes oficiales de Beryl para Ubuntu (GPG key: 1609B551)
deb [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty main
deb-src [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty main

# Repositorio de Screenlets para Ubuntu (si no sabes que son los screenlets, en youtube.com hay unos videos)(GPG key: 619A3D4E)
deb [http://hendrik.kaju.pri.ee/ubuntu](http://hendrik.kaju.pri.ee/ubuntu) feisty screenlets all
deb-src [http://hendrik.kaju.pri.ee/ubuntu](http://hendrik.kaju.pri.ee/ubuntu) feisty screenlets all

# Paquetes de Easycam
deb [http://blognux.free.fr/debian](http://blognux.free.fr/debian) unstable main

# Audacious
deb [http://vdlinux.sourceforge.jp/](http://vdlinux.sourceforge.jp/) experimental all
deb-src [http://vdlinux.sourceforge.jp/](http://vdlinux.sourceforge.jp/) experimental all

# Repositorio para ubuntu de Geole
deb [http://ubuntu.geole.info/](http://ubuntu.geole.info/) feisty universe multiverse

# Paquetes para Ubuntu Linux2Go (GPG key: E8BDA4E3)
deb [http://www.linux2go.dk/ubuntu](http://www.linux2go.dk/ubuntu) feisty main
deb-src [http://www.linux2go.dk/ubuntu](http://www.linux2go.dk/ubuntu) feisty main

# Paquetes de Tvfreeplayer (GPG key: 3C6489CB)
deb [http://www.tvfreeplayer.com/linux/falcon](http://www.tvfreeplayer.com/linux/falcon) feisty all mods vlc
deb-src [http://www.tvfreeplayer.com/linux/falcon](http://www.tvfreeplayer.com/linux/falcon) feisty all mods vlc

# gnomemeeting - ekiga (GPG key: 52ABFCB1)
deb [http://snapshots.ekiga.net/ubuntu/](http://snapshots.ekiga.net/ubuntu/) feisty main
deb-src [http://snapshots.ekiga.net/ubuntu/](http://snapshots.ekiga.net/ubuntu/) feisty main
deb [http://snapshots.voxgratia.org/ubuntu/](http://snapshots.voxgratia.org/ubuntu/) feisty main
deb-src [http://snapshots.voxgratia.org/ubuntu/](http://snapshots.voxgratia.org/ubuntu/) feisty main

# Repositorio de seb128 (gaim - rhythmbox)
deb [http://people.ubuntu.com/~seb128/deb](http://people.ubuntu.com/~seb128/deb) ./
deb-src [http://people.ubuntu.com/~seb128/deb](http://people.ubuntu.com/~seb128/deb) ./

# Paquetes Mjpegtools y Cinelerra (Elige tu arquitectura)
deb [http://www.kiberpipa.org/~gandalf/ubuntu/feisty/cinelerra/pentium4/](http://www.kiberpipa.org/~gandalf/ubuntu/feisty/cinelerra/pentium4/) ./
# deb-src [http://www.kiberpipa.org/~gandalf/ubuntu/dapper/cinelerra/pentium4/](http://www.kiberpipa.org/~gandalf/ubuntu/dapper/cinelerra/pentium4/) ./
#############deb [http://www.kiberpipa.org/~gandalf/ubuntu/dapper/mjpegtools](http://www.kiberpipa.org/~gandalf/ubuntu/dapper/mjpegtools) ./
#############deb [http://www.kiberpipa.org/~gandalf/ubuntu/feisty/cinelerra/i686/](http://www.kiberpipa.org/~gandalf/ubuntu/feisty/cinelerra/i686/) ./
#############deb [http://www.kiberpipa.org/~gandalf/ubuntu/dapper/cinelerra/athlonxp/](http://www.kiberpipa.org/~gandalf/ubuntu/dapper/cinelerra/athlonxp/) ./
#############deb-src [http://www.kiberpipa.org/~gandalf/ubuntu/dapper/cinelerra/i686/](http://www.kiberpipa.org/~gandalf/ubuntu/dapper/cinelerra/i686/) ./
#############deb-src [http://www.kiberpipa.org/~gandalf/ubuntu/dapper/cinelerra/athlonxp/](http://www.kiberpipa.org/~gandalf/ubuntu/dapper/cinelerra/athlonxp/) ./

# Repositorio Cafuego para Feisty: Broadcom firmware, google-earth, beagle (GPG key: 969F3F57)…
deb [http://au.ubuntu.cafuego.net](http://au.ubuntu.cafuego.net) feisty-cafuego all
deb-src [http://au.ubuntu.cafuego.net](http://au.ubuntu.cafuego.net) feisty-cafuego all
deb [http://au.ubuntu.cafuego.net](http://au.ubuntu.cafuego.net) feisty-cafuego bcm43xx
deb-src [http://au.ubuntu.cafuego.net](http://au.ubuntu.cafuego.net) feisty-cafuego bcm43xx
deb [http://au.ubuntu.cafuego.net](http://au.ubuntu.cafuego.net) feisty-cafuego internode
deb-src [http://au.ubuntu.cafuego.net](http://au.ubuntu.cafuego.net) feisty-cafuego internode
deb [http://au.ubuntu.cafuego.net](http://au.ubuntu.cafuego.net) feisty-cafuego google
deb-src [http://au.ubuntu.cafuego.net](http://au.ubuntu.cafuego.net) feisty-cafuego google
deb [http://au.ubuntu.cafuego.net](http://au.ubuntu.cafuego.net) feisty-cafuego secondlife
deb-src [http://au.ubuntu.cafuego.net](http://au.ubuntu.cafuego.net) feisty-cafuego secondlife
#########Tienen un pequeño error, cuando se solucione, lo descomento ##########deb [http://au.ubuntu.cafuego.net](http://au.ubuntu.cafuego.net) feisty-cafuego media
#########Tienen un pequeño error, cuando se solucione, lo descomento ##########deb-src [http://au.ubuntu.cafuego.net](http://au.ubuntu.cafuego.net) feisty-cafuego media

# Paquetes Debuntu Ubuntu Feisty
deb [http://repository.debuntu.org/](http://repository.debuntu.org/) feisty multiverse
deb-src [http://repository.debuntu.org/](http://repository.debuntu.org/) feisty multiverse

# Repositorio Mogoth (Monkey’s Audio, xmms pugins, vlc plugins, gqview, audacity…) (GPG key: 7E2E4741)
deb [http://morgoth.free.fr/ubuntu](http://morgoth.free.fr/ubuntu) feisty-backports main
deb-src [http://morgoth.free.fr/ubuntu](http://morgoth.free.fr/ubuntu) feisty-backports main

# Latest Nvidia drivers in restricted modules packages
###### No uso Nvidia, por eso lo comento#####deb [http://amaranth.selfip.com/](http://amaranth.selfip.com/) feisty lrm
###### No uso Nvidia, por eso lo comento#####deb-src [http://amaranth.selfip.com/](http://amaranth.selfip.com/) feisty lrm

# Repositorio de Automatix (GPG key: E23C5FC3)
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main testing

# edevelop - e17 (Enlightenment DR 17)
deb [http://edevelop.org/pkg-e/ubuntu](http://edevelop.org/pkg-e/ubuntu) feisty e17
deb-src [http://edevelop.org/pkg-e/ubuntu](http://edevelop.org/pkg-e/ubuntu) feisty e17

# Musicbrainz
deb [http://ftp.musicbrainz.org/pub/musicbrainz/users/luks/ubuntu](http://ftp.musicbrainz.org/pub/musicbrainz/users/luks/ubuntu) feisty musicbrainz
deb-src [http://ftp.musicbrainz.org/pub/musicbrainz/users/luks/ubuntu](http://ftp.musicbrainz.org/pub/musicbrainz/users/luks/ubuntu) feisty musicbrainz

# Repositorio imbrandons (GPG key: 887D9FD2)
deb [http://www.imbrandon.com/packages](http://www.imbrandon.com/packages) feisty all beryl
deb-src [http://www.imbrandon.com/packages](http://www.imbrandon.com/packages) feisty all beryl

# Paquetes de Administrador del Sistema Ubuntu
deb [http://ubuntu.moshen.de](http://ubuntu.moshen.de) feisty multimedia misc eyecandy
deb-src [http://ubuntu.moshen.de](http://ubuntu.moshen.de) feisty multimedia misc eyecandy

# El repositorio del conocimiento (GPG key: DD385D79)
deb [http://debs.peadrop.com](http://debs.peadrop.com) feisty backports
deb-src [http://debs.peadrop.com](http://debs.peadrop.com) feisty backports

# Repositorio IVTV para Ubuntu (GPG key: 80DF6D58)
deb [http://dl.ivtvdriver.org/ubuntu](http://dl.ivtvdriver.org/ubuntu) feisty all
deb-src [http://dl.ivtvdriver.org/ubuntu](http://dl.ivtvdriver.org/ubuntu) feisty all

# Repositorio de Treviño para Feisty Fawn (GPG key: 81836EBF - DD800CD9)
# Para mas informacion: [http://3v1n0.tuxfamily.org](http://3v1n0.tuxfamily.org)
deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy suspend2
deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy suspend2

#Repositorio de Elisa Media Center
deb [http://elisa.fluendo.com/packages](http://elisa.fluendo.com/packages) feisty main

deb [http://hydr0g3n.free.fr/qbittorrent/feisty/](http://hydr0g3n.free.fr/qbittorrent/feisty/) ./
deb-src [http://hydr0g3n.free.fr/qbittorrent/feisty/](http://hydr0g3n.free.fr/qbittorrent/feisty/) ./
root@lean:/home/lean#

---

### Post by Rocket2DMn on 2008-01-30
Any LiveCD will work, you just need it because you can't check the filesystem when it's mounted.  Do this before the next steps.

Also, staying logged in as root is a very bad idea.
You have a very large sources.list file, hopefully nothing conflicts in it.  You can try disabling everything not from the official repositories, maybe just by copying the file to a backup and deleting everything else (it would be easier then commenting everything else out).
First:
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup
```
then: modify the sources.list file with
```
gksudo gedit /etc/apt/sources.list
```

---

### Post by Lean 946 on 2008-01-30
can i mount the swap on the live cd?

---

### Post by Rocket2DMn on 2008-01-30
I don't believe so since swap doesn't technically have a mount point.  Sorry.

---

### Post by Lean 946 on 2008-01-30
it's ok like this?
```
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://ar.archive.ubuntu.com/ubuntu/ feisty main restricted
deb-src http://ar.archive.ubuntu.com/ubuntu/ feisty restricted main multiverse universe

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ar.archive.ubuntu.com/ubuntu/ feisty-updates main restricted universe
deb-src http://ar.archive.ubuntu.com/ubuntu/ feisty-updates main restricted universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://ar.archive.ubuntu.com/ubuntu/ feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ar.archive.ubuntu.com/ubuntu/ feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://ar.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
# deb-src http://ar.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security restricted main multiverse universe
deb http://security.ubuntu.com/ubuntu feisty-security universe
deb http://security.ubuntu.com/ubuntu feisty-security multiverse
```

---

### Post by Lean 946 on 2008-01-30
> **Rocket2DMn said:**
> I don't believe so since swap doesn't technically have a mount point.  Sorry.
i have the swap as /dev/sda5

---

### Post by Rocket2DMn on 2008-01-30
That looks pretty good, try running
```
sudo apt-get update
sudo apt-get install *yourpackage*
```
Otherwise, boot up that LiveCD and run fsck on your root partition.

"i have the swap as /dev/sda5"  - That's a device, not a mount point on your file system.  A mount point would map /dev/sda5 to some directory like /media/swap , but swap doesn't work like that, if you look in /etc/fstab you will see it mounts to "none".

---

### Post by Lean 946 on 2008-01-30
Ok, the changes to my sources.list doesn't make any effect, now i'm on my live cd and I de-mounted my root (/) directoty
now I have to do:
```
sudo fsck /dev/sda1
```
right?

---

