---
title: "Unable to mount external harddrive"
date: 2007-04-18
forum: General Help
---

### Post by greenday121 on 2007-04-18
Hello.

I am currently running Ubuntu + KDE off my hard drive (not the live CD).  I am trying to mount an external hard drive but when I try to mount the drive I get the following error:

hal-storage-removable-mount-all-options refused uid 1000

I have searched on the internet for possible solutions and found one that suggested modifying something called an FSTAB file but I have no idea what that is because I am a bit of a linux noob.

Thanks for the help in advance!

**It should also be noted that the hard drive is NTFS**

---

### Post by JLB on 2007-04-18
fstab (file system table iirc) is located in your /etc   directory. It basically tells linux what to do with file systems found on your computer. The error indicates a permissions issue to me. 

Try editing the /etc/fstab file with the code below. Just add it to the end f the file and hit the enter key one time after that to insert a blank line as the last thing there. (don't ask why... it is a relic I kept from the slackware days :D )

Anyhow... to edit the file press the key combination ALT-F2 . This will bring up a command dialog box for you. in it type :```
kdesu kate /etc/fstab
```
You will be asked for your admin password. Enter it.

In the fstab file type/ copy& paster the following

```
/dev/sda1 /Windows/C ntfs ro,users,gid=users,umask=0002,nls=utf8 0 0
```

save it and plug in your USB drive again. This should get you read access to your NTFS drive.

---

### Post by crispy_420 on 2007-04-18
DId you install the related packages to mount/read/write to NTFS?

You may not have to edit the fstab as this is only temp connection. Just create a directory to use from, mount to. Say /home/"username"/external.

Then from terminal: mount /dev/sda1 /home/"username"/external

sda1 being your drive

---

### Post by gregconquest on 2007-04-19
Green Day,

I'm trying to make a guide for fstab now. While what I'm trying to make is not exactly for you, there are some links you can follow to get more info. Check out the links at the bottom of [http://ubuntuforums.org/showthread.php?p=2477107#post2477107]("http://ubuntuforums.org/showthread.php?p=2477107#post2477107")

HTH
Greg

---

