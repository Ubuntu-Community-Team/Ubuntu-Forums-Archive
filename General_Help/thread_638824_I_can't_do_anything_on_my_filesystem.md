---
title: "I can't do anything on my filesystem"
date: 2007-12-12
forum: General Help
---

### Post by StitchJAcket on 2007-12-12
I have encountered this issue before but was unable to resolve it. Please someone help me here.

I just installed Ubunty Fiesty and updated to Gutsy. Here's the issue. For my filesystem the owner is set to unknown. Now the way i have this hard drive partitioned is there is a /boot partition, a root partition and a /home partition. However the root partition holds all my links to home and boot etc. Here's the problem i installed limewire and am unable to set the directory to save documents to because in order to set it i have to go through root which the permissions are set to read only. I can't change the permissions because i am not the owner the owner is unknown. Please help me i need to get this working.

---

### Post by ajgreeny on 2007-12-12
You should be able to change ownership of the files or folders with **chown.**  Have a look at ```
man chown
``` in terminal and it may help you.  Also you could try ```
gksudo nautilus
``` which will open nautilus as root and may allow you to change owner of the folders etc graphically, but be careful, nautilus as root can be dangerous if you are careless and accidentally remove something.

---

### Post by r-mo on 2007-12-12
It is very dangerous and highly unrecommended to change the permissions of the root file system.  Limewire shouldn't be asking to write there! Just set it to save in your home folder.

If you want to use space on your root partition (say if you're running out of space on /home) create a directory and give yourself write permissions to that only., but please don't start changing permissions on system folders.

```

sudo mkdir /storage
sudo chown user:user storage

```

where  user is your user name

---

### Post by r-mo on 2007-12-12
Having just tried limewire (have to say I prefer nicotine) I just want to make sure you know where you are in the filesystem as when you browse for a shared folder the starting directory is /usr/share/limewire which has a directory called root in it and could be leading to some confusion.

---

