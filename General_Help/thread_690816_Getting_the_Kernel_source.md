---
title: "Getting the Kernel source"
date: 2008-02-07
forum: General Help
---

### Post by CaesarLike on 2008-02-07
HI all,

I am trying to use some commands to get a copy of my kernel to do a few tweaks to it.  The code comes from a computer magazine article on how to compile a custom kernel.  The magazine is Australian Personal Computer, Jan 2008 issue [page 78].  However, I am having problems running the command, as it asks for the installation disk to copy the kernel.  But when I put the installation disk in, the terminal does not recognise it.  Below is the shell command the magazine provides.  I have typed it exactly as shown in the magazine, but the actual correct format is not quite clear to me, so I may be typing it incorrectly in the terminal.

[COLOR="Blue"]
sudo -s

apt-get install build-essential bin86
kernel-package libqt3-headers
libqt3-mt-dev wget libncurses5
libncurses5-dev linux-kernel-devel
linux-source[/COLOR]

Can anyone see what the problem is with the command.  What is the correct format for the command, as I assume this is not typed into the terminal the way it is shown.

---

### Post by pointone on 2008-02-07
[http://ubuntuforums.org/showthread.php?t=311158](http://ubuntuforums.org/showthread.php?t=311158)

---

### Post by bilge.tutak on 2008-02-07
Check your /etc/apt/sources.list file and see if it is set to CDROM. Unless you are intentionally trying to use the CDROM as a source. If you want to download them from internet, then you should give some apt sources (or uncomment the ones in your file).

---

