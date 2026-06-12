---
title: "unable to use fstab command"
date: 2006-08-12
forum: General Help
---

### Post by pigeonor on 2006-08-12
I am trying to give my drives write permission, but for some reason, the dev/fstab command wont work in terminal.... did i do something wrong?  can anyone please help me?  all i am trying to do is have the ability to write onto my own drive.

thank you:(

---

### Post by pigeonor on 2006-08-12
i am able to access fstab, but i cant save it so that i can make it writable.... i really need some help here....

---

### Post by Ramses de Norre on 2006-08-12
fstab is a file (/etc/fstab) which you need to edit with root priviliges, so you can use this command for example: ```
sudo gedit /etc/fstab
```
Type your own user password and don't worry if you don't see characters when you type, that's normal.
Then edit the file and save and close it.

---

### Post by pigeonor on 2006-08-12
awsome, you are great.... now i have another question:

this is the drive that i am trying to give write info:

/dev/sda1   *           1        8669    69633711   83  Linux

and

/dev/sdb5               2       38764   293048248+   b  W95 FAT32

what do i need to add to them to make them writable?

---

### Post by orb9220 on 2006-08-12
You don't make your linux partition writable it already is in your home directory. This is to protect you from going and doing things you are not supposed to do until you understand what and why you are changing things.

I have a home folder then I can go there to copy and install stuff to 

for fat32 mine is:

/dev/hdd1       /media/hdd1     vfat    defaults,utf8,umask=007,gid=46 0       0
Yours would be:

/dev/sdb5       /media/sdb5     vfat    defaults,utf8,umask=007,gid=46 0       0

---

