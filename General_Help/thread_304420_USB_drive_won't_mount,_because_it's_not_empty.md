---
title: "USB drive won't mount, because it's not empty?"
date: 2006-11-21
forum: General Help
---

### Post by Mimsy on 2006-11-21
Up until today, my small mobile hard drive has auto-mounted just fine whenever I plugged it into the USB port. Today, however, it refuses. The drive shows up in Nautilus, correctly named, but when I try to open it I get this error message:

> error: directory /media/escape pod is not empty
error: could not execute pmount


"Not empty" has never been a problem before. 

I'm going on a road-trip 6:00 am tomorrow, and I want to leave a backup on the USB drive, in my house, so if something happens to the laptop on the road, I still have my data. This refusal to mount the USB driveis therefor, for obvious reasons, a big problem for me.

Help, please?

/Mimsy

---

### Post by taurus on 2006-11-21
Need the output of these three commands from a temrinal!

```
sudo fdisk -l
cat /etc/fstab
df -h
```

---

### Post by Mimsy on 2006-11-21
Certainly. Here they are, one after the other:

> mimsy@Hawk:~$ sudo fdisk -l
Password:

Disk /dev/hda: 30.0 GB, 30005821440 bytes
255 heads, 63 sectors/track, 3648 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3555    28555506   83  Linux
/dev/hda2            3556        3648      747022+   5  Extended
/dev/hda5            3556        3648      746991   82  Linux swap / Solaris

Disk /dev/sda: 5000 MB, 5000970240 bytes
255 heads, 63 sectors/track, 608 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         607     4875696    6  FAT16


> mimsy@Hawk:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0


> 
mimsy@Hawk:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1              27G  3.6G   22G  14% /
varrun                126M   96K  125M   1% /var/run
varlock               126M  4.0K  126M   1% /var/lock
udev                  126M  104K  125M   1% /dev
devshm                126M     0  126M   0% /dev/shm
lrm                   126M   19M  107M  15% /lib/modules/2.6.15-27-386/volatile


As far as I can tell, the mobile drive is nowhere to be found. Very odd.

Thanks for the quick reply!

/Mimsy

---

### Post by Mimsy on 2006-11-21
Okay, stupid question:
Should I install the 12 updates the update-manager just told me about, and see if they do anything to solve my problem?

/Mimsy

---

### Post by taurus on 2006-11-21
Just one more command!  ;) 

```
ls -la /media
```
Go ahead and update your machine.  Wouldn't hurt...

---

### Post by Mimsy on 2006-11-21
> mimsy@Hawk:~$ ls -la /media
total 164980
drwxr-xr-x  4 root root      4096 2006-11-19 14:45 .
drwxr-xr-x 21 root root      4096 2006-10-28 01:03 ..
lrwxrwxrwx  1 root root         6 2006-10-28 00:27 cdrom -> cdrom0
drwxr-xr-x  2 root root      4096 2006-10-28 00:27 cdrom0
-rw-------  1 root root 168747040 2006-11-18 15:46 ESCAPE
drwx------  3 root root      4096 2006-11-18 15:45 ESCAPE POD

There it is! The Escape Pod is finally showing up! That makes me happy. :) I wonder why there is a cdrom0 in there though. That drive isn't connected right now...

Updating, updating... with any luck, the new HAL update will take care of the hibernate problems I've had recently.

/Mimsy

---

### Post by taurus on 2006-11-21
Actually, cdrom0 is your mount point which means when you insert a CD into the drive, it will be mounted to /media/cdrom0.  Now, see if you can mount it with this command...

```

sudo mount -t vfat /dev/sda1 "/media/ESCAPE POD"
df -h

```

---

### Post by Mimsy on 2006-11-21
Well, if cdrom0 is a mount point it  makes perfect sense to list it. :)

Those commands made the terminal do this:

> mimsy@Hawk:~$ sudo mount -t vfat /dev/sda1 "/media/ESCAPE POD"
Password:
mimsy@Hawk:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1              27G  3.6G   22G  14% /
varrun                126M   96K  125M   1% /var/run
varlock               126M  4.0K  126M   1% /var/lock
udev                  126M  104K  125M   1% /dev
devshm                126M     0  126M   0% /dev/shm
lrm                   126M   19M  107M  15% /lib/modules/2.6.15-27-386/volatile
/dev/sda1             4.7G  4.3G  377M  93% /media/ESCAPE POD

It mounted the drive, and now there is a shortcut to it on the desktop. I don't seem to have permissions to write to it though. Apparently, I made it a root-only drive. So I would need to make myself root, correct?

/Mimsy

---

### Post by taurus on 2006-11-21
You can use "sudo" to write to it if you wish or you can unmount it first and mount it using /etc/fstab with read and write permission for everybody--you.

```

/dev/sda1   '/media/ESPCAE POD'   vfat   defaults,umask=000   0   0

```
```
sudo umount "/media/ESCAPE POD"
sudo mount -a
df -h
```

---

### Post by Mimsy on 2006-11-21
I think I figred it out. I typed "sudo -s -H" into a terminal and then nautilus, to get the file browser open, and then manually copies everything I needed to copy and pasted to the USB drive. A bit crude perhaps, but it got the job done. I now have backups of everything important. :)

Edit: We must have posted at the same time. I'll save those commands fo rnext time so I can make it easier to access the mobile drive. :)

Taurus, you rule. **Thank you!**

/Mimsy

[SIZE="1"]And now to PM the url to this thread to myself, so I have all the commands for next time this happens...[/SIZE]

---

### Post by taurus on 2006-11-21
Or you can open nautilus with a root privilege with

```
gksudo nautilus
```
Now, you can drag 'n drop anywhere you want...  ;)

---

### Post by Mimsy on 2006-11-21
I tried that one first, but apparently it doesn't work if you've already self-promoted to root status, by using > sudo -s -H

I think I like not being root way better though. I might break stuff if I waved my root privileges around maniacally, without knowing what I'm doing. :)

Thanks again. I feel much better about going on the road with my laptop, now that my term paper is safely copied to a back-up device that isn't coming with us.

/Mimsy

---

### Post by taurus on 2006-11-21
> **Mimsy said:**
> I tried that one first, but apparently it doesn't work if you've already self-promoted to root status, by using 

I think I like not being root way better though. I might break stuff if I waved my root privileges around maniacally, without knowing what I'm doing. :)

Thanks again. I feel much better about going on the road with my laptop, now that my term paper is safely copied to a back-up device that isn't coming with us.

/Mimsy
Hey, whatever command or method that you feel comfortable, you should stick with it.  Who cares what others think as long as you get it done, right!  

Have a safe trip.

---

### Post by Mimsy on 2006-11-21
> **taurus said:**
> Hey, whatever command or method that you feel comfortable, you should stick with it.  Who cares what others think as long as you get it done, right!  

Have a safe trip.

Good point... "gksudo nautilus" it is then. Now, if only I could find that spare laptop mouse we have laying around here somewhere..... :)

Thanksgiving roadtrip, here I come!

/Mimsy

---

### Post by taurus on 2006-11-21
> **Mimsy said:**
> Good point... "gksudo nautilus" it is then. Now, if only I could find that spare laptop mouse we have laying around here somewhere..... :)

Maybe the cat ate it!!!  :twisted: 

> Thanksgiving roadtrip, here I come!

/Mimsy

You and a few millions other people...  #-o

---

### Post by Mimsy on 2006-11-21
> **taurus said:**
> Maybe the cat ate it!!!  :twisted: 

I would not put that past my cat, actually... She drinks vodka too. :???: 

/Mimsy

---

### Post by taurus on 2006-11-21
> **Mimsy said:**
> I would not put that past my cat, actually... She drinks vodka too. :???: 

/Mimsy
Oh dear...  :-k

---

### Post by Mimsy on 2006-11-21
Yeah, that's pretty much what we said when we caught her lapping up what was left in one of the shot glasses. She's not invited to Superbowl parties anymore.

/Mimsy

---

