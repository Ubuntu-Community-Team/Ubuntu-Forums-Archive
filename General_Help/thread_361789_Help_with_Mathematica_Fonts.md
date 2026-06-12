---
title: "Help with Mathematica Fonts"
date: 2007-02-14
forum: General Help
---

### Post by Mets on 2007-02-14
Hi I'm trying to get Mathematica to work on Edgy and I'm having a few problems.  The program runs fine, but there seems to be some fonts missing.  Is there an apt-get package of Mathematica fonts that's easy to install?  I know Gentoo has a package (emerge mathematica_fonts), though I've seen some problems configuring that.

If there isn't, then I actually have legal copies of both the TTF and Type1 fonts, but I haven't a clue how to install them.  I run Mathematica through ssh (i.e. I ssh -x into one of the Unix servers here on campus and run Mathematica over that).  Can anybody help me with installing these?  Thanks a lot.

---

### Post by kevinlyfellow on 2007-02-22
Have you tried dropping them into a directory under
/usr/local/Wolfram/Mathematica/5.2/SystemFiles/Fonts

I have the same problem, but I have a bigger issue I'd like to get your feedback from.  When I try to open a document from the gui, I get a segmentation fault.  This started happening when I upgraded to edgy.  Have you had this issue?

---

### Post by ntetreau on 2007-02-23
Same problem here, segmentation fault when opening a document!

Nic

---

### Post by peterhaagerup on 2007-02-28
It seems like i solved the problems with the fonts and segmentation fault:
[http://www.ubuntuforums.org/showthread.php?t=371141](http://www.ubuntuforums.org/showthread.php?t=371141)

---

### Post by kevinlyfellow on 2007-02-28
Thank you so much!!!  I started to try doing something similar to that (I found in fedora forums) but didn't seem to work!  Thank you again!

BTW I just found a *potential* solution to the beryl issue
[http://forum.beryl-project.org/viewtopic.php?f=39&t=3781](http://forum.beryl-project.org/viewtopic.php?f=39&t=3781)

EDIT: Confirmed... start mathematica from the provided shell script and indeed it works!!!  Further, you can remove any references to imwheel.  Infact, theres probably a better way to do it for us

---

### Post by kevinlyfellow on 2007-03-01
I tried to put XLIB_SKIP_ARGB_VISUALS=1 into /etc/environment and while mathematica would work fine, the window decorator refused to start.  So it seems be to leave it in the script

---

### Post by gringogrande on 2007-03-02
Actually, I tried installing the windows version with Wine 0.9.31 and it works pretty nicely. The only problem encountered is that it crashes as soon as you enter a erroneous expression. Turns out it is the system beep that causes it to crash, but you can just turn it off in the options.

Other than that, I have to say that it's a much nicer interface than using Motif since that only gave me grief, with transparent colors, wonky keymaps, no scrollwheel etc.

So in other words, I suggest using it with wine instead.

---

### Post by kevinlyfellow on 2007-03-03
I was doing that, but I was getting funky symbols everywhere.  As of now, everything works on the linux version, so I'm happy.  I've never been any good at getting things to run properly under wine.

I do wish that Wolfram would take better care of the linux gui.  It is understandable though, since they won't know what kind of graphical environment people will be using for science applications.

---

### Post by neoguy2012 on 2007-06-30
Hi,

In case Peter's solution didn't solve your font problem, you might have to put the Mathematica fonts into that directory if you haven't done so already.  You can obtain the fonts from the Mathematica website here:

[http://support.wolfram.com/mathematica/systems/macintosh/general/latestfonts.en.html](http://support.wolfram.com/mathematica/systems/macintosh/general/latestfonts.en.html)

Good luck!

---

