---
title: "Strange new mounting system using uuid"
date: 2007-02-06
forum: General Help
---

### Post by kaminix on 2007-02-06
Hi!
I've just copied all my data to a USB drive in order to reformat my previous FAT disk to ext3. I've already done that. Now I want to mount it.

But when I mount it I see something absolutely terrifying. The format of fstab is changed! It uses something called UUID now, and I have NO idea how to use that.

How do I mount my ext3 hda5 to /media/hda5 using this uuid?

---

### Post by yabbadabbadont on 2007-02-06
Just put an entry in there like you used to.  It should still work.

---

### Post by bodhi.zazen on 2007-02-06
yabbadabbadont' s advice should solve your problem.

However, if you want to use UUID, 

First plug in the usb device.

Then in a terminal type:```
blkid
```

That command will show you the device uuid

Then in fstab:

```
UUID=#### /media/hda5 ....
```

where #### = the partition uuid

8)

---

### Post by kaminix on 2007-02-06
What's good about the UUID?

---

### Post by bodhi.zazen on 2007-02-06
> **kaminix said:**
> What's good about the UUID?

[size=4]**[color=red]Whaaat ?**[/color] :shock: Isn't it obvious ? [/size]

Just look at that geek factor, I mean where else can you find a fstab with UUID=f81d4fae-7dec-11d0-a765-00a0c91e6bf6 8)

Really, all the geeks have em now, where have you been :p

:lolflag:

Some people feel it is more secure ...

IMO UUID is helpful for removable devices as the location /dev/sdxy may change depending on how and when you attach the device making it difficult to put an entry in fstab ...

This is not so critical as now USB devices are auto mounted ...

Also you can just as easily use LABEL=<name> ...

Obviously this is not such an advantage with a fixed HD as in your case.

I guess I was answering your question, providing information for your interest as the "problem" was solved by yabbadabbadont

---

### Post by kaminix on 2007-02-09
kaminix@kaminix:~$ blkid /dev/sda1
/dev/sda1: UUID="f51ccb00-a2ca-4b51-892a-af62b6bd56db" SEC_TYPE="ext2" TYPE="ext3"
kaminix@kaminix:~$ sudo vim /etc/fstab
(adding:
# /dev/sda1
UUID=f51ccb00-a2ca-4b51-892a-af62b6bd56db /media/usbdisk        ext3    defaults        0       1)

kaminix@kaminix:~$ sudo umount /dev/sda1
kaminix@kaminix:~$ sudo mount -a
mount: special device /dev/disk/by-uuid/f51ccb00-a2ca-4b51-892a-af62b6bd56db does not exist


Why isn't it working? :(

---

### Post by bodhi.zazen on 2007-02-09
Just a guess ....

With usb devices, sometimes after you unmount them you need to physically remove the device and then plug it back in before you re mount it 

One user reported UUID=XXXX would not work, but /dev/disk/by-uuid/XXXX did

Where XXXX = your uuid ;)

Otherwise it looks good ;)

---

### Post by kaminix on 2007-02-09
> **bodhi.zazen said:**
> Just a guess ....

With usb devices, sometimes after you unmount them you need to physically remove the device and then plug it back in before you re mount it 

One user reported UUID=XXXX would not work, but /dev/disk/by-uuid/XXXX did

Where XXXX = your uuid ;)

Otherwise it looks good ;)Still get the same mount: special device /dev/disk/by-uuid/UUID=f51ccb00-a2ca-4b51-892a-af62b6bd56db does not exist


Speaking of mounting disks, how do I make it writable?

---

### Post by bodhi.zazen on 2007-02-09
> **kaminix said:**
> Still get the same mount: special device /dev/disk/by-uuid/UUID=f51ccb00-a2ca-4b51-892a-af62b6bd56db does not exist

No UUID

Like this:> /dev/disk/by-uuid/f51ccb00-a2ca-4b51-892a-af62b6b

> Speaking of mounting disks, how do I make it writable?

First mount the device

Then in a terminal :

```
sudo chown username:users /media/usbdisk
sudo chmod 770 /media/usbdisk
```

---

### Post by kaminix on 2007-02-09
> **bodhi.zazen said:**
> No UUID

Like this:



First mount the device

Then in a terminal :

```
sudo chown username:users /media/usbdisk
sudo chmod 770 /media/usbdisk
```
mount: special device /dev/disk/by-uuid/f51ccb00-a2ca-4b51-892a-af62b6b does not exist
:(

---

### Post by bodhi.zazen on 2007-02-09
Well I see nothing wrong with your syntax.

Lets start at the beginning

First what version of Ubuntu are you currently running ?

Copy and paste the following information to reduce errors/typos ...

1. Current line in fstab

2. output of :```
ls /dev/disk/by-uuid -l
```

3. The exact command you are using to mount ...

Here is what I am getting on my box :

> [~]$ sudo umount /mnt/sda1/
[~]$ ls /mnt/sda1/
[~]$ 
[~]$ ls /dev/disk/by-uuid/ -l
total 0
lrwxrwxrwx 1 root root 10 2007-02-08 18:31 344A-10F8 -> ../../hda1
lrwxrwxrwx 1 root root 10 2007-02-08 18:32 8093-8F05 -> ../../sda1
[~]$ 
[~]$ sudo mount /dev/disk/by-uuid/8093-8F05 /mnt/sda1/
[~]$ 
[~]$ ls /mnt/sda1/
avatar204791_1.gif        HowTo.bashrc ... 

And this line in fstab works with sudo mount -a :

> /dev/disk/by-uuid/8093-8F05 /mnt/sda1 vfat  defaults,auto 0 2

---

### Post by Magnes on 2007-02-09
I find UUID VERY useful. I recently changed my slave disk to master disk, so hda changed to hdb. Because of the UUID thing the only change I needed to do was editing grub menu.lst.

---

### Post by kaminix on 2007-02-09
> **bodhi.zazen said:**
> Well I see nothing wrong with your syntax.

Lets start at the beginning

First what version of Ubuntu are you currently running ?

Copy and paste the following information to reduce errors/typos ...

1. Current line in fstab

2. output of :```
ls /dev/disk/by-uuid -l
```

3. The exact command you are using to mount ...

Here is what I am getting on my box :



And this line in fstab works with sudo mount -a :
Okay, now I got a different UUID, and it worked. Thanks.

But...
kaminix@kaminix:~$ sudo chown -Rv kaminix:kaminix /media/usbdisk/
chown: changing ownership of `/media/usbdisk/lost+found': Read-only file system
failed to change ownership of `/media/usbdisk/lost+found' to kaminix:kaminix
chown: changing ownership of `/media/usbdisk/': Read-only file system
failed to change ownership of `/media/usbdisk/' to kaminix:kaminix


current fstab line:
/dev/disk/by-uuid/45C7-A9FB     /media/usbdisk  ext3    defaults,auto   0       2

---

### Post by bodhi.zazen on 2007-02-09
Hi kaminix

I do not have much free time in the next few days, and I am late now, sorry ...

You could try chown without the -Rv flags, although I suspect it will fail ...

Each time you format a partition it will be assigned a new uuid ;)

It sounds as if the device is mounted ro which would indicte errors in the file system.

Unmount the device, the run 

sudo fsck /dev/sda1

If you get errors, 

```
sudo fsck -y /dev/sda1
```

man fsck : [http://www.die.net/doc/linux/man/man8/fsck.8.html](http://www.die.net/doc/linux/man/man8/fsck.8.html)

HTH

---

