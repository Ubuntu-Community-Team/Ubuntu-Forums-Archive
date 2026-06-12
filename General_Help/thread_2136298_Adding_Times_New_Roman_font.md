---
title: "Adding Times New Roman font"
date: 2013-04-17
forum: General Help
---

### Post by emtom on 2013-04-17
using **sudo apt-get install ttf-mscorefonts-installer** got me to the configuration package window (Configuring ttf-mscorefonts-installer) with the EULA. But nothing seems to be happening. 

Do I need to press keys or click somewhere to install?

---

### Post by howefield on 2013-04-17
Press the tab key to highlight the ok button and press enter.

---

### Post by emtom on 2013-04-17
Thank you, howefield. It worked! It took me few tries to use autoremove, and here's the result.

E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
tombaldwin@tombaldwin-VGC-RB52:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-headers-3.5.0-17 linux-headers-3.5.0-17-generic
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
After this operation, 69.9 MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 181282 files and directories currently installed.)
Removing linux-headers-3.5.0-17-generic ...
Removing linux-headers-3.5.0-17 ...
tombaldwin@tombaldwin-VGC-RB52:~$ sudo cp ~/Desktop/times.ttf /usr/share/fonts
[sudo] password for tombaldwin: 
cp: cannot stat `/home/tombaldwin/Desktop/times.ttf': No such file or directory
tombaldwin@tombaldwin-VGC-RB52:~$ 

From what I've read in [http://ubuntuforums.org/showthread.php?t=2125494&highlight=times+roman](http://ubuntuforums.org/showthread.php?t=2125494&highlight=times+roman) (where I found the install code), it looks like I now have to use something like

sudo cp ~/Desktop/times.ttf /usr/share/fonts

but that command yielded this result cp: cannot stat `/home/tombaldwin/Desktop/times.ttf': No such file or directory

I've tried searching for times.ttf in my computer but cannot locate it. Is there a default folder where all of the files are?

---

### Post by emtom on 2013-04-17
I searched for and found **times.ttf** using **Location - File System**. The file's properties said** times.ttf** is in** /usr/share/fonts/truetype/msttcorefonts**, which, with the exception of the **/truetype/msttcorefonts** part, seems to be where instructions in other posts said to copy it, using the form **sudo cp ~/Desktop/times.ttf /usr/share/fonts**. Which seems like sending it to its own registry. At this point, I'm pretty confused. I'm viewing posts, hoping to find a solution. It's time for a break.

I copied **times.ttf** to the Desktop and retried** sudo cp ~/Desktop/times.ttf /usr/share/fonts**, but got the message "No such file or directory".

---

### Post by deadflowr on 2013-04-17
Try running
```
fc-cache -fv
```

This will reload your font cache, and update the fonts loaded in the system.

---

### Post by emtom on 2013-04-17
Thank you, deadflowr! It worked! Opening a new document in LibreOffice Writer showed the font set at Times New Roman. Opening a new workbook in LibreOffice Calc showed the font set at Arial and New Times Roman on the font list. Thank you!

---

