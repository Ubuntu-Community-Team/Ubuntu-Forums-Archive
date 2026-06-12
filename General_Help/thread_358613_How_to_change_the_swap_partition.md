---
title: "How to change the swap partition"
date: 2007-02-11
forum: General Help
---

### Post by evenrik on 2007-02-11
I need to delete the primary partition containing swap, then create an extended partition containing a swap partition. I should be able to use Knoppix to delete/create the partitions but how do I set ubuntu (6.10) to use the new swap partition? Will ubuntu boot with its swap partition gone?

---

### Post by confused57 on 2007-02-11
You might want to use the gparted live cd(approx a 30 mb download) to repartition:
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

What you might want to before you boot up the gparted live cd  to repartition, is comment out(place a # in front of) your swap entry in your /etc/fstab:
Open a terminal(Applications---Accessories---Terminal), enter:
```
gksudo gedit /etc/fstab
```

put a # in front of your swap entry:

```
#/dev/hda5       none            swap    sw              0       0
```

this should prevent Ubuntu from trying to mount swap at startup after you've made your changes.

After you've made your new swap partition(I think there is an option to "format" as swap), make a note of all the partition changes, e.g. hda6, hda7,etc

Then boot back into Ubuntu, open your /etc/fstab & change the /dev/hdax for your swap & remove the # in front of.

I've never moved my swap partition, but this is how I would go about doing so...at least I've bumped your thread & you may want to wait for someone who's actually done this.

---

### Post by evenrik on 2007-02-12
Thanks for your suggestions. 
Here is the swap line from fstab:
```

# /dev/sda4
UUID=aedef53e-ad1e-46a6-a86d-9bde1354a315 none            swap    sw              0       0
```
So with 1 gig ram I should be able to boot with this line commented out? If so does this seem like a reasonable plan:
[LIST=1]
[*]Comment out the swap line from fstab
[*]Reboot so the boot partition is not mounted
[*]Use qtparted to delete/create the partitions
[*]Use "sudo vol_id -u /dev/[new swap partition]" to get the UUID
[*]Edit the swap line in fstab to add the new UUID and uncomment it
[*]Reboot
[/LIST]

---

### Post by taurus on 2007-02-12
Why not replace this line in /etc/fstab

```

UUID=aedef53e-ad1e-46a6-a86d-9bde1354a315 none            swap    sw              0       0

```
with this one?

```
/dev/sda4   none   swap   sw   0   0
```

---

