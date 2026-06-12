---
title: "Monitor Calibration -- Installing &quot;Monica&quot;"
date: 2007-03-21
forum: General Help
---

### Post by jomiz80 on 2007-03-21
I'm trying to get [[COLOR="Blue"]Monica[/COLOR]]("http://www.pcbypaul.com/software/monica.html") working 6.10. I could not find any packages to automatically install it. Of course, I'm kinda new to linux (loving it so far!) and I can't get it to work.

Anyways, I've tried to do a compile of the source code. Here is a list of what I've done:

1_ Downloaded the source from [[COLOR="Blue"]here[/COLOR]]("http://www.pcbypaul.com/software/monica.html")
2_ Tried to 'make', but got errors, because I needed to install FLTK and some dev packages from synaptic.
3_ After installing dependencies, was able to successfully 'make' and 'make install' Monica
4_ However, I get this error message in a graphical pop-up, and then Monica closes:

> Monica cannot read your /etc/inittab file...

This is used by Monica to determine your login type, graphical login and place the call to monicarc into the .xinitrc file in your home directory.

Any suggestions on what my next steps should be?  Thanks.

---

### Post by Nikos.Alexandris on 2007-09-12
Hi!

Did you have any success installing monica?

Would be happy with a positive reply.

Nikos.

---

### Post by TimGS on 2007-11-20
Nikos - I've just installed Monica from sourcecode.

First you need to go to Synaptic and install FLTK. At first I just installed 'linfltk1.1' which wasn't enough - so then I went pack and installed libfltk1.1-dev and libfltk1.1-dbg which did the trick.

One thing I haven't managed to work out is how to adjust the colour temperature of the display.

-- Tim.

---

### Post by Zoggy888 on 2008-04-08
I'm having the same issue with Monica unpacked from the binary, monica-3.4_gcc-3.3.5:

> Monica cannot read your /etc/inittab file...

This is used by Monica to determine your login type, graphical login and place the call to monicarc into the .xinitrc file in your home directory.

Can anyone help?  I'm running Gutsy.

---

### Post by Zoggy888 on 2008-04-09
After some googling, found out that ubuntu had stop using inittab (since edgy?) and is using upstart now,  But there's a workaround, do :

> sudo cp /usr/lib/upstart/migrate-inittab.pl /etc/inittab

Now you can start monica without any problem.

But do remember to remove / rename the inittab afterward, as it might interfere with your next start up.

---

