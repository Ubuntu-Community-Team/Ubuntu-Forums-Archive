---
title: "in gutsy, apt-file is looking for a cdrom?"
date: 2007-10-22
forum: General Help
---

### Post by loell on 2007-10-22
odd, :( , I am hunting a prticular file so I installed **apt-file** , but when i tried doing
```
sudo apt-file update
```

it prompted 

```
sudo apt-file update
[sudo] password for usernamel:
Put CDROM labeled [Ubuntu_7.10__Gutsy_Gibbon__-_Release_i386_(20071016)] in the cdrom device
read: 1: arg count
mount: block device /dev/scd0 is write-protected, mounting read-only
mount: /dev/scd0 already mounted or /media/cdrom0 busy
mount: according to mtab, /dev/scd0 is already mounted on /media/cdrom0
cp: cannot stat `/cdrom/dists/gutsy/Contents-i386.gz': No such file or directory

```

 seems it is looking for the gutsy installer in the cdrom, but I've already inserted  it, but can't find **/cdrom/dists/gutsy/Contents-i386.gz**? anyone know what that file is?

similarly, when I installed**  build-essential** it looked for the installer, though it finds the necessary package and **installed it from the CD**, its baffling that it did not installed from the repository directly.

---

### Post by bionnaki on 2007-10-22
comment out the cd rom entry in /etc/apt/sources.list

sudo nano /etc/apt/sources.list
and then
sudo apt-get update

---

### Post by loell on 2007-10-22
thanks, now it just gave me the idea to go to **system menu** --> ** software sources**--> unchek the cdrom source :)



but another stoppper is

when i do **sudo apt-file update** 

its just freezes :( , anyone out there who has experience in using **apt-file**?

---

### Post by briwood on 2007-11-21
> when i do sudo apt-file update

its just freezes

I had the same reaction, but actually, it's working.  It is updating and it doesn't give you output.  I have a standard dsl connection.  I let mine sit for about 4 min and it finally returned another shell prompt. At that point I could do 

```
apt-file search <filename>
```

This also may pause for several seconds before you see output.

---

