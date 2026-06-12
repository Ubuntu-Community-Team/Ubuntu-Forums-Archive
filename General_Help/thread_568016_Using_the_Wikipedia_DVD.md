---
title: "Using the Wikipedia DVD"
date: 2007-10-05
forum: General Help
---

### Post by PmDematagoda on 2007-10-05
I've just installed the Wikipedia DVD, but when I try to start it up it just doesn't do anything, does anyone know why this happens?:confused: Or could anyone give me a good guide on installing the Wikipedia DVD?

---

### Post by PmDematagoda on 2007-10-05
I need help on this as I am about install Ubuntu on my uncle's computer, without any form of offline encyclopaedia he will not accept it. So basically it's either getting the Wikipedia DVD to work or curtains on my hopes of converting my family to the Linux faith:(.

---

### Post by GavinZac on 2007-10-05
Is the Wikipedia DVD made for Windows?

If so, you could try using it with WINE

---

### Post by PmDematagoda on 2007-10-05
Actually the Wikipedia DVD can be installed purely for Linux as well, so while I can use Wine, it is better if I use the normal Linux version for reliability purposes.

---

### Post by bubbalouie on 2007-10-05
Seems to work for me, though I am using the wikipedia CD (my ISP makes it an unmetered download :) ), I couldn't find the DVD and I am running low on quota right now.  However, just double clicking the start script fails.

I have mounted the ISO file onto a directory **/home/ryan/virtual-drives/1/** I used acetoneiso2 to do this.

Then I fire up a console and type the following **./kiwix.sh** from within the mounted location.

Then I am met with a glorious 0.5 wikipedia browser. The logical fix to mounting the ISO, would be to copy the files direct from the CD ISO (or I guess in your case the DVD) to a location in your home directory and run the script from there, you could very easily make a link to run it on you uncles desktop to save him from the dreaded console.

I have attached a screen shot to show the tools, look at the console for hints :)

Good luck

*EDIT: the following command works when put into a shortcut **sh /home/ryan/Program_Files/Kiwix\ 0.5/kiwix.sh** I copied the files from the ISO to a location in my home folder and it works a treat

---

### Post by PmDematagoda on 2007-10-06
I tried that, but the only thing I got was:-

```
Segmentation fault (core dumped)
```

Is there anything else I should do?

---

### Post by bubbalouie on 2007-10-06
Try a different version of the disk, I'd say something is broken on the DVD ISO. Unfortunately I can't tell you more, a segfault basically means it  is trying to access something in memory it isn't allowed to touch. 

Strangely I found my copy won't run off the CD when you burn it, it only works when running of a mounted ISO or from a directory on my hard disk. Perhaps the software is trying to write to a file on the CD and can't manage it (maybe accessing files using pointers to the file object they created would cause a segfault if the file is read only, but it has been a long time since I wrote C or C++ for a program on an operating system :( ), really speaking I don't have time to try and track which programs are accessing what files when I launch kwix (sorry).

Sadly the best I can advise is: Run from you hard disk, Try a different version of ther software.

If the windows version runs, the new version of wine (0.9.46) is VERY stable and may be worth a try, even with some other offline encyclopedia (whatever your uncle uses now would be great, it would reduce the learning curve). I personally run some of my development tools under wine, CrossWorks (a nice little IDE for micrcontrollers), ARMWSD (The Analog Devices MCU flash loader), SWCAD III (Linear Technologies electronics simulation tool), and I have had no issues, even when using the serial port or doing printing. The following link is what I used to get the latest version of wine: [http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

Good luck :)

---

### Post by PmDematagoda on 2007-10-06
Thanks bubbalouie.

---

### Post by Hobbes on 2007-12-03
I can confirm that trying to run the script from the mounted iso fails, and after using their "kiwix-installer-linux" script, which appears to have worked... i also get a segmentation fault from running the .sh file from my home directory.

Using wine the .exe file works however...

Peace.

---

