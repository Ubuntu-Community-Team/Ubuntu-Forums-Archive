---
title: "Adding Times New Roman font to my fonts"
date: 2013-03-14
forum: General Help
---

### Post by babakflame on 2013-03-14
Hi buddies
How can I add Times New Roman font to my libreoffice fonts?

    Regards
     Bobi

---

### Post by Laobi on 2013-03-14
Install MS Core Fonts:
```
sudo apt-get install ttf-mscorefonts-installer 
```

---

### Post by varunendra on 2013-03-14
..or simply copy the desired ttf font file to your **/usr/share/fonts** directory.

For example, if the times.ttf file is on your desktop, then in a terminal do -
```
sudo cp ~/Desktop/times.ttf /usr/share/fonts
```

Now run libre office writer and pick the font from the fonts list. :)

---

### Post by babakflame on 2013-03-14
Dear Laobi
Hi 
after I run the aforementioned directive, Sth that had a software configuration  name appeared on terminal.:confused::confused::confused:
After I run Ctrl + c
I came out of terminal and by running again the directive I got this message:
[HTML]
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

[/HTML]
 Ichecked my libreOffice , I have still do not access to TimesNew Roman Font.:(:(:frown::frown:

---

### Post by varunendra on 2013-03-14
> **babakflame said:**
> 
```
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
```

**[SIZE=4]Never ever interrupt an installation process..![/SIZE]**

What you saw in terminal, I assume, was the stage when the installer starts downloading MS fonts. IIRC, it does not show any continuous progress indication, but keeps downloading in the background, and only displays a new line when one font package is downloaded and next one is in progress.

You interrupted it in the middle of the process, hence the error now, and no font.

Anyway, enough of the horror show, the solution, luckily, is easy :)
For the font, just do what I suggested if you already have the font(s) available (in windows, the font directory is **windows\fonts**, where you can copy the font from).

For the lock error (the real issue), please do in a terminal -
```
sudo rm /var/lib/dpkg/lock
```
This will delete the lock file which will be auto-generated when the package manager is run again.

---

### Post by babakflame on 2013-03-14
Dear Varun
Hi
Thanks for yr hints.
 This time I did exactly what u have mentioned, I can see times.ttf in /use/share/fonts folder albeit, when I run the libreoffice writer There is still no TimesNewRoman font.:confused::confused:

Can I still use directives for installling MS-word fonts automatically for ibreoffice?
I typed the directive
sudo apet-get install ttf-mscorefonts installer and I got this error:

babak@babak-VPCEA26FG:~$ sudo rm /var/lib/dpkg/lock
babak@babak-VPCEA26FG:~$ sudo apt-get install ttf-mscorefonts-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  libntfs10
Use 'apt-get autoremove' to remove them.
The following packages will be upgraded:
  ttf-mscorefonts-installer
1 upgraded, 0 newly installed, 0 to remove and 27 not upgraded.
1 not fully installed or removed.
E: Could not get lock /var/cache/apt/archives/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/cache/apt/archives/



    Regards
      Bobi

---

### Post by varunendra on 2013-03-14
Well.. I already have Times font installed the proper way, so can't re-test it.

If you double-click the font file, it should open with "Font viewer". If so, there should be a button "Install Font" at the bottom right corner of the viewer. Try it, hopefully, it'll do the job for you.

By the way, I have installed a few fonts at different times using the previously stated method. Don't remember if I needed to do anything else, but one of the fonts I just copied (and can access in libre office) is in the **/usr/share/fonts** directory, and two others are in **/usr/share/fonts/truetype** directory.

The MS fonts were installed with wine and they reside in **/usr/share/fonts/truetype/msttcorefonts** directory. If the Font Viewer trick doesn't help, you can try manually copying to these locations.

Or maybe do a restart for the change to take effect (although I just tried with another font and it worked instantly!)

As for the "Unable to lock" error, is the **/var/lib/dpkg/lock** file still there?

---

### Post by babakflame on 2013-03-14
[HR][/HR]Dear My friend Varun
Thnks Buddy . My problem Solved.:guitar:
  Regards
    Bobi

---

### Post by varunendra on 2013-03-14
> **babakflame said:**
> My problem Solved

Sweet! Please mark the thread as [solved] then (follow the 'how to' link in my signature to see how).

If the package manager problem persists (the unable to lock.... error), start a new thread for it.

---

