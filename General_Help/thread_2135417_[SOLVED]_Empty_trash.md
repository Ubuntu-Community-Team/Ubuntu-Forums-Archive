---
title: "[SOLVED] Empty trash"
date: 2013-04-14
forum: General Help
---

### Post by Olle/Nicki on 2013-04-14
I can't empty the trashcan. Tryed several ideas in the forum and on the webb without succes.
Please help me.

---

### Post by ibjsb4 on 2013-04-14
In terminal:

```
rm -r ~/.local/share/Trash/*
```

more here

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=empty+trash+in+terminal&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=empty+trash+in+terminal&sa=Search&cof=FORID:9)

---

### Post by Olle/Nicki on 2013-04-14
> **ibjsb4 said:**
> In terminal:

```
rm -r ~/.local/share/Trash/*
```

more here

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=empty+trash+in+terminal&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=empty+trash+in+terminal&sa=Search&cof=FORID:9)

Sorry, but it didn't work.

```
rm: can not remove "/home/olle/.local/share/Trash/*" The file or the catalog dosn't excist
```
(Translated from Swedish)

---

### Post by ibjsb4 on 2013-04-14
Are you still running 9.04?

```
rm -rf ~/.Trash/*
```

---

### Post by Olle/Nicki on 2013-04-14
No, 12.04 32 bit

---

### Post by ibjsb4 on 2013-04-14
The folder exist right?
/home/olle/.local/share/Trash

---

### Post by ibjsb4 on 2013-04-14
```
gksudo nautilus
```

Navigate to the files and delete both under .Trash

---

### Post by Olle/Nicki on 2013-04-14
> **ibjsb4 said:**
> The folder exist right?
/home/olle/.local/share/Trash

No, there is no folder "Trash" there. But it is really on the desktop and I can open it.
This is really odd.

Edit--------

I found the Trash folder now and it contain three folders: expunged + files +info. All of them are empty.

---

### Post by ibjsb4 on 2013-04-14
Ok, try this.  Do a search on Trash.

```
sudo find / -type d -name *Trash*
```

---

### Post by Olle/Nicki on 2013-04-14
Additional information:

I have a dualboot with Windows 7. I have deleted some files (750 windows files ) when running Ubuntu. But could not empty the trash. Earlier when I had Mandriva and Windows XP, this was never a problem.

---

### Post by Olle/Nicki on 2013-04-14
> **ibjsb4 said:**
> Ok, try this.  Do a search on Trash.

```
sudo find / -type d -name *Trash*
```

```
olle@olle-s5530sc:~$ sudo find / -type d -name *Trash*
[sudo] password for olle: 
/media/sda2/.Trash-1000
/home/olle/.local/share/Trash
olle@olle-s5530sc:~$ 

```

---

### Post by ibjsb4 on 2013-04-14
Open Nautilus (gksudo nautilus) and delete both trash folders.

/media/sda2/.Trash-1000 
/home/olle/.local/share/Trash

They will regenerate when needed.

Edit: On a side note there is a delete command to bypass trash in nautilus.

[ATTACH=CONFIG]241323[/ATTACH]

---

### Post by Olle/Nicki on 2013-04-14
Sorry, I manage to delete the folders but my 750 files are still in the trashcan.

---

### Post by ibjsb4 on 2013-04-14
reboot

---

### Post by Olle/Nicki on 2013-04-14
> **ibjsb4 said:**
> reboot

I have done it. But no success.

---

### Post by ibjsb4 on 2013-04-14
Those trash files should of been deleted.  I just want to be sure by adding a "forced delete" to the original command.

```
sudo rm -rf /media/sda2/.Trash-1000

sudo rm -rf /home/olle/.local/share/Trash
```

Im running low on ideas  :(

---

### Post by Olle/Nicki on 2013-04-14
> **ibjsb4 said:**
> Those trash files should of been deleted.  I just want to be sure by adding a "forced delete" to the original command.

```
sudo rm -rf /media/sda2/.Trash-1000

sudo rm -rf /home/olle/.local/share/Trash
```

Im running low on ideas  :(

Tried your first line and got the answer: The filesystem is only readable.
How does it come?

---

### Post by ibjsb4 on 2013-04-14
Read only file system

[http://ubuntuforums.org/showthread.php?t=1907513](http://ubuntuforums.org/showthread.php?t=1907513)

Are you running the 3.5 kernel

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1063354](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1063354)

---

### Post by Olle/Nicki on 2013-04-14
> **ibjsb4 said:**
> .......Are you running the 3.5 kernel

No, I have 3.2.0-40

---

### Post by Olle/Nicki on 2013-04-15
I finally fixed the problem. The files in .Trash-1000 was locked. Not even root could delete them. But when I rebooted in to Windows, I saw the folder there and managed to delete the whole folder.

This was something new for me, but there is a conclusion: Never delete files in an other system, only in the system that you are logged in to.

---

### Post by ibjsb4 on 2013-04-15
NTFS?  Really not sure whats with that, but glad you got it solved.  See ya :)

---

