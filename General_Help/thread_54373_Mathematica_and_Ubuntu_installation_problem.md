---
title: "Mathematica and Ubuntu installation problem"
date: 2005-08-04
forum: General Help
---

### Post by kes on 2005-08-04
I have a installation disk of Mathematica 5.0. It contains usual setup.exe for Windows and Mathinstaller srcipt for Unix...
Well, theoretically that should be enough,  but when I'm  asking to run Mathinstaller  script nothing happens... 
fine, I tryed to install it using setup.exe and WinE (HQ), and I've received the following message: "Cannot install the installation programme"... so that's how it ends... :???: 

can anyone tell me how can I install mathematica on my notebook?
thanks

---

### Post by bored2k on 2005-08-04
1. You don't want to run Mathematica through Wine.
2. I inserted the disc, went to the right folder and just ran "MathInstaller"

Here's the whole process.
After I did```
foo@bar:~$ cd /media/cdrom0/Unix/Installer
foo@bar:/media/cdrom0/Unix/Installer$ ls
[COLOR=Green]**MathInstaller**[/COLOR]  [COLOR=Navy]**TextResources**[/COLOR]
foo@bar:/media/cdrom0/Unix/Installer$ bash MathInstaller

```I got this:
```

--------------------------------------------------------------------------------                          Mathematica 5.0 Installer
--------------------------------------------------------------------------------
Copyright (c) 2003  Wolfram Research, Inc. All rights reserved.

WARNING: Mathematica is protected by copyright law and international
treaties. Unauthorized reproduction or distribution may result in severe
civil and criminal penalties and will be prosecuted to the maximum extent
possible under law.

The following installation methods are available:

  (1) Full
  (2) Minimal

Type your selection, or press ENTER to select (1):
>

```

---

### Post by eerke on 2007-04-26
In Feisty 7.04 I got this result:

root@Feynman:/media/cdrom0/Unix/Installer# ./MathInstaller
-bash: ./MathInstaller: /bin/sh: bad interpreter: Permission denied

What is going wrong? (It worked in Dapper)

Kind regards

Eerke

Sorry, I forgot the bash command

---

### Post by irisevelyn on 2007-05-07
Try to copy the Unix directory in which the MathInstaller is to wherever you want to install it to and then run it from there.
Worked just fine on my Computer right now.
Good luck

---

### Post by jsym on 2007-06-04
I had a similar problem installing Maple11.

Overcoming it required two steps:

1. Copying the script and directory containing all the installation files to my Desktop.

2. Right-clicking on the script, selecting the **Permissions tab** and then checking the **"allow executing file as program"** box.

---

### Post by bjornTFN on 2007-08-09
Hi, I had a similar problem when installing Matlab R2007a on Ubuntu 7.04

The cause is (I think) that by default your cdrom is mounted in such a way as to disable running files on it as programs (even if you mount it as root).

To overcome this, unmout your cdrom drive. Then remount it but specify 
-o exec
on the mount command. This will enable running programs from the disk. Alternatively, use the method above (just found that remounting was quicker :-) )

---

### Post by jsym on 2007-08-09
Good call, bjornTFN. :)

Let's take it one step further though and set the cdrom to automatically mount with the **exec** option every time.
[LIST=1]
[*]Open fstab for editing: ```
# sudo gedit /etc/fstab
```
[*]Add exec to the list of options associated with the cdrom.  For example the cdrom line will say something like ```
/dev/cdrom        /media/cdrom0   udf,iso9660 user,noauto     0       0
```  Whatever it says, insert a comma followed by "exec" immediately at the end of the options list (the third group of text), like so ```
/dev/cdrom        /media/cdrom0   udf,iso9660 user,noauto**,exec**     0       0
``` 
[*]Save the file and you should be good to go every time you mount the cdrom and need to run a binary from it.
[/LIST]

---

