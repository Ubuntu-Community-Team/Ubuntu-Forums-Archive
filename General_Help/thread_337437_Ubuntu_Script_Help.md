---
title: "Ubuntu Script Help"
date: 2007-01-13
forum: General Help
---

### Post by antivirus6613 on 2007-01-13
I use ubuntu live cd 5.10 for getting files off hard drives. I wanted to write a script that would enable me to do so. Basically I mount the hard drive with these commands

sudo mkdir /media/windows
sudo mount /dev/hda1 /media/windows/ -t ntfs -o nls=utf8,umask=0222

hda1 is mostly the one that i use

Then i just go to the desktop and click on windows ( drive ) and find the files i copy them to the desktop then my usb. Ubuntu automatically mounts my thumbdrive. 
Basically if anyone can write a script or help me write one that will enable me to mount ntfs drive and copy files to the desktop.  in windows it is copy XXXXXX(DIR) XXXXXX(DIR) and basically i want to copy some system files to the desktop then my thumbdrive. Mainly its the sam and system files windows\system32\config. 

I have no idea how to write a script or do anything with permissions. I am new to linux, familar with some commands like sudo mount and mkdir and stuff.

---

### Post by aysiu on 2007-01-13
So basically you want to write a script that will do those two commands?

A script is basically a text file, so create a text file: ```
gedit mountwindows.sh
``` This will open a text file called *mountwindows.sh*. Then make the first line ```
#!/bin/bash
``` I don't know enough about the technical aspects of scripts to tell you *exactly* what that line does, but it basically just makes your script a script instead of just a text file. Then, put in your two commands, so that the full text file will read: ```
#!/bin/bash
sudo mkdir /media/windows
sudo mount /dev/hda1 /media/windows/ -t ntfs -o nls=utf8,umask=0222
``` Finally, save and exit and then type ```
chmod +x mountwindows.sh
``` This will make the file executable. If you're using Gnome, you should be able to double-click that mountwindows.sh file, execute it in the terminal, and have Windows mounted to /media/windows.

---

### Post by antivirus6613 on 2007-01-13
Right now im in windows so i made a file that says. 

#!/bin/bash
sudo mkdir /media/filecopy
sudo mkdir /media/windows
sudo mount /dev/hda1 /media/windows/ -t ntfs -o nls=utf8,umask=0222
cp /media/windows/windows/system32/config/sam /media/filecopy
cp /media/windows/windows/system32/config/system /media/filecopy

It is a text file and i called it mountwindows


Then when i put it on my thumbdrive and boot into linux and double click on it (mountwindows.txt), it says run in terminal, run, display. So i click run in terminal and it doesnt do anything. Nothing is mounted and nothing shows up.

---

### Post by aysiu on 2007-01-13
You made it executable?

Also, I'm not sure if it makes a difference, but you may want to title it mountwindows.sh instead of mountwindows.txt.

In any case, what about if you run it from the terminal? What errors do you get? ```
cd /media/thumbdrive
./mountwindows.txt
``` I'm assuming your thumb drive is mounted at /media/thumbdrive. Substitute in the actual location.

---

### Post by antivirus6613 on 2007-01-13
Basically when i name it mountwindows.sh and click on it, it gives me same options as when i do with a text file. If i choose run from terminal, it pops up and then closes (very fast). if i try to open it in terminal it cannot locate the file or find it. If i drag and drop in terminal it doesnt work because the path has spaces and it needs _ to replace, if if i replace it cannot find it. 

can you make it and post on rapidshare or something. my file is exactly like i posted before 

#!/bin/bash
sudo mkdir /media/filecopy
sudo mkdir /media/windows
sudo mount /dev/hda1 /media/windows/ -t ntfs -o nls=utf8,umask=0222
cp /media/windows/windows/system32/config/sam /media/filecopy
cp /media/windows/windows/system32/config/system /media/filecopy

It should work but i dont know why it doesnt

---

### Post by aysiu on 2007-01-14
> **antivirus6613 said:**
> if i try to open it in terminal it cannot locate the file or find it. If i drag and drop in terminal it doesnt work because the path has spaces and it needs _ to replace, if if i replace it cannot find it. I don't know what you mean by this. You can use a path that has spaces. Just type part of the path and hit tab to complete it. If you don't understand that, copy mountwindows.sh to your desktop. Then do this: ```
cd ~/Desktop
./mountwindows.sh
``` and then post the output back here.

---

### Post by 0MG on 2007-01-14
you sneaky login cracker you. :p

---

### Post by antivirus6613 on 2007-01-15
OMG, you have uncoverd the secret :-p

sorry for the long time gap. its cuz i dont boot livecds often cuz my computer is being used.
Anyways Ok i got it to work sorta. I just changed the hdd path and moved the script to desktop like you said. now only 1 prob. the

cp /media/windows/windows/system32/config/sam /media/filecopy
cp /media/windows/windows/system32/config/system /media/filecopy

doesnt work. Even if i change /media/filecopy to ~/Desktop it wont let me.
Heres exactly what is says ( i just throw it in terminal and let it run)
cp: cannot create regular file "~/Desktop/sam": Permission Denied

BTW when i copy the file onto my thumbdrive it has a lock next to it.

---

### Post by majoridiot on 2007-01-16
two suggestions to try... in your mount statement, try changing umask=0222 to umask=002 or
try replacing it with uid=<yourusername> to give ownership to you when it is mounted.

---

### Post by antivirus6613 on 2007-01-16
so basically change

sudo mount /dev/hda1 /media/windows/ -t ntfs -o nls=utf8,umask=0222

to 

sudo mount /dev/hda1 /media/windows/ -t ntfs -o nls=utf8,umask=002 (what does umask do?)

or can i do

sudo mount /dev/hda1 /media/windows/ -t ntfs -o nls=utf8,umask=0222 uid-=ubuntu 

ubuntu is my uid cuz im booting live cd.

---

### Post by majoridiot on 2007-01-16
> **antivirus6613 said:**
> so basically change

sudo mount /dev/hda1 /media/windows/ -t ntfs -o nls=utf8,umask=0222

to 

sudo mount /dev/hda1 /media/windows/ -t ntfs -o nls=utf8,umask=002 (what does umask do?)


yes.  umask is essentiall a flavor of chmod, which sets permissions.  since it's an ntfs, you
should only need to set the perms for the entire partition and not all individual directories,
etc.  i recommended trying 002, as i've seen mention of different distros requiring different
umasks, due to differences in how bash is initialized.  002 seemed to be a popular alternate
for 0222 in this ntfs situation, so i thought it was worth trying.

> **antivirus6613 said:**
> 
or can i do

sudo mount /dev/hda1 /media/windows/ -t ntfs -o nls=utf8,umask=0222 uid-=ubuntu 

ubuntu is my uid cuz im booting live cd.

if ubuntu is your username, then yes.  if you mount it like that, it should give ownership of
the mounted device to your user.

---

