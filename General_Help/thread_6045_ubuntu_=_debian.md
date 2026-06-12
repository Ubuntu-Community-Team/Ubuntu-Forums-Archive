---
title: "ubuntu = debian ??"
date: 2004-11-24
forum: General Help
---

### Post by spb on 2004-11-24
I'm new to ubuntu, but I've managed debian for about a year on my workstation at the office and redhat 7.X before that.  

I installed ubuntu last night and the question that I have is how to think about it as I configure it.  Is ubuntu just debian with a 2.6.X kernel and a nice install?  If I proceed to configure my machine as if it were a debian box would there be any unpleasant surprises that I would find?  

I like debian, but the reason that I'm installing ubuntu instead of debian for my home server is that I wanted a 2.6.X kernel so I could use alsa and other modern devices.  I've tried moving from the 2.2.X kernel to at 2.6.X in Woody and found the change in the kernel tools to be a pain.  

One specific question that I have is about the kernel.  When I rebuild the kernel in ubuntu can I use the debian specific methods such as:

[http://www.holtmann.org/linux/kernel/debian.html](http://www.holtmann.org/linux/kernel/debian.html)

or do I need to use more general methods that I used when I learned redhat?  

Thank you for your advice,
spb

---

### Post by p!=f on 2004-11-24
Debian and Ubuntu
[http://www.ubuntulinux.org/ubuntu/relationship/document_view](http://www.ubuntulinux.org/ubuntu/relationship/document_view)

Just for the information. Debian Sarge, next stable release, will support 2.6 for sure.

And yes. As on every Debian-based system, compiling a kernel using kernel-package is recommended. :)

---

### Post by wayover13 on 2004-11-24
It's not quite right to say Debian doesn't have a 2.6.x kernel.  You must've been using stable.  I used Debian unstable for the last year or so, and had been running the 2.6.x kernel since 2.6.3 was released.  Not sure what kernel testing uses.

As for configuring the system, I'm still figuring that out.  I still do dpkg-reconfigure whatever for some things, but that's mainly because I don't know if Ubuntu/Gnome has some equivalent gui or something.

James

---

### Post by p!=f on 2004-11-24
[QUOTE=wayover13]It's not quite right to say Debian doesn't have a 2.6.x kernel. 
[/QUOTE]
Can't find where it was said.

[QUOTE=wayover13]
As for configuring the system, I'm still figuring that out.  I still do dpkg-reconfigure whatever for some things, but that's mainly because I don't know if Ubuntu/Gnome has some equivalent gui or something.
[/QUOTE]
```

 * 19:00:47 * pef @ agonicus *
[~] > wajig show gkdebconf
Package: gkdebconf
Priority: optional
Section: universe/admin
Installed-Size: 580
Maintainer: Agney Lopes Roth Ferraz <agney@users.sourceforge.net>
Architecture: i386
Version: 1.2.50
Depends: libatk1.0-0 (>= 1.7.2), libc6 (>= 2.3.2.ds1-4), libgconf2-4 (>= 2.7.3.1), libglib2.0-0 (>= 2.4.6), libgtk2.0-0 (>= 2.4.4), liborbit2 (>= 1:2.12.0), libpango1.0-0 (>= 1.6.0b), xterm | x-terminal-emulator, debconf (>= 1.4.3), gettext-base, gksu (>= 0.9.10)
Suggests: whiptail | dialog | gnome-utils, liblocale-gettext-perl, libterm-readline-gnu-perl, libgnome2-perl, libqt-perlFilename: pool/universe/g/gkdebconf/gkdebconf_1.2.50_i386.deb
Size: 186354
MD5sum: 6c4a55dc9400c08708e82bf73e61ff09
Description: Helper to reconfigure packages with Debconf
 This is a program that helps one using the "dpkg-reconfigure" tool.
 It is basically a graphical frontend. It makes life easier showing
 a simple menu of packages which can be reconfigured with Debconf and
 the Debconf frontends that can be used for the reconfiguration.
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu

```

---

### Post by wayover13 on 2004-11-24
[QUOTE=p!=f]Can't find where it was said.[/QUOTE]

"I like debian, but the reason that I'm installing ubuntu instead of debian for my home server is that I wanted a 2.6.X kernel" implies he thinks he could not get a 2.6.x kernel with Debian.  Thanks for the info on gkdebconf.

James

---

### Post by spb on 2004-11-24
[QUOTE=wayover13]implies he thinks he could not get a 2.6.x kernel with Debian. 

James[/QUOTE]

Starting with Woody I could move from 2.2 to 2.4, but moving from 2.4 to 2.6 involves changing the system tools.  I eventually compiled the 2.6 kernel, but it was a great deal of work and afterwards I could not get the ALSA to work properly.  I believe that I must have made some mistake compiling the modules or the module tools.  

I'm hoping that using ubuntu I will be able to configure the 2.6 kernel easier and there will be fewer mistakes on my end.  

I'm glad to hear that the basics that I learned from working with Woody can be used to configure and manage Warty.  I still have a great deal to learn, but knowing that there are no hidden surprises between the two is reassuring.

---

### Post by wayover13 on 2004-11-25
To move to 2.6.x in Debian, I just apt-get(ted) the 2.6.x kernel image.  I had to go through a bit of tweaking (mouse was lost, pcspeaker module not loading), but after those hiccups, things worked great.  I got the 2.2.20 kernel when I installed, too (started from floppies).  This is just the standard install kernel.  But I immediately put unstable repositories in sources.list and did apt-get dist-upgrade and went with the newest 2.4.x kernel.  Anyway, very similar principles on Ubuntu except everything should be done through the Gnome interface as much as possible.  Hoary is the Ubuntu unstable, in case you hadn't heard that.  Warty is like Woody/stable.

James

---

### Post by CyBEr-GaNgE on 2004-11-25
[QUOTE=wayover13]To move to 2.6.x in Debian, I just apt-get(ted) the 2.6.x kernel image.  I had to go through a bit of tweaking (mouse was lost, pcspeaker module not loading) [...] I immediately put unstable repositories in sources.list and did apt-get dist-upgrade James[/QUOTE]

I had the same problem spd have.
I'm looking for a Debian based distro, easy to configure.
I don't have a fast internet connection, for this reason I'm looking for a good distro with the possibility to add some Debian package...
For now ububtu seems to work....for now

---

