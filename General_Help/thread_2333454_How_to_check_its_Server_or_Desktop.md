---
title: "How to check its Server or Desktop"
date: 2016-08-10
forum: General Help
---

### Post by tech291083 on 2016-08-10
Friends,

I just installed Ubuntu 16.04 LTS Server 32 bit on my PC. Then I did the following as root,

```

sudo apt-get update 
sudo apt-get upgrade 
sudo apt-get dist-upgrade

```

Rebooted the PC and then installed the GUI by,

```

sudo apt-get install ubuntu-desktop

```

Now, I wanted to confirm that the original Ubuntu was Server, so I did the following,

```

root@ubuntupc:~# uname -a
Linux ubuntupc 4.4.0-34-generic #53-Ubuntu SMP Wed Jul 27 16:06:28 UTC 2016 i686 i686 i686 GNU/Linux
root@ubuntupc:~# 

```

And the above output has the word "generic" meaning Desktop version, am I right? I thought there would be "server" instead of "generic" in the output, since the original Ubuntu version was Server with no GUI and it was me who installed the GUI manually. 

So, how can one actually find out that the original Ubuntu installed was Server and not Desktop after he installs the GUI manually? I have always relied on "uname -a" command to figure out the version.

Thanks.

---

### Post by tech291083 on 2016-08-10
I am also not able to figure out as to what DE I am running, even though I have installed the GUI by


```

sudo apt-get install ubuntu-desktop

```


```

root@ubuntupc:~# env
TERM=xterm-256color
SHELL=/bin/bash
USER=root
LS_COLORS=rs=0:di=01;34:ln=01;36:mh=00:pi=40;33:so=01;35:do=01;35:bd=40;33;01:cd=40;33;01:or=40;31;01:mi=00:su=37;41:sg=30;43:ca=30;41:tw=30;42:ow=34;42:st=37;44:ex=01;32:*.tar=01;31:*.tgz=01;31:*.arc=01;31:*.arj=01;31:*.taz=01;31:*.lha=01;31:*.lz4=01;31:*.lzh=01;31:*.lzma=01;31:*.tlz=01;31:*.txz=01;31:*.tzo=01;31:*.t7z=01;31:*.zip=01;31:*.z=01;31:*.Z=01;31:*.dz=01;31:*.gz=01;31:*.lrz=01;31:*.lz=01;31:*.lzo=01;31:*.xz=01;31:*.bz2=01;31:*.bz=01;31:*.tbz=01;31:*.tbz2=01;31:*.tz=01;31:*.deb=01;31:*.rpm=01;31:*.jar=01;31:*.war=01;31:*.ear=01;31:*.sar=01;31:*.rar=01;31:*.alz=01;31:*.ace=01;31:*.zoo=01;31:*.cpio=01;31:*.7z=01;31:*.rz=01;31:*.cab=01;31:*.jpg=01;35:*.jpeg=01;35:*.gif=01;35:*.bmp=01;35:*.pbm=01;35:*.pgm=01;35:*.ppm=01;35:*.tga=01;35:*.xbm=01;35:*.xpm=01;35:*.tif=01;35:*.tiff=01;35:*.png=01;35:*.svg=01;35:*.svgz=01;35:*.mng=01;35:*.pcx=01;35:*.mov=01;35:*.mpg=01;35:*.mpeg=01;35:*.m2v=01;35:*.mkv=01;35:*.webm=01;35:*.ogm=01;35:*.mp4=01;35:*.m4v=01;35:*.mp4v=01;35:*.vob=01;35:*.qt=01;35:*.nuv=01;35:*.wmv=01;35:*.asf=01;35:*.rm=01;35:*.rmvb=01;35:*.flc=01;35:*.avi=01;35:*.fli=01;35:*.flv=01;35:*.gl=01;35:*.dl=01;35:*.xcf=01;35:*.xwd=01;35:*.yuv=01;35:*.cgm=01;35:*.emf=01;35:*.ogv=01;35:*.ogx=01;35:*.aac=00;36:*.au=00;36:*.flac=00;36:*.m4a=00;36:*.mid=00;36:*.midi=00;36:*.mka=00;36:*.mp3=00;36:*.mpc=00;36:*.ogg=00;36:*.ra=00;36:*.wav=00;36:*.oga=00;36:*.opus=00;36:*.spx=00;36:*.xspf=00;36:
SUDO_USER=james
SUDO_UID=1000
USERNAME=root
MAIL=/var/mail/root
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
PWD=/home/james
LANG=en_IN
SHLVL=1
SUDO_COMMAND=/bin/bash
HOME=/home/james
LANGUAGE=en_IN:en
LOGNAME=root
LESSOPEN=| /usr/bin/lesspipe %s
SUDO_GID=1000
DISPLAY=:0
LESSCLOSE=/usr/bin/lesspipe %s %s
XAUTHORITY=/home/james/.Xauthority
_=/usr/bin/env

```


```

root@ubuntupc:~# echo $DESKTOP_SESSION
.......no output here........
root@ubuntupc:~# 

```

How can one know as to what desktop environments are installed on the Ubuntu system?
Thanks.

---

### Post by steeldriver on 2016-08-10
AFAIK since 12.04, there is no difference between the desktop and server kernels - so uname will not be able to distinguish a desktop system from a server system

As well, the DESKTOP_SESSION environment variable is set by a running session - assuming you're not running a desktop as root (I hope not! never do that!) it will be unset (in SSH or console logins for example)

If you want to see what desktop sessions are *installed*, you should be able to use

```

ls /usr/share/xsessions

```

---

### Post by tech291083 on 2016-08-10
> **steeldriver said:**
> AFAIK since 12.04, there is no difference between the desktop and server kernels - so uname will not be able to distinguish a desktop system from a server system

As well, the DESKTOP_SESSION environment variable is set by a running session - assuming you're not running a desktop as root (I hope not! never do that!) it will be unset (in SSH or console logins for example)

If you want to see what desktop sessions are *installed*, you should be able to use

```

ls /usr/share/xsessions

```

Yes, you are right. I can see the difference myself now. When I ran the following commands both as a normal user ie james and root. thanks a lot.

```

james@ubuntupc:~$ ls /usr/share/xsessions 
plasma.desktop  ubuntu.desktop
james@ubuntupc:~$ 
james@ubuntupc:~$ echo $DESKTOP_SESSION
ubuntu
james@ubuntupc:~$ 
======================================================================
james@ubuntupc:~$ sudo -s
[sudo] password for james: 
root@ubuntupc:~# 
root@ubuntupc:~# ls /usr/share/xsessions 
plasma.desktop  ubuntu.desktop
root@ubuntupc:~# 
root@ubuntupc:~# echo $DESKTOP_SESSION

root@ubuntupc:~# 

```

---

### Post by tech291083 on 2016-08-10
> **steeldriver said:**
> 

uname will not be able to distinguish a desktop system from a server system



Right, but there must be some way to find out, thanks.

---

### Post by grahammechanical on 2016-08-10
Installing a desktop environment will not change the kernel. I doubt that very much. 

> Before 12.04, Ubuntu server installs a server-optimized kernel by  default. Since 12.04, there is no difference in kernel between Ubuntu  Desktop and Ubuntu Server since linux-image-server is merged into  linux-image-generic.

[http://askubuntu.com/questions/31081/whats-the-difference-between-the-server-version-and-the-desktop-version](http://askubuntu.com/questions/31081/whats-the-difference-between-the-server-version-and-the-desktop-version)

Regards

---

### Post by SeijiSensei on 2016-08-10
> **tech291083 said:**
> Right, but there must be some way to find out, thanks.

A vanilla server installation has no GUI, so there is no copy of /usr/bin/X which runs the windowing system.  On a desktop, you'll see /usr/bin/X which will, if the desktop GUI is active, be running and appear in "ps ax" like this:

```
1671 ?        Ss    23:07 /usr/bin/X -core :0 -seat seat0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch
```

Of course, if you install a [klx]ubuntu-desktop meta-package you'll have a copy of /usr/bin/X, but why would you do that rather than installing desktop Ubuntu in the first place?  You can install the server packages you need like Apache or Postfix after you've installed the desktop.

---

### Post by tech291083 on 2016-09-04
> **grahammechanical said:**
> Installing a desktop environment will not change the kernel. I doubt that very much. 



[http://askubuntu.com/questions/31081/whats-the-difference-between-the-server-version-and-the-desktop-version](http://askubuntu.com/questions/31081/whats-the-difference-between-the-server-version-and-the-desktop-version)

Regards

Very nice and simple idea, really a very useful link, thanks a lot regards.

---

### Post by tech291083 on 2016-09-04
> **SeijiSensei said:**
> 

A vanilla server installation has no GUI, so there is no copy of /usr/bin/X which runs the windowing system.  On a desktop, you'll see /usr/bin/X which will, if the desktop GUI is active, be running and appear in "ps ax" like this:

```
1671 ?        Ss    23:07 /usr/bin/X -core :0 -seat seat0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch
```

Of course, if you install a [klx]ubuntu-desktop meta-package you'll have a copy of /usr/bin/X, but why would you do that rather than installing desktop Ubuntu in the first place?  You can install the server packages you need like Apache or Postfix after you've installed the desktop.

This is simply great, I just somehow wanted to find out. Thanks a lot.

---

