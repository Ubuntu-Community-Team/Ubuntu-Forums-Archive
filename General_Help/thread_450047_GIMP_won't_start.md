---
title: "GIMP won't start"
date: 2007-05-20
forum: General Help
---

### Post by stealth17 on 2007-05-20
I'm running Ubuntu 7.04 AMD64 and I removed GIMP to try installing GIMPshop. Well I couldn't get GIMPshop installed, no biggy, and I actually decided I just want GIMP back anyways. So I reinstalled GIMP and now I can't get it to startup.

I tried starting via command line:

```
$ gimp --verbose
gimp: error while loading shared libraries: libart_lgpl_2.so.2: cannot open shared object file: No such file or directory
```I ran ldd to find the dependency and the libart_lgpl_2.so.2 sure does exist where it is looking for it and it is set to 0777 root:root. I tried running gimp with sudo, no luck.

I have reinstalled gimp and any dependency I could think of without any luck. I removed gimp and reinstalled using aptitude, no luck.

I'm running out of ideas, please help :(

EDIT: Also, I just restarted and no luck still...

---

### Post by mbradlcu on 2007-05-21
maybe try reinstalling libart-2.0-2? here's some info from my system (amd64, 7.04) that gimp is working on:

root@matt-x64:~# ls -al /usr/lib/libart_lgpl_2.so.2
lrwxrwxrwx 1 root root 23 Jan 21 00:40 /usr/lib/libart_lgpl_2.so.2 -> libart_lgpl_2.so.2.3.17
root@matt-x64:~# ls -al /usr/lib/libart_lgpl_2.so.2.3.17 
-rw-r--r-- 1 root root 93208 Jan 27  2005 /usr/lib/libart_lgpl_2.so.2.3.17

daturan@matt-x64:~$ gimp -v
GIMP version 2.2.13

---

### Post by stealth17 on 2007-05-21
> **mbradlcu said:**
> maybe try reinstalling libart-2.0-2? here's some info from my system (amd64, 7.04) that gimp is working on:

root@matt-x64:~# ls -al /usr/lib/libart_lgpl_2.so.2
lrwxrwxrwx 1 root root 23 Jan 21 00:40 /usr/lib/libart_lgpl_2.so.2 -> libart_lgpl_2.so.2.3.17
root@matt-x64:~# ls -al /usr/lib/libart_lgpl_2.so.2.3.17 
-rw-r--r-- 1 root root 93208 Jan 27  2005 /usr/lib/libart_lgpl_2.so.2.3.17

daturan@matt-x64:~$ gimp -v
GIMP version 2.2.13

Everything looks the same except I still get the error.

I was going to reinstall libart-2.0-2 but Synaptic told me it was going to uninstall a whole mess of other apps if I removed it. Can I run 

```
$ sudo apt-get remove libart-2.0-2 && sudo apt-get install libart-2.0-2
```via the command line without it removing all those other packages?

hmmm just tried and looks like I can't even through command line:

```
The following packages will be REMOVED:
  agave alacarte ark bluefish compiz compiz-gnome contact-lookup-applet
  deskbar-applet desktop-effects dvd95 eog etherape evince evolution-webcal
  f-spot file-roller firefox-gnome-support firestarter gcalctool gconf-editor
  gdm gedit gimp gimp-print gimp-svg gnome-about gnome-app-install
  gnome-applets gnome-btdownload gnome-control-center gnome-cups-manager
  gnome-games gnome-keyring-manager gnome-media gnome-netstatus-applet
  gnome-panel gnome-pilot gnome-pilot-conduits gnome-power-manager
  gnome-screensaver gnome-session gnome-spell gnome-system-tools
  gnome-terminal gnome-user-guide gnome-utils gnome-volume-manager gthumb
  gtkhtml3.14 gucharmap hal-device-manager hwdb-client-gnome k3b k9copy kchart
  kdebase-bin kdelibs4c2a kfilereplace klinkstatus koffice-libs kommander
  kpovmodeler kruler libart-2.0-2 libart-2.0-dev libbonoboui2-0 libcvsservice0
  libeel2-2 libgail-common libgail-gnome-module libgail18 libgdl-1-0
  libgdl-1-common libgnome-desktop-2 libgnome-window-settings1
  libgnome2-canvas-perl libgnome2-perl libgnome2.0-cil libgnomecanvas2-0
  libgnomecupsui1.0-1c2a libgnomeprint2.2-0 libgnomeprintui2.2-0 libgnomeui-0
  libgtkhtml2-0 libgtkhtml3.14-19 libgtksourceview1.0-0 libgucharmap6 libk3b2
  libk3b2-mp3 liblpint-bonobo0 libpanel-applet2-0 libslab0 nautilus
  nautilus-cd-burner network-manager-gnome python-gnome2 python-gnome2-desktop
  python-gnome2-extras python-gnomecanvas python-gtkhtml2 quanta rhythmbox
  serpentine sound-juicer tomboy totem-mozilla totem-xine tsclient
  ubuntu-desktop ubuntu-docs update-notifier vino yelp zenity
0 upgraded, 0 newly installed, 114 to remove and 0 not upgraded.
```

---

### Post by mbradlcu on 2007-05-21
ahhh! wow that's a lotOdependencies.. what about reinstalling but not removing? or you can wget it from me, [http://qndfix.no-ip.info/~satch/libart_lgpl_2.so.2.3.17](http://qndfix.no-ip.info/~satch/libart_lgpl_2.so.2.3.17)

---

### Post by stealth17 on 2007-05-22
> **mbradlcu said:**
> ahhh! wow that's a lotOdependencies.. what about reinstalling but not removing? or you can wget it from me, [http://qndfix.no-ip.info/~satch/libart_lgpl_2.so.2.3.17]("http://qndfix.no-ip.info/%7Esatch/libart_lgpl_2.so.2.3.17")

What type of file is that? How can I reinstall without removing first?

---

### Post by bobplano on 2007-05-22
sudo apt-get reinstall libart-2.0-2
try that

---

### Post by stealth17 on 2007-05-22
> **bobplano said:**
> sudo apt-get reinstall libart-2.0-2
try that

E: Invalid operation reinstall

---

### Post by stealth17 on 2007-05-22
> **mbradlcu said:**
> ahhh! wow that's a lotOdependencies.. what about reinstalling but not removing? or you can wget it from me, [http://qndfix.no-ip.info/~satch/libart_lgpl_2.so.2.3.17]("http://qndfix.no-ip.info/%7Esatch/libart_lgpl_2.so.2.3.17")

I replaced the file in /usr/lib with the downloaded one and it didn't help.

> **bobplano said:**
> sudo apt-get reinstall libart-2.0-2
try that

I ran sudo apt-get install -reinstall libart-2.0-2 and it didn't help.

I tried sudo apt-get remove --purge gimp and then deleted all the gimp folders and files it adds. I downloaded the gimp from the Ubuntu packages site and installed it and came up with the same error.

I downloaded the Gimp source and tried compiling it but I and stuck on the error

```
checking for GTK+ - version >= 2.4.4... no
*** Could not run GTK+ test program, checking why...
*** The test program failed to compile or link. See the file config.log for the
*** exact error that occured. This usually means GTK+ is incorrectly installed.
configure: error: Test for GTK+ failed. See the file 'INSTALL' for help.
```So I reinstalled the libgtk package and no luck. Then I figured maybe it needs the 32bit version, so I downloaded the 32bit version from the ubuntu packages site and installed using the --force-architecture trick. Same thing.

I really really really need gimp and I am out of ideas :(

Maybe a useful piece of information, I downloaded the libart_gpl source and compiled and installed it. Everything went smooth on the install, and when I tried launching gimp it gave a different error:

```
wrong ELF class: ELFCLASS64
```

Would this mean that it has something to do with the dependency and not gimp itself? If so, what do I do to fix?

---

### Post by mbradlcu on 2007-05-23
the ELF problem I've seen with games running on my 64bit system, I think it may have something to do with 32/64 libs.. anyway I'm pretty stumped too, you've done just about everything short of re-installing,, I think the error you're getting when trying to build gimp maybe because you need the gtk-dev packages installed.
good luck and sorry I can't be more help.

---

### Post by stealth17 on 2007-05-25
> **mbradlcu said:**
> the ELF problem I've seen with games running on my 64bit system, I think it may have something to do with 32/64 libs.. anyway I'm pretty stumped too, you've done just about everything short of re-installing,, I think the error you're getting when trying to build gimp maybe because you need the gtk-dev packages installed.
good luck and sorry I can't be more help.

I can't get the stupid dev packages installed because there are a TON of dependences for it  and none for AMD64.

Come on guys, I design websites, I REALLY REALLY need Gimp asap :(

---

### Post by SexualChocolate on 2007-06-03
stealth17: Did you ever get this working? I tried to install gimpshop and I'm also getting the following error (on x64 feisty):

```

gimp: error while loading shared libraries: libart_lgpl_2.so.2: cannot open shared object file: No such file or directory

```

So I searched for libart_lgpl_2.so.2 and libart_lgpl.so.2.3.17 and got:

```

jason@laptop:~$ sudo updatedb; locate libart_lgpl_2.so.2 ; locate libart_lgpl_2.so.2.3.17
/lib/libart_lgpl_2.so.2
/usr/lib/libart_lgpl_2.so.2.3.17
/usr/lib/gimp/2.0/modules/libart_lgpl_2.so.2
/usr/lib/vmware/lib/libart_lgpl_2.so.2
/usr/lib/vmware/lib/libart_lgpl_2.so.2/libart_lgpl_2.so.2
/usr/lib/gtk-2.0/2.10.0/loaders/libart_lgpl_2.so.2
/usr/lib/libart_lgpl_2.so.2
/usr/local/lib/gimp/2.0/modules/libart_lgpl_2.so.2
/usr/X11R6/lib/libart_lgpl_2.so.2
/home/jason/Desktop/downloads/vmware-distrib/lib/lib/libart_lgpl_2.so.2
/home/jason/Desktop/downloads/vmware-distrib/lib/lib/libart_lgpl_2.so.2/libart_lgpl_2.so.2
/usr/lib/libart_lgpl_2.so.2.3.17

```

Any ideas?

---

### Post by stealth17 on 2007-06-03
> **SexualChocolate said:**
> stealth17: Did you ever get this working? I tried to install gimpshop and I'm also getting the following error (on x64 feisty):

```

gimp: error while loading shared libraries: libart_lgpl_2.so.2: cannot open shared object file: No such file or directory

```So I searched for libart_lgpl_2.so.2 and libart_lgpl.so.2.3.17 and got:

```

jason@laptop:~$ sudo updatedb; locate libart_lgpl_2.so.2 ; locate libart_lgpl_2.so.2.3.17
/lib/libart_lgpl_2.so.2
/usr/lib/libart_lgpl_2.so.2.3.17
/usr/lib/gimp/2.0/modules/libart_lgpl_2.so.2
/usr/lib/vmware/lib/libart_lgpl_2.so.2
/usr/lib/vmware/lib/libart_lgpl_2.so.2/libart_lgpl_2.so.2
/usr/lib/gtk-2.0/2.10.0/loaders/libart_lgpl_2.so.2
/usr/lib/libart_lgpl_2.so.2
/usr/local/lib/gimp/2.0/modules/libart_lgpl_2.so.2
/usr/X11R6/lib/libart_lgpl_2.so.2
/home/jason/Desktop/downloads/vmware-distrib/lib/lib/libart_lgpl_2.so.2
/home/jason/Desktop/downloads/vmware-distrib/lib/lib/libart_lgpl_2.so.2/libart_lgpl_2.so.2
/usr/lib/libart_lgpl_2.so.2.3.17

```Any ideas?

Nope, never did get it to work. I got jacked by the kernel update the other day too and couldn't boot anymore even with the old kernel. I ended up saying screw it and reinstalling with the 32bit version :(

---

