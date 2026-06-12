---
title: "Repartioning"
date: 2007-01-28
forum: General Help
---

### Post by Titus A Duxass on 2007-01-28
Okay it's my turn to hose up!
I have just changed the size of my partitions using gparted from the live CD.
I have three partitions:
hda1 5.3gb as / - ext3
hda2 2.0gb swap
hda3 270gb as /var/lib - xfs

I resized them to:
hda1 12.0gb
hda2 3.0gb
hda3 264.0gb (ish) 

I kept the same layout, I did not reformat them.

Now the myth box will not boot, I get the following message:
Server Authorization directory (daemon/ServAuthDir) is set to /var/lib/gdm but this does not exist.  Please correct GCM configuration and restart GDM.

Sudo dpkg-reconfigure gdm gives:

failed to open package info file `/var/lib/dpkg/status' for reading: No such file or directory.  GDM is not installed.

Output of sudo fdisk -l
/dev/hda1 linux
/dev/hda2 swap
/dev/hda3 linux

(abbreviated version).

Cat /etc/fstab:
/dev/hda1
UUID=30dd42fe-609b-4ed-b3cf-ef6c390dc6ac / ext3 defaults,errors=remount-ro 0 1
/dev/hda3
UUID=9050001d-a7ee-42c5-9c7b-138ec7510fce /var/lib xfs defaults 0 2
/dev/hda2
UUID=dee41b3a-c065-46a8-8116-89473fa74f4b none swap sw 0 0 
/dev/hdc /media/cdrom0
/dev/ /media/floppy0

Can anyone provide some pointers as to what I should be doing (yes I have searched, but failed to find any thread which describes my problem).

Thanks
Titus

---

### Post by hal10000 on 2007-01-28
> 
/dev/hda1
UUID=30dd42fe-609b-4ed-b3cf-ef6c390dc6ac / ext3 defaults,errors=remount-ro 0 1
/dev/hda3
UUID=9050001d-a7ee-42c5-9c7b-138ec7510fce /var/lib xfs defaults 0 2
/dev/hda2
UUID=dee41b3a-c065-46a8-8116-89473fa74f4b none swap sw 0 0

Maybe when you repartitioned the UUID's of your partitions were changed.

So you can either look into /dev/disk/by-uuid directory to see how the actual links are named ([COLOR="Red"]ls -l /dev/disk/by-uuid[/COLOR]) and change them in your /etc/fstab (and probably in your /boot/grub/menu.lst too)

or you might substitude the UUID's with their real /dev/hdaX names (also in both your /etc/fstab and in /boot/grub/menu.lst

I would first try to change only the settings in /etc/fstab and if this is not sufficant then also change /boot/grub/menu.lst

---

### Post by Titus A Duxass on 2007-01-28
Okay, ls -l  /dev/disk/byuuid/ reveals that only hda1 and hda2 are listed. There is no entry for hda3.

Hda3 is my /var/lib partition which I reduced in size, so that seem to be my problem. How do I recreate the entry for hda3?

---

### Post by hal10000 on 2007-01-28
That's strange. You should just change the UUID entry to /dev/hda3 in your /etc/fstab.
then try to mount your /etc/fstab entries again: [COLOR="Red"]sudo mount -a[/COLOR]
Verify if your hda3 is really mounted ([COLOR="Red"]mount[/COLOR])
Then reboot and see what happens.

---

### Post by Titus A Duxass on 2007-01-29
After quite a bit of buggering about I solved it by reinstalling :-)

---

