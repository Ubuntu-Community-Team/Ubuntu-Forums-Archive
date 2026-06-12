---
title: "Need help to install lphoto and nvu"
date: 2005-08-24
forum: General Help
---

### Post by blackant on 2005-08-24
I have found these two softwares,

[http://lphoto.com/?page=downloads](http://lphoto.com/?page=downloads)

and

[http://www.nvu.com/download.html](http://www.nvu.com/download.html)

But I am a newbie to Linux, and don't know which to download or install.
Can anyone guide me with steps by steps?

Thank you.

---

### Post by lol on 2005-08-24
nvu is available via apt (or synaptic or whichever method you use to install software from the repositories).

lphoto is more troublesome to install. The version 1 is IMHO not worth the trouble, and I have never been able to install the version 2 (haven't tried very hard either though).

If you still want to do it, the best way to install it (version 1) is to download the debian tar.gz, and then, in a terminal, run the following commands:

tar xvfz lphoto_1.0.4.tar.gz
cd lphoto-1.0.4
dpkg-buildpackage
dpkg -i ../lphoto_1.0.4_i386.deb

dpkg-buildpackage will probably fail the first time because of unresolved dependencies. If so, install the missing librairies and try again.

---

### Post by blackant on 2005-08-24
[QUOTE=lol]nvu is available via apt (or synaptic or whichever method you use to install software from the repositories).

lphoto is more troublesome to install. The version 1 is IMHO not worth the trouble, and I have never been able to install the version 2 (haven't tried very hard either though).

If you still want to do it, the best way to install it (version 1) is to download the debian tar.gz, and then, in a terminal, run the following commands:

tar xvfz lphoto_1.0.4.tar.gz
cd lphoto-1.0.4
dpkg-buildpackage
dpkg -i ../lphoto_1.0.4_i386.deb

dpkg-buildpackage will probably fail the first time because of unresolved dependencies. If so, install the missing librairies and try again.[/QUOTE]
I couldn't find it in the apt-get. :(
What should I add?

---

### Post by arnieboy on 2005-08-24
[QUOTE=blackant]I couldn't find it in the apt-get. :(
What should I add?[/QUOTE]
read [http://ubuntuguide.org](http://ubuntuguide.org) u will find answers to most of your questions there.

---

### Post by blackant on 2005-08-24
[QUOTE=arnieboy]read [http://ubuntuguide.org](http://ubuntuguide.org) u will find answers to most of your questions there.[/QUOTE]

For some reason, it still couldn't find the nvu package even after I try the guide.

I did this auto script before.
[http://ubuntuforums.org/showthread.php?t=22646](http://ubuntuforums.org/showthread.php?t=22646)

Any help?
Thanks

Btw, I download the nvu from the official site, can help to install by issuing a command to it?

Thanks.

---

### Post by rwabel on 2005-08-25
try out f-spot instead of lphoto. It's still an early project but looks incredible. But I haven't seen lphoto :-)

---

