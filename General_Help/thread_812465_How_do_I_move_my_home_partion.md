---
title: "How do I move my home partion?"
date: 2008-05-29
forum: General Help
---

### Post by darthpenguin on 2008-05-29
Hi All

I have Ubuntu installed on one HDD and /home is on another HDD. The /home HDD is failing. Is it possible to move all files on my /home to a new SATA drive and make that my /home drive? what would be the procedure for that? I'm still new to Ubuntu so any terminal commands would help. thx

---

### Post by tamoneya on 2008-05-29
you should use the dd command to copy entire partitions.  Then you should go and enlarge the partition to take up all the space on the sata.```
dd if=/dev/sdb of=/dev/sdc
```Where /dev/sdb is your old drive and /dev/sdc is the new drive.

---

### Post by unutbu on 2008-05-29
With a slight bit of modification, you can use the [this guide]("http://www.psychocats.net/ubuntu/separatehome")

Skip the part about resizing your partition, skip to the part entitled "Using the new partition".

---

### Post by darthpenguin on 2008-05-30
Thx unutbu, 

From studying this guide it seems to me that I just have to;
1. hook up the new SATA
2. Boot from Live CD
3. Use gparted to format the SATA with ext3 (it is new so has no partition)
4. Mount drives sdb1 as /old and sdb2 as /new
5. Copy everything from /old to /new useing 
     "cd '/old'"
     "find . -depth -print0 | sudo cpio --null --sparse -pvd /new/"
6. Change fstab to mount SATA as /home by adding 
     "/dev/sdb2 /home ext3 nodev,nosuid 0 2"
7. Reboot

There are multiple user folders in my home directory so permission settings are different for every folder. I am also sharing each users home directory over SAMBA. Will this procedure  effect sharing or permissions? Have I missed any steps? Thx for your help.

---

### Post by Black Hawk on 2008-05-30
Yes permissions wil be f'ed up to fix: 
1. Boot your machine from hd
2. Get to a console (press ctrl + alt + f1 on login screen)
3. login (you might get an error because you can't acess your home dir)
4. Do sudo chown -R <user1> /home/<user1> 
Repet step four for all users

I don't know about samba. You might have to reactivate file sharing after moving the home dir.

---

### Post by unutbu on 2008-05-30
> **darthpenguin said:**
> 
4. Mount drives sdb1 as /old and **sdb2** as /new

I think the first partition of your new drive will be called /dev/sdc1, not sdb2.
> 
5. Copy everything from /old to /new useing
"cd '/old'"
"find . -depth -print0 | sudo cpio --null --sparse -pvd /new/"

The find command may not work properly if you run it as a normal user. Use
```
sudo find . -depth -print0 | sudo cpio --null --sparse -pvd /new/
```
instead.

> 
6. Change fstab to mount SATA as /home by adding 
     "/dev/sdb2 /home ext3 nodev,nosuid 0 2"

Again, /dev/sdb2 should probably be /dev/sdc1. When your /dev/sdb drive fails, or when you decide to remove it from your system, then your third drive, /dev/sdc, will become your second drive and then it will be named /dev/sdb. This would require you to edit your fstab. 

To avoid having to edit your fstab, you can use an fstab line like this:

```
UUID=XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX /home ext3  nodev,nosuid 0 2
```

UUID is a unique identifier for your partition. You can find out what the UUID should be by typing

```
blkid /dev/sdc1
```
(while your new drive is the third drive). Use the output from that command to replace the
XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX above.

> 
There are multiple user folders in my home directory so permission settings are different for every folder. I am also sharing each users home directory over SAMBA. Will this procedure  effect sharing or permissions? Have I missed any steps? Thx for your help.
I think cpio will preserve permissions, so there shouldn't be any problem. The method is also safe in the sense that you can test if it works before removing your old /home. As far as I can see, you haven't missed anything else. Good luck!

---

### Post by fsmithred on 2008-05-30
> **darthpenguin said:**
> Thx unutbu, 

From studying this guide it seems to me that I just have to;
1. hook up the new SATA
2. Boot from Live CD
3. Use gparted to format the SATA with ext3 (it is new so has no partition)
4. Mount drives sdb1 as /old and sdb2 as /new
5. Copy everything from /old to /new useing 
     "cd '/old'"
     "find . -depth -print0 | sudo cpio --null --sparse -pvd /new/"
6. Change fstab to mount SATA as /home by adding 
     "/dev/sdb2 /home ext3 nodev,nosuid 0 2"
7. Reboot

There are multiple user folders in my home directory so permission settings are different for every folder. I am also sharing each users home directory over SAMBA. Will this procedure  effect sharing or permissions? Have I missed any steps? Thx for your help.


I'd do #5 this way, and then not have to mess with fixing permissions:

sudo cp -r --preserve=all /old /new

(actually, I think that should be '/old/* /new'. I always get confused with that.)

---

### Post by unutbu on 2008-05-30
> **Black Hawk said:**
> Yes permissions wil be f'ed up to fix: 

I just did an experiment using
```

sudo find . -print0 | sudo cpio --null --sparse -pvd ../newhome/

```
Permissions and ownership attributes are preserved.

> 
I don't know about samba. You might have to reactivate file sharing after moving the home dir.
What we're doing is sort of like a stomach (data) transplant. The samba configuration files live in /etc (the brain?), which will remain untouched. When we transplant the stomach, the brain won't know the difference.

---

### Post by darthpenguin on 2008-05-31
Ok. I don't have enough power to run 3 HDDs and a CD so I figured I could do this without the Live CD. sudo find . -depth -print0 | sudo cpio --null --sparse -pvd /newhome copied everything over but did not preserve permissions Black Hawk's suggestion allowed me to access my home folder and log in to gnome. I then changed all permissions manualy (terminal) back to what they were. Samba was unafected and sharing still works as it did. Another question though, My SATA is 500GB I gave 1024MB to the swap and the rest to /home (ext3) but it only registers as 431GB, I know HDDs are never as big as they say but 68GB seems like a lot to go missing what is the deal?
Thx for all you help.

---

### Post by unutbu on 2008-05-31
darthpenguin, congratulations, and thanks for the report on how the process went. As for the missing 68G, please post

```
sudo fdisk -l
df

```

---

