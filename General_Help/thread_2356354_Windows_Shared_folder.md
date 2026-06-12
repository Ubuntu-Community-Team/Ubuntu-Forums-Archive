---
title: "Windows Shared folder"
date: 2017-03-22
forum: General Help
---

### Post by Docfxit on 2017-03-22
I created a folder in Ubuntu 16.04.2
I followed all the instructions to install and setup samba at:
[https://help.ubuntu.com/community/How%20to%20Create%20a%20Network%20Share%20Via%20Samba%20Via%20CLI%20(Command-line%20interface/Linux%20Terminal)%20-%20Uncomplicated,%20Simple%20and%20Brief%20Way](https://help.ubuntu.com/community/How%20to%20Create%20a%20Network%20Share%20Via%20Samba%20Via%20CLI%20(Command-line%20interface/Linux%20Terminal)%20-%20Uncomplicated,%20Simple%20and%20Brief%20Way)!

I followed all the instructions to share the folder I created.
When I try to see what is in the folder from Windows it asks me for a user/password.  I put it in and it asks me for the same user/password.
What could I have done wrong?

Thank you,

Docfxit

---

### Post by r.stiltskin on 2017-03-22
It sounds like you may have made a mistake in entering your username or your samba password.  You can run
```
sudo pdbedit -L
```that will list the samba users so you can verify that your username is listed there.  If it's not, you can run
```
sudo smbpasswd -a USERNAME
```to add yourself as a samba user.  It will then prompt you to enter a password for the new user.

Or if your USERNAME is already listed as a samba user you can run
```
sudo smbpasswd USERNAME
```(note, NO -a  in this case) and that will let you enter a new samba password for your already-existing samba user account so you'll be sure that it's set up correctly.

---

### Post by Docfxit on 2017-03-23
Thank you for the reply.

I tried the cmds.  With sudo pdbedit -L 
I get:
comand not found.

I'm guessing nothing was saved last time I booted Ubuntu.

I downloaded Ubuntu from:
[https://www.ubuntu.com/download/desktop](https://www.ubuntu.com/download/desktop)
and installed it to a USB bootable flash drive.
I selected TRY Ubuntu.    I did not select Install.
Does Try not save the changes I made?
I don't want to install it to the hard drive because I am trying to use Ubuntu to recover the OS on the hard drive.
Do I need to install Ubuntu for it to save the settings?
If I do need to install it, Can I install it to the same USB flash drive?

Thanks,

Docfxit

---

### Post by r.stiltskin on 2017-03-23
Ordinarily the live usb discards all changes when you shut it down, but you can create one with persistent storage.  If 4gb of storage is enough the instructions [here]("https://www.howtogeek.com/howto/14912/create-a-persistent-bootable-ubuntu-usb-flash-drive/") are pretty simple.

If you need more than that it's more involved.  The usb drive has to be repartitioned and formatted with an ext4 partition for persistent storage.  Instructions for that are [here]("https://help.ubuntu.com/community/mkusb/persistent").

---

### Post by Docfxit on 2017-03-25
Thank you for the reply...

I tried the links you provided and found it was to complicated for me.
I tried this link:
[http://www.instructables.com/id/Boot-and-Run-Ubuntu-from-a-Flash-Drive/step5/Install-Ubuntu-to-the-Flash-Drive/](http://www.instructables.com/id/Boot-and-Run-Ubuntu-from-a-Flash-Drive/step5/Install-Ubuntu-to-the-Flash-Drive/)
and I'm stuck on step #7 where it has this cmd:
root@ubuntu:~#"cp -rf casper disctree dists install pics pool preseed .disk isolinux/* md5sum.txt README.diskdefines ubuntu.ico casper/vmlinuz casper/initrd.gz /media/Ubuntu/"

I am getting this error with the cmd:
No such file or directory

If I run this cmd:
root@ubuntu:/media# ls
I get:
cdrom ubuntu

What am I doing wrong?

Thanks,
Docfxit

---

