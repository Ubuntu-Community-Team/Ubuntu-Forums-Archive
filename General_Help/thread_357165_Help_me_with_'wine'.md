---
title: "Help me with 'wine'"
date: 2007-02-09
forum: General Help
---

### Post by DougieFresh4U on 2007-02-09
I have downloaded the file for a game from Gamehouse Games (.exe.) It's listed under Applications>Other and when I try to open it, wine desktop does a quick flash and disapears. Any suggestions please!!!:confused: I should also mention I can not get to bottom of wine config window to click apply (see screenshot)

---

### Post by Irony on 2007-02-09
Run the command from terminal and post the results, e.g.;

[PHP]wine "/mnt/hda1_XPHome/Program Files/Photostudio/PSTUDIO.EXE"[/PHP]

Note, enclose the path in quotes in case there are any spaces in the path.

---

### Post by rich.bradshaw on 2007-02-09
What happened to your theme? I though mine was weird cos I changed it from human to clearlooks... :)

---

### Post by DougieFresh4U on 2007-02-09
> **Irony said:**
> Run the command from terminal and post the results, e.g.;

[PHP]wine "/mnt/hda1_XPHome/Program Files/Photostudio/PSTUDIO.EXE"[/PHP]

Note, enclose the path in quotes in case there are any spaces in the path.
dougie@DougiesToyBox:~$ /mnt/hda1_XPHome/Program Files/Photostudio/PSTUDIO.EXE
bash: /mnt/hda1_XPHome/Program: No such file or directory
dougie@DougiesToyBox:~$ "/mnt/hda1_XPHome/Program Files/Photostudio/PSTUDIO.EXE" 
bash: /mnt/hda1_XPHome/Program Files/Photostudio/PSTUDIO.EXE: No such file or directory
dougie@DougiesToyBox:~$

---

### Post by taurus on 2007-02-09
```
**wine** "/mnt/hda1_XPHome/Program Files/Photostudio/PSTUDIO.EXE" 
```

---

### Post by DougieFresh4U on 2007-02-09
> **taurus said:**
> ```
**wine** "/mnt/hda1_XPHome/Program Files/Photostudio/PSTUDIO.EXE" 
```

dougie@DougiesToyBox:~$ wine "/mnt/hda1_XPHome/Program Files/Photostudio/PSTUDIO.EXE"
wine: cannot find '/mnt/hda1_XPHome/Program Files/Photostudio/PSTUDIO.EXE'
dougie@DougiesToyBox:~$

---

### Post by taurus on 2007-02-09
```
ls -la /mnt/hda1_XPHome/Program Files/Photostudio
```

---

### Post by DougieFresh4U on 2007-02-09
> **taurus said:**
> ```
ls -la /mnt/hda1_XPHome/Program Files/Photostudio
```

dougie@DougiesToyBox:~$ ls -la /mnt/hda1_XPHome/Program Files/Photostudio
ls: /mnt/hda1_XPHome/Program: No such file or directory
ls: Files/Photostudio: No such file or directory
dougie@DougiesToyBox:~$

---

### Post by taurus on 2007-02-09
```
ls -la "/mnt/hda1_XPHome/Program Files"
```

---

### Post by Motoxrdude on 2007-02-09
Can you just give us the directory of it so we dont have to keep guessing?

---

### Post by DougieFresh4U on 2007-02-09
> **taurus said:**
> ```
ls -la "/mnt/hda1_XPHome/Program Files"
```

WTF:::dougie@DougiesToyBox:~$ ls -la "/mnt/hda1_XPHome/Program Files"
ls: /mnt/hda1_XPHome/Program Files: No such file or directory
dougie@DougiesToyBox:~$

---

### Post by taurus on 2007-02-09
```
ls -la /mnt/hda1_XPHome
-or-
df -h
```

---

### Post by DougieFresh4U on 2007-02-09
> **taurus said:**
> ```
ls -la /mnt/hda1_XPHome
-or-
df -h
```

not sure I understood your code correctly???   dougie@DougiesToyBox:~$ ls -la /mnt/hda1_XPHome
ls: /mnt/hda1_XPHome: No such file or directory
dougie@DougiesToyBox:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1              36G  4.3G   30G  13% /
varrun                125M   92K  125M   1% /var/run
varlock               125M     0  125M   0% /var/lock
procbususb             10M   68K   10M   1% /proc/bus/usb
udev                   10M   68K   10M   1% /dev
devshm                125M     0  125M   0% /dev/shm
lrm                   125M   26M  100M  21% /lib/modules/2.6.20-6-generic/volatile
dougie@DougiesToyBox:~$

---

### Post by Irony on 2007-02-09
Find the path to **your** particular executable.

You will have to find your correct path, if it is showing in applications you can find it by doing;

*System tools > Applications menu editor > navigate your way to the application and > right click > select properties > note the path*

Then put in terminal;

[PHP]wine "/example/not my example/dont be a turnip/yourprogram.exe"[/PHP]

---

### Post by taurus on 2007-02-09
I am a little confuse now.  /dev/hda1 is your / partitioon so what happens in /mnt since nothing shows on /mnt at all?  What is /mnt/hda1_XPHome anyway?

---

### Post by Shay Stephens on 2007-02-09
At least with Photoshop 7, you don't use the linux path, but instead the windows path when running a program.  So an example would be:
wine "C:\Program Files\Photostudio\PSTUDIO.EXE"

Don't forget the backslashes.

---

### Post by Irony on 2007-02-09
Its an ***example***, you are not meant to copy and paste it as I've written it:lolflag: 

For example;

This runs a program directly from my Windows partition mounted in /mnt;

[PHP]wine "/mnt/hda1_XPHome/Program Files/Photostudio/PSTUDIO.EXE"[/PHP]

Whereas this runs a program installed in the .wine folder;

[PHP]wine "/home/irony/.wine/drive_c/Program Files/AutoSketch/Sketch.exe"[/PHP]

***They are examples because the original poster didn't post the path to his program. The examples show the correct format of the terminal command.***

---

### Post by DougieFresh4U on 2007-03-18
For some reason, the wine in Feisty seems to have solved my problem with Game House games (.EXE files)

---

