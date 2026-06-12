---
title: "SD Card &amp;USB flash disk  problem - mount point not accessible"
date: 2012-10-21
forum: General Help
---

### Post by zhangweiwu on 2012-10-21
This problem is easy to reproduce.
1. insert a SD card. see it auto mounted.
2. Try to access it (from nautilus), get

"Could not display "/media/tristan/SD CARD
The location is not a folder."

The first thing weird is why not "/media/SD CARD"? But then I pass it as "must be a new policy, to make clear whose device is it, in case of multi-user logged in."

The next thing is wrong permission:
```

tristan@lyonesse:~$ ls -lh /media/
total 4.0K
drwxr-x---+ 3 root root 4.0K 10&#26376; 21 15:53 tristan

```

With such permission setting, of course I (tristan) could not access the mount point. It looks to me ubuntu intended to make me the owner of /media/tristan but failed to do so.

It could be because I changed my pid. What I did is to run 'vipw' and change my uid from 1000 to 1005 (also do chown on existing /home/tristan), a practise I keep doing for about 5 years ever time right after I install ubuntu. I use NFS, keeping my UID the same with the one on the server has benifits.

Is there a way to correct /media/<username> ownership or should I report this a bug?

Thanks!

---

### Post by varunendra on 2012-10-21
> **zhangweiwu said:**
> It could be because I changed my pid. What I did is to run 'vipw' and change my uid from 1000 to 1005..Try to unmount the partition then remount it with uid=1005,dmask=027,fmask=137 options. For example (assuming the card is sdb1, prefered mount-point is '/media/sdcard' and your gid is still 100):
```
sudo mount -t vfat -o uid=1005,gid=100,dmask=027,fmask=137 /dev/sdb1 /media/sdcard
```
For better details, please follow "[How to fstab]("http://ubuntuforums.org/showthread.php?t=283131")" tutorial by bodhi.zazen. It is about how to set fstab entries, but also gives some good info about mount points.

---

### Post by zhangweiwu on 2012-10-21
For sure manually umount and remount works, except it has to be done every time.


I am not sure if I am using pmount: it is just a freshly new Ubuntu installation, 12.10.

After further fiddling with the installation I found only users whoes UID is greater than 1000 have this problem. So it seems a bug to me. My workaround is to change my UID to 1000 and stay with it. It is going to create some problem with NFS, but perhaps this is the right time I give up NFS, fewer and fewer people are using it nowadays, and have many problems (e.g. PC doesn't shut down computer when NFS is mounted; the whole UI hangs when just a folder is offline; and many others).

---

### Post by varunendra on 2012-10-22
> **zhangweiwu said:**
> For sure manually umount and remount works, except it has to be done every time.
Hmm.. that is quite annoying..
I think an easier workaround would be to just create an fstab entry for it, or create a script for mounting it. Additionally, you can then add the path to this script to a file with 'NOPASSWD' option in /etc/sudoers.d directory so you don't have to type in your password everytime you run that script. Let me know if you are interested in doing so.

---

