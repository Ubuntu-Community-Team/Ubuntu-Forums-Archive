---
title: "I need to edit a deb package -- how?"
date: 2007-04-04
forum: General Help
---

### Post by mpooley on 2007-04-04
Hi
I have a problem with a Brother fax driver that has been converted from an RPM using alien.
and it doesnt work!
I need to edit a few lines but as a complete newbie i dont know how?
when i open the package using ark it wont allow me to edit any of the files, I tried saving the file in a different name but its still the same.
can anyone tell me how to do this please?

---

### Post by josephus on 2007-04-04
not clear what you are trying to edit in this file.  anyway look at your other thread.

---

### Post by brentoboy on 2007-04-04
yeah,  I'm kind of curious about what you would change really.

on the filp side of that, if things arent set up correctly by the installer, and you know what should be done differently, there is nothing stopping you from taking the resulting files and changing them after installation.

installing a deb file is nothing more than unzipping its contents and then running a script that activates things that need special attention.

It worries me that you know what to change but not how.  I would think that to really know what needs to change (in a safe sort of "know what you are doing" sort of way) you would need to have a decent amount of pre-knowledge about how those things are unrolled.

I guess I dont really understand deep down what you want to do, and maybe that is why I'm a bit uncomfortable with your question.

---

### Post by mpooley on 2007-04-04
HI and thanks for your interest.

Well,   I am getting any info from asking on this and other forums. so I know only what i'm told!
I know that Debian uses the cupsys command not cups so i just wanted to alter the three times that this is used in the installer.

I didn't know how else i could do it - so thats why i wanted to know.

Now you and josephus have told me there is another way but until than i didnt know that.

by googling i found an old thread that did allow me to change the package and it installed ok but it is interesting to learn of other methods. The fax still doesn't show up in the cups list though!! but at least the ppd file is loaded and i can choose it manually.

Trouble is that to a newcomer to linux all this is extremely difficult and confusing. I'm here to learn though and i know i will get there in the end!



I am still trying to work out how to send a fax straight out through my fax machine on the network i've followed the instructions on the Brother site meticulously but it just doesn't happen -- no errors nothing - just a jumping hourglass for a few seconds !

I DO appreciate all the help i have been given though!

---

### Post by brentoboy on 2007-04-04
if it were me, I wouldnt use the aliened rpm package, I would find a tarball installer.  Most packages (like on sourceforge or wherever) offer tarballs as thier lowest common denominator linux package.

if you unzip (or unroll) the tarball file, you go into the folder and "make" and then "install" it, and it should have scripts that work on pretty much any version of linux.  There are lots of howtos about installing from tarball, so I am not going to outline it here.

But I would certainly do it that way before I messed around with a deb file that was aliened from somewhere else.

if you have a tarball, and want to create a deb file from it so that apt will know it has been installed and so things will be clean on your system, maybe this will help...
[http://doc.gwos.org/index.php/Deb_Guide](http://doc.gwos.org/index.php/Deb_Guide)

---

### Post by mpooley on 2007-04-04
Thanks i will look into that.

:KS

---

