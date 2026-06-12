---
title: "Illegibly small fonts"
date: 2007-09-24
forum: General Help
---

### Post by nilpill on 2007-09-24
I've been using Kubuntu Feisty Fawn for about half a year now, and about a month ago, something weird happened to my fonts. In most cases, the fonts are just fine, but at the OS's login window and in a few certain programs (like aMSN), the fonts are so incredibly tiny, there is no way anyone could possibly read it. Could you give me any help in fixing this?

Here's what it looks like:

[ATTACH]44348[/ATTACH]

---

### Post by jualin on 2007-09-24
Go to the console and write 
```
kcontrol
```
Then go to appearance & themes, and then Fonts. Check wether the font sizes are correct.
I hope this helps:)

---

### Post by nilpill on 2007-09-26
Unfortunately, it's not as simple as that. All my font settings (at least, in that menu) are fine, but the problem is still there. I actually migrated over to Ubuntu to see if Kubuntu was actually the source of my woes, but that doesn't seem to be the case, as Ubuntu shows the same problem.

On the bright side, I have found the reason for the odd font sizes. It appears to be directly connected to me using the ATI driver, because it only happens when I've set Ubuntu to use it instead of the generic driver.

Now that I know where the problem lies, could that give you guys more headway into the solution to this problem? (Other than removing the ATI driver, of course. I need that 3D acceleration.)

I've made another screenshot to illustrate how the problem only occurs in a few programs, and that it it has nothing to do with my font settings:

[ATTACH]44482[/ATTACH]

---

### Post by strabes on 2007-09-26
Sorry for the non-answer, but ATI is expected to release acceptable linux drivers in October.

---

### Post by nilpill on 2007-09-26
Not exactly a real solution, no, but at least it's good to hear.

Here's hoping the new drivers fix this thing! :-D

---

### Post by SeanTater on 2007-09-26
Just the same thing happened to me about 3 days ago.

Do we have any of the following in common (because this is what I changed that caused it)

Multiple monitors (clones), with different resolutions

Hand-edited xorg.conf file

Unusual resolution (1336by768 what what I think I had it at)

lspci says: 01:05.0 VGA compatible controller: ATI Technologies Inc ATI Radeon XPRESS 200M 5955 (PCIE)

Using FGLRX

Using Feisty


And I fixed it by doing:

sudo dpkg-reconfigure --default-priority xserver-xorg
and choose "fglrx"

NOTE: This will destroy anything you did by hand..

---

### Post by nilpill on 2007-09-27
The only things in common is that we're using FGRLX and Feisty, but I tried your solution anyway, with odd results. It didn't fix the whole problem, but the Ubuntu splash screen has the right font size now. The login page and AMSN are still shot, though.

---

### Post by Bill_ on 2007-10-02
I've had the same thing happen to me too just recently.
My login window has very small fonts but the whole login window is so big that only part of it is displayed at a time, and the fonts in amsn have become really small.
I have an nvidia card and it happens when I'm using the nvidia-glx driver, but not with the opensource one.

---

### Post by buanzo on 2007-10-29
I have exactly the same situation described in the previous message: Nvidia, very small login screen fonts (which, apparently, I fixed by means of setting the Session Manager's fonts via KDE Settings menu), and just tested amsn, and it also has excessively small fonts.

Any ideas?

---

