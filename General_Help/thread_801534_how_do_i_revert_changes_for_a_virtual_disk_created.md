---
title: "how do i revert changes for a virtual disk created?"
date: 2008-05-20
forum: General Help
---

### Post by Link^^ on 2008-05-20
Hello everybody!

I hope I posted in the right place.

I am runing ubuntu 8.04 on ntfs system disk. When I installed it, I selected 4 gb of space for the ubuntu install space.
Short after that I have run out of disk space. So I have followed this instructions [https://wiki.ubuntu.com/WubiGuide#head-fda2b476cbe51b911313b25d55e6bf70c6134b2b](https://wiki.ubuntu.com/WubiGuide#head-fda2b476cbe51b911313b25d55e6bf70c6134b2b) to create more space.

the command that I gave was:

```
sudo sh wubi-add-virtual-disk /home 3000
```

this moved my /home folder to a virtual disk of 3 gb. My mistake is that I actually wanted to move the /usr folder and not /home.

the website says to revert changes > To undo the changes remove /home, copy rename /home.backup to /home and remove the /home line in /etc/fstab.

I was not able to remove the folder /home at all. Can somebody show me how to go through this thing to undo what i have done ?

I still have the /home.backup folder.

---

### Post by ago on 2008-05-20
You can have both /usr as well as /home in dedicated partitions 
And now you can move the full installation to a dedicated partition
Anyway the commands are:

sudo mv /home /home.old
sudo mv /home.backup /home
sudo sed -i "s:.* /home .*::" /etc/fstab
sudo reboot

---

### Post by Link^^ on 2008-05-20
I just tried that, and now it does not let me to log in with my user. It says that it cannot access it.

---

### Post by ago on 2008-05-21
Boot in rescue mode and check that your user folder is in /home and that it is owned by your username. You can use "ls -al" to list the directory content.

---

### Post by Link^^ on 2008-05-21
my user folder is there. I dont know what to look for to see if it's owned by me or not.

this is what is prompted to me when I try a normal log in:
> Your home directory is listed as: '/home/silviu' but it does not appear to exist. Do you want to log in with the /(root) directory as your home directory? It is unlikely anything will work unless you use failsafe session.
when I click ok, his is what is prompted:
> User's $HOME/.dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions. User's $home directory must be owned by user and not writable by others.
any light that you could shed over this problem ?

---

### Post by ago on 2008-05-21
you use "ls -al" to check permissions/ownership

---

### Post by Link^^ on 2008-05-21
I have tried ls -al, but I don't know what is that I have to look for when it lists me the folders.

this is what I get by tipping ls -al in /home
```
drwxr-xr-x  2  root  root  4096  May  20  17:10
drwxrwxrwx  24  silviu  silviu  4096  May  20  21:32
```

---

### Post by ago on 2008-05-21
I assume your username is also silviu (whoami). What is in /home/silviu?

---

### Post by Link^^ on 2008-05-24
other then list the content of home with ls -al, I can't get in /home/silviu. I tried cd silviu from /home

---

### Post by ago on 2008-05-25
Can you get in with sudo?

---

### Post by Link^^ on 2008-05-28
no, it would not let me in with sudo.

---

### Post by ago on 2008-05-28
comment out the line containing "/home" (if any) in /etc/fstab
mv /home/silviu mv /home/silviu.old
reboot

a new home folder should be created on the fly.
try now to look into

/home.old
/home/silviu.old

and to mount the virtual disk

sudo mount -o loop /host/ubuntu/disks/home.disk /mnt
ls /mnt

some of them should have your old files that you can copy onto your new home

---

