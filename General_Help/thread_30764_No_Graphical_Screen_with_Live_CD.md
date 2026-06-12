---
title: "No Graphical Screen with Live CD"
date: 2005-04-30
forum: General Help
---

### Post by mkoljack on 2005-04-30
I'm using the kubuntu live cd.  Everything goes fine, it appears to be loading, no error messages, then I get a command line, $   Am I missing something or isn't it supposed to go into graphical mode and load KDE.  I am using a ATI Radeon 9200 video card, basic Samsung 710 LCD monitor, external Creative USB sound card.  What am I doing wrong? Appreciate any help as I am fairly new to this.

Thank you.  Mark

---

### Post by xodeus on 2005-04-30
[QUOTE=mkoljack]I'm using the kubuntu live cd.  Everything goes fine, it appears to be loading, no error messages, then I get a command line, $   Am I missing something or isn't it supposed to go into graphical mode and load KDE.  I am using a ATI Radeon 9200 video card, basic Samsung 710 LCD monitor, external Creative USB sound card.  What am I doing wrong? Appreciate any help as I am fairly new to this.

Thank you.  Mark[/QUOTE]
Does the coomandline tell you to login or is it just saying $??
When it's saying $ then try to type startx and ENTER.
Then tell us the messages you get

---

### Post by mkoljack on 2005-04-30
After issuing the startx command, output was:

skipping /usr/x11r6/lib/modules/extensions/libglcore.a: no symbols found
invalid memory allocation
cannot read bios
vbe initialization failed
screens found but none have a usable configuration
fatal server error: no screens found
x:10 fatal io error 104 on x server

I then disabled the ATI Radeon 9200 video card and used the integrated video card.
No problem going right into graphical mode -- KDE 3.4 looks great.

If I install Kubuntu on the HD, do you think the video card detection will be a problem or is this only an inherent problem with the live cd?

Thank you for your kind response.  Mark

---

