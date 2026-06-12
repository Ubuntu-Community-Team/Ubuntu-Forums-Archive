---
title: "all KDE related programs will not run in gnome in edgy"
date: 2006-11-05
forum: General Help
---

### Post by cptjaben on 2006-11-05
When I try and run Amarok, kaffeine, or k3b in gnome I get various error messages.

when I try and run amarok I get:

Floating point exception (core dumped

when I try and run kaffeine I get:

ERROR: Communication problem with kaffeine, it probably crashed.

when I try and run k3b I get:

ERROR: Communication problem with k3b, it probably crashed.

Does anyone have an idea on how to fix this?
Thanks

---

### Post by taurus on 2006-11-05
I assume you install Edgy first with Gnome and then install those KDE apps with synaptic/apt-get/aptitude, right!!!  I don't have any problem running k3b because that is the only burning program that I use, no matter what window manager I an running...

---

### Post by cptjaben on 2006-11-05
I installed the programs with synaptic after in gnome with dapper and then upgraded to edgy, after I upgraded they all worked fine until just a few days ago.

---

### Post by taurus on 2006-11-05
Try to remove it and install it again and see what happens.  Open a terminal, Applications -> Accessories -> Terminal, and type

```

sudo aptitude update
sudo aptitude remove k3b
sudo aptitude install k3b
k3b

```

---

### Post by cptjaben on 2006-11-05
after removing and installing k3b, When I try to run it I get this message:

ERROR: Communication problem with k3b, it probably crashed.

---

### Post by taurus on 2006-11-05
Hmm...  What does your /etc/apt/sources.list look like anyway?

```
more /etc/apt/sources.list
```
Also, what does it say when you run this from a terminal?

```
ldd /usr/bin/k3b
-or-
ldd /bin/k3b
```

---

### Post by cptjaben on 2006-11-05
My /etc/apt/sources.list looks like this:

```
deb-src http://archive.ubuntu.com/ubuntu/ edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ edgy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ edgy universe multiverse main restricted
deb-src http://archive.ubuntu.com/ubuntu/ edgy universe multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu edgy-security main restricted
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted
deb http://security.ubuntu.com/ubuntu edgy-security universe multiverse
deb-src http://security.ubuntu.com/ubuntu edgy-security universe multiverse

## dapper-commercial by canonical
## currently has realplay (realplayer 10) and opera (opera 9)
# deb http://archive.canonical.com/ubuntu dapper-commercial main

## Bleeding edge (official) wine repository for Dapper
## only uncomment it if you need it
## deb http://wine.budgetdedicated.com/apt dapper main
## deb-src http://wine.budgetdedicated.com/apt dapper main

## skype (official)
## only uncomment it if you need it
## deb http://download.skype.com/linux/repos/debian/ stable non-free
# deb http://www.getautomatix.com/apt dapper main
# deb http://www.beerorkid.com/compiz/ dapper main
# deb http://xgl.compiz.info/ dapper main
# deb-src http://xgl.compiz.info/ dapper main

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ edgy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ edgy-updates main restricted

#compiz Quinn's
# deb http://www.beerorkid.com/compiz dapper main
# deb http://xgl.compiz.info/ dapper main
# deb-src http://xgl.compiz.info/ dapper main

# deb http://morgoth.free.fr/ubuntu dapper-backports main
# deb-src http://wine.budgetdedicated.com/apt dapper mainci

 # debian.scribus.net - Primary repository
# deb http://debian.scribus.net/debian dapper main restricted
# deb-src http://debian.scribus.net/debian dapper main restricted

# debian.tagancha.org - Backup repository    
# deb http://debian.tagancha.org/debian dapper main restricted
# deb-src http://debian.tagancha.org/debian dapper main restricted

 
```





When I run ldd /usr/bin/k3b I get:

```
        linux-gate.so.1 =>  (0xffffe000)
        libk3bdevice.so.2 => /usr/lib/libk3bdevice.so.2 (0xb7f38000)
        libk3b.so.2 => /usr/lib/libk3b.so.2 (0xb7d83000)
        libhal.so.1 => /usr/lib/libhal.so.1 (0xb7d7a000)
        libdbus-1.so.3 => /usr/lib/libdbus-1.so.3 (0xb7d4a000)
        libdbus-qt-1.so.1 => /usr/lib/libdbus-qt-1.so.1 (0xb7d3a000)
        libkparts.so.2 => /usr/lib/libkparts.so.2 (0xb7cf5000)
        libkio.so.4 => /usr/lib/libkio.so.4 (0xb79b7000)
        libkdeui.so.4 => /usr/lib/libkdeui.so.4 (0xb76de000)
        libkdesu.so.4 => /usr/lib/libkdesu.so.4 (0xb76c8000)
        libkwalletclient.so.1 => /usr/lib/libkwalletclient.so.1 (0xb76b7000)
        libkdecore.so.4 => /usr/lib/libkdecore.so.4 (0xb747c000)
        libDCOP.so.4 => /usr/lib/libDCOP.so.4 (0xb7449000)
        libresolv.so.2 => /lib/tls/i686/cmov/libresolv.so.2 (0xb7435000)
        libutil.so.1 => /lib/tls/i686/cmov/libutil.so.1 (0xb7431000)
        libart_lgpl_2.so.2 => /usr/lib/libart_lgpl_2.so.2 (0xb741c000)
        libidn.so.11 => /usr/lib/libidn.so.11 (0xb73ec000)
        libkdefx.so.4 => /usr/lib/libkdefx.so.4 (0xb73c1000)
        libqt-mt.so.3 => /usr/lib/libqt-mt.so.3 (0xb6be2000)
        libaudio.so.2 => /usr/lib/libaudio.so.2 (0xb6bcb000)
        libXt.so.6 => /usr/lib/libXt.so.6 (0xb6b7d000)
        libjpeg.so.62 => /usr/lib/libjpeg.so.62 (0xb6b5e000)
        libXi.so.6 => /usr/lib/libXi.so.6 (0xb6b56000)
        libXrandr.so.2 => /usr/lib/libXrandr.so.2 (0xb6b53000)
        libXcursor.so.1 => /usr/lib/libXcursor.so.1 (0xb6b4a000)
        libXinerama.so.1 => /usr/lib/libXinerama.so.1 (0xb6b46000)
        libXft.so.2 => /usr/lib/libXft.so.2 (0xb6b34000)
        libfreetype.so.6 => /usr/lib/libfreetype.so.6 (0xb6aca000)
        libfontconfig.so.1 => /usr/lib/libfontconfig.so.1 (0xb6a9b000)
        libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb6a97000)
        libpng12.so.0 => /usr/lib/libpng12.so.0 (0xb6a74000)
        libXext.so.6 => /usr/lib/libXext.so.6 (0xb6a66000)
        libX11.so.6 => /usr/lib/libX11.so.6 (0xb699d000)
        libSM.so.6 => /usr/lib/libSM.so.6 (0xb6994000)
        libICE.so.6 => /usr/lib/libICE.so.6 (0xb697c000)
        libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0xb6969000)
        libXrender.so.1 => /usr/lib/libXrender.so.1 (0xb6961000)
        libz.so.1 => /usr/lib/libz.so.1 (0xb694c000)
        libacl.so.1 => /lib/libacl.so.1 (0xb6946000)
        libattr.so.1 => /lib/libattr.so.1 (0xb6942000)
        libmusicbrainz.so.4 => /usr/lib/libmusicbrainz.so.4 (0xb6912000)
        libexpat.so.1 => /usr/lib/libexpat.so.1 (0xb68f4000)
        libstdc++.so.6 => /usr/lib/libstdc++.so.6 (0xb6815000)
        libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0xb67ee000)
        libgcc_s.so.1 => /lib/libgcc_s.so.1 (0xb67e3000)
        libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb66af000)
        libnsl.so.1 => /lib/tls/i686/cmov/libnsl.so.1 (0xb6699000)
        libXfixes.so.3 => /usr/lib/libXfixes.so.3 (0xb6693000)
        /lib/ld-linux.so.2 (0xb7f73000)
        libXau.so.6 => /usr/lib/libXau.so.6 (0xb6690000)
        libXdmcp.so.6 => /usr/lib/libXdmcp.so.6 (0xb668b000)

```

When i run ldd /bin/k3b i get:

ldd: /bin/k3b: No such file or directory

Any ideas?

---

### Post by taurus on 2006-11-05
And what does it say when you run

```
file /usr/bin/k3b
```

---

### Post by cptjaben on 2006-11-05
When I run file /usr/bin/k3b, It says:

/usr/bin/k3b: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), for GNU/Linux 2.6.0, dynamically linked (uses shared libs), for GNU/Linux 2.6.0, stripped

---

### Post by taurus on 2006-11-05
And

```
uname -a
```

---

### Post by cptjaben on 2006-11-05
When I type uname -a, I get this:

Linux john 2.6.17-10-386 #2 Fri Oct 13 18:41:40 UTC 2006 i686 GNU/Linux

---

### Post by cptjaben on 2006-11-05
Not sure if this matters, but the problems starting happening after I had to reinstall my graphics drivers by reinstalling: xorg-driver-fglrx in synaptic. In addition I have to change my xorg.conf to say 'fglrx' instead of ati' and I also restarted X by pressing CTRL+ALT+Backspace. Hope this helps, The list of programs i cannot run include, open office, scribus, amarok, kaffeine, Kcalc, totem, k3b, plus many other programs that I haven't attempted to run. Thanks

---

### Post by maniacmusician on 2006-11-06
To find out if this is indeed the problem (and it seems likely), just change your xorg.conf back to say "ati".

---

### Post by cptjaben on 2006-11-06
i restarted my computer today and all of my programs seem to work again, don't know what caused them to but i'm not complaining thanks for the help everyone.

---

### Post by jdong on 2006-11-06
Most likely some of your DCOP or other sockets located in the root of your home directory and /tmp were broken for some reason, and a reboot cleaned them out.

---

