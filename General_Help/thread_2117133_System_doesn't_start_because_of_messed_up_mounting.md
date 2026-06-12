---
title: "System doesn't start because of messed up mounting"
date: 2013-02-17
forum: General Help
---

### Post by nemiux on 2013-02-17
Hello, I'm really not an expert on this, but I broke down my ubuntu system and even though it's nothing too serious (I think), I have no idea how to fix it.
What happened:
I installed some software(I can't remember the name at the moment, but I got it using the application installer(I forgot how it's called in the 12.04 i'm using, I only set it up today, but in previous versions its synaptic), and the program was responsible for drive mounting. However, I mounted 2 of the partitions (they are called 'much' and 'dideli', and analogically been mounted in /media/Much and /media/Dideli), and after I restarted the PC the ubuntu doesn't load. I manged to get the text error by clicking delete, and what was written there was something like:
Cannot mount file system /media/Dideli.
So I imagine it got set on auto-mount during the ubuntu startup, however, something went wrong. I think all I have to do is to disable this mounting, am I right? In any way, what should I do? Thanks.

---

### Post by ajgreeny on 2013-02-17
Presumably whatever it was you installed with the software-centre will have changed the /etc/fstab file and added lines for those two partitions.  Please try to remember what you installed as it may make life simpler.

Can you boot to a live CD or USB, manually mount the root partition of the installed ubuntu, and look for the /etc/fstab file in that.  Make sure you are not seeing the /etc/fstab of the live system.  Show us the content of that file.

The fstab in the root partition of your instalation which is causing the problem should have two lines relating to the partitions causing the error, so you can edit them out with command ```
gksudo gedit /media/*partition-name*/etc/fstab
```You will find the partition's name in the location bar of nautilus when you search for the file.

There is not really any need to install packages to mount, or automount partitions at boot, as it is very easy to do it all manually by backing up and then editing fstab, saving the file then checking all is OK with command ```
sudo mount -a
```

---

### Post by nemiux on 2013-02-18
> **ajgreeny said:**
> Presumably whatever it was you installed with the software-centre will have changed the /etc/fstab file and added lines for those two partitions.  Please try to remember what you installed as it may make life simpler.

Can you boot to a live CD or USB, manually mount the root partition of the installed ubuntu, and look for the /etc/fstab file in that.  Make sure you are not seeing the /etc/fstab of the live system.  Show us the content of that file.

The fstab in the root partition of your instalation which is causing the problem should have two lines relating to the partitions causing the error, so you can edit them out with command ```
gksudo gedit /media/*partition-name*/etc/fstab
```You will find the partition's name in the location bar of nautilus when you search for the file.

There is not really any need to install packages to mount, or automount partitions at boot, as it is very easy to do it all manually by backing up and then editing fstab, saving the file then checking all is OK with command ```
sudo mount -a
```
Thanks a lot! I had to work a little, creating the usb live pendrive and so on, but everything's back to normal. I just want to ask one thing.
I did as you said, now my fstab file looks like this:
```
proc                          /proc          proc  nodev,noexec,nosuid                0  0  
/host/ubuntu/disks/root.disk  /              ext4  loop,errors=remount-ro             0  1  
/host/ubuntu/disks/swap.disk  none           swap  loop,sw                            0  0  
/dev/sdb2                     /media/Dideli  ntfs  nls=iso8859-1,ro,noauto,umask=000  0  0  
/dev/sdb1                     /media/Much    ntfs  nls=iso8859-1,ro,noauto,umask=000  0  0  
```
As you can see, I'm mounting sdb1 and sdb2 drives, I used the same software(Storage Device Manager) to create the entries, cause I'm not sure what should be written there, I just removed the "start on boot" tick. But when I try the ```
sudo mount -a
``` nothing happens. I can mount them manually, but well, it's a pain to do it everytime. Any idea what's wrong?

---

### Post by ajgreeny on 2013-02-18
I do not know the **storage-device-manager** so have no idea what that does or how it does it.  I am also not sure for certain if the fstab you show is from your live USB or your hard disk installation. Is this a wubi installation? If so my answer may need some caution  as I do not know the differences between wubi and a proper partitioned  installation.

However the lines in fstab would normally be better in the format shown below using UUID which you can get from ```
sudo blkid -c /dev/null
```Device names can change if other partitions are ever edited or changed.  Make sure you have ntfs-3g installed and edit the lines to the format of
```
UUID=[COLOR=Red]uuid-from-blkid[/COLOR] /media/Dideli/    ntfs-3g        auto,user,rw 0 0
```Backup fstab and give it a try.

---

### Post by nemiux on 2013-02-18
> **ajgreeny said:**
> I do not know the **storage-device-manager** so have no idea what that does or how it does it.  I am also not sure for certain if the fstab you show is from your live USB or your hard disk installation. Is this a wubi installation? If so my answer may need some caution  as I do not know the differences between wubi and a proper partitioned  installation.

However the lines in fstab would normally be better in the format shown below using UUID which you can get from ```
sudo blkid -c /dev/null
```Device names can change if other partitions are ever edited or changed.  Make sure you have ntfs-3g installed and edit the lines to the format of
```
UUID=[COLOR=Red]uuid-from-blkid[/COLOR] /media/Dideli/    ntfs-3g        auto,user,rw 0 0
```Backup fstab and give it a try.
The Storage Device Manager can be found in Ubuntu Software Center by entering **pysdm** into the search.
Yes, it's the wubi installation, and I'm 100% sure that I'm looking at the wubi's fstab, not the live usb stick's.
Using the command I found out this:
```
/dev/sdb2: LABEL="Dideli" UUID="92E0BB2EE0BB1785" TYPE="ntfs" 

```
And by placing the information
```
UUID=92E0BB2EE0BB1785 /media/Dideli/    ntfs-3g        auto,user,rw 0 0
```
into the fstab and saving it, I instantly get this error:
```
Unable to mount Dideli
Unprivileged user can not mount NTFS block devices using the external FUSE
library. Either mount the volume as root, or rebuild NTFS-3G with integrated
FUSE support and make it setuid root. Please see more information at
http://tuxera.com/community/ntfs-3g-faq/#unprivileged

```

---

### Post by ajgreeny on 2013-02-18
But fstab **_is_** run as root when the system boots, not as a user, so I don't understand the error you see.  Did you make the edit and then try **"mount -a**" without using sudo as that would not be possible.

OK, Now I'm out of my depth, and I don't have any windows ntfs partitions to try this on, nor do I know wubi, as I said before.

I will therefore have to back out of this and let you wait for any other answers, unless my comment above is your problem now, rather than the fstab being wrongly edited.

---

