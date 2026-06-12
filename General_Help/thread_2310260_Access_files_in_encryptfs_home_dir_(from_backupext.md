---
title: "Access files in encryptfs /home dir (from backup/external HDD)"
date: 2016-01-17
forum: General Help
---

### Post by user102942 on 2016-01-17
I had a laptop with Kubuntu 14.04 64-bit. It had a hardware issue, so I removed the hard disk and connected it as an _external HDD_ to my old Lubuntu 14.04 32-bit laptop.

The problem is, I can't access my (Kubuntu) /home partition from the replacement (Lubuntu) laptop. This is the readme file:
```
THIS DIRECTORY HAS BEEN UNMOUNTED TO PROTECT YOUR DATA.

From the graphical desktop, click on:
 "Access Your Private Data"

or

From the command line, run:
 ecryptfs-mount-private
```

Clicking on the "Access-Your-Private-Data.desktop" does nothing. Entering the ecryptfs-mount-private command in a terminal also does nothing. Possibly because I'm using a different laptop (Lubuntu 32 bit) that doesn't have my usual account.

I know the login username and password to my Kubuntu account but don't remember receiving or entering a private key or passphrase.

The other system files (/etc, /root, /bin, ...) can be accessed. Only /home is on an encryptfs partition.

What can I do to access the files in /home from my replacement laptop?


Edit: If useful, these files are in .ecryptfs:
```
auto-mount auto-umount Private.mnt Private.sig wrapped-passphrase
```
I made a Lubuntu account with the same username and password as the Kubuntu account, ran ecryptfs-mount-private (with and without sudo) but it said:
```
ERROR: Encrypted private directory is not setup properly
```

---

### Post by SagaciousKJB on 2016-01-20
Did you follow this guide?
[http://blog.dustinkirkland.com/2011/04/introducing-ecryptfs-recover-private.html](http://blog.dustinkirkland.com/2011/04/introducing-ecryptfs-recover-private.html)
[http://askubuntu.com/questions/93975/recovering-ecryptfs-partition-with-ecryptfs-recover-private-not-working](http://askubuntu.com/questions/93975/recovering-ecryptfs-partition-with-ecryptfs-recover-private-not-working)

---

### Post by sean121 on 2016-06-23
did you ever find a solution to this? i am experiencing a similar issue with an older hdd i found while packing that i would like to recover the data off of

this is as far as i got with it
 i have an older hdd with a corrupted  version of 12.04 on it. the home directory is encrypted so when i have  it plugged in as an external, i cannot access the files to copy them to a  different drive so i can load a new distro onto the corrupted drive. i  am trying to acess it through and external mount to usb on a laptop  running 16.04

```
sean@sean-Presario-CQ56-Notebook-PC:~$ sudo ecryptfs-recover-private
[sudo] password for sean: 
INFO: Searching for encrypted private directories (this might take a while)...
find: ‘/run/user/1000/gvfs’: Permission denied
mount | grep ^/
sean@sean-Presario-CQ56-Notebook-PC:~$ mount | grep ^/
/dev/sda1 on / type ext4 (rw,relatime,errors=remount-ro,data=ordered)
/dev/sdb1 on /media/sean/d2883916-8b62-4eea-bd2d-5ef74b122d54 type ext4 (rw,nosuid,nodev,relatime,data=ordered,uhelper=udisks2)
sean@sean-Presario-CQ56-Notebook-PC:~$ ls -l /home
total 4
drwxr-xr-x 39 sean sean 4096 Jun 23 12:56 sean


```

i get about that far and then i get lost. can you point me a little more directly at the next step please?
Thanks in advance

---

### Post by QDR06VV9 on 2016-06-23
> **sean121 said:**
> this is as far as i got with it
 i have an older hdd with a corrupted  version of 12.04 on it. the home directory is encrypted so when i have  it plugged in as an external, i cannot access the files to copy them to a  different drive so i can load a new distro onto the corrupted drive. i  am trying to acess it through and external mount to usb on a laptop  running 16.04

```
sean@sean-Presario-CQ56-Notebook-PC:~$ sudo ecryptfs-recover-private
[sudo] password for sean: 
INFO: Searching for encrypted private directories (this might take a while)...
find: ‘/run/user/1000/gvfs’: Permission denied
mount | grep ^/
sean@sean-Presario-CQ56-Notebook-PC:~$ mount | grep ^/
/dev/sda1 on / type ext4 (rw,relatime,errors=remount-ro,data=ordered)
/dev/sdb1 on /media/sean/d2883916-8b62-4eea-bd2d-5ef74b122d54 type ext4 (rw,nosuid,nodev,relatime,data=ordered,uhelper=udisks2)
sean@sean-Presario-CQ56-Notebook-PC:~$ ls -l /home
total 4
drwxr-xr-x 39 sean sean 4096 Jun 23 12:56 sean
```


i get about that far and then i get lost. can you point me a little more directly at the next step please?
Thanks in advance
@sean121 Please do not post multiple help requests I have your own thread located here:[http://ubuntuforums.org/showthread.php?t=2328720](http://ubuntuforums.org/showthread.php?t=2328720)
Dilutes the community's efforts in helping you

---

