---
title: "Rdesktop segmentation fault"
date: 2007-04-07
forum: General Help
---

### Post by gejr on 2007-04-07
I use tsclient(rdesktop frontend) to connect to my windows machine. And I get "Segmentation fault (core dumped)" every time  i open the startmenu and click on the desktop somewhere to remove it. As if this wasn't enough..rdesktop always crashes after 10-20 seconds with the same segfault error. 

What can be wrong? are there any alternatives to rdesktop? I do not want to use VNC.

 

Bug?

---

### Post by gejr on 2007-04-07
I uninstalled rdesktop 1.5  and installed 1.4.1 from source. That fixed the problem. Hopefully it's an error that will be addressed. I have no idea how to post bugreports..and I'm not even sure it's a bug or another ebkac.

---

### Post by Eddie Hung on 2007-04-15
The bug report relating to this issue can be found here: [https://bugs.launchpad.net/bugs/104332](https://bugs.launchpad.net/bugs/104332)

As you can see, they haven't answered my question =(

Eddie

EDIT: This bug is fixed in debian:
Information: [http://packages.qa.debian.org/r/rdesktop.html](http://packages.qa.debian.org/r/rdesktop.html)
Deb file: [http://mirror.positive-internet.com/debian/pool/main/r/rdesktop/rdesktop_1.5.0-2_i386.deb](http://mirror.positive-internet.com/debian/pool/main/r/rdesktop/rdesktop_1.5.0-2_i386.deb)

I've tested it myself and it works!

---

### Post by MFH on 2007-07-18
> **Eddie Hung said:**
> The bug report relating to this issue can be found here: [https://bugs.launchpad.net/bugs/104332](https://bugs.launchpad.net/bugs/104332)

As you can see, they haven't answered my question =(

Eddie

EDIT: This bug is fixed in debian:
Information: [http://packages.qa.debian.org/r/rdesktop.html](http://packages.qa.debian.org/r/rdesktop.html)
Deb file: [http://mirror.positive-internet.com/debian/pool/main/r/rdesktop/rdesktop_1.5.0-2_i386.deb](http://mirror.positive-internet.com/debian/pool/main/r/rdesktop/rdesktop_1.5.0-2_i386.deb)

I've tested it myself and it works!
well, "positive internet" if you're on i386...

To be useful to others, on amd64 I had to do :

# wget [http://http.us.debian.org/debian/pool/main/r/rdesktop/rdesktop_1.5.0-2_amd64.deb](http://http.us.debian.org/debian/pool/main/r/rdesktop/rdesktop_1.5.0-2_amd64.deb)
# dpkg --ignore-depends=libc6 -i rdesktop_1.5.0-2_amd64.deb
(Reading database ... 110835 files and directories currently installed.)
Preparing to replace rdesktop 1.5.0-2 (using .../tmp/rdesktop_1.5.0-2_amd64.deb) ...
Unpacking replacement rdesktop ...
Setting up rdesktop (1.5.0-2) ...

But now indeed it works. Thanks for your hint which guided me to the goal...

---

### Post by CrucifiedEgo on 2007-10-04
A general thanks -- rdesktop crashed every few minutes -- the new .deb worked fine for me!

-J

---

