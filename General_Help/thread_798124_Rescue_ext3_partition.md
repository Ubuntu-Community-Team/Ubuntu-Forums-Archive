---
title: "Rescue ext3 partition"
date: 2008-05-17
forum: General Help
---

### Post by pavpan on 2008-05-17
I've been trying to reinstall, and before the reinstall I had the following partitions:

1. / partition
2. /home partition
3. swap partition
4. / partition from old install

I decided to go with lvm this time around, and so decided to delete the /, old /, and swap partitions and making an LVM partition out of it. (Leaving the /home partition as I had a lot of important data on it.

I set that up correctly, but now Ubuntu does not recognize my /home partition as any sort of bootable file system. Gparted shows it just as an unknown partition, and fdisk does not recognize it. I can't mount it either, as I am am told by mount "/dev/sdb2 is already mounted or /mount/bobdole busy". How can I save my data?! HELP!

---

### Post by Patb on 2008-05-18
Pavpan, could you post the output of 
```
sudo fdisk -l
```
Even though "fdisk does not recognise it", that output might be informative.  (I don't use lvm by the way so I probably won't be much help - sorry.)

Cheers, Pat.

---

### Post by cdtech on 2008-05-18
> "/dev/sdb2 is already mounted or /mount/bobdole busy"

With LVM:

You don't mount a "LVM" partition the same way you mount a regular partition

what is the output:
pvs
this will list your volume groups
like this:
/dev/hda2  VolGroup01
/dev/hdb2  VolGroup00

lvdisplay /dev/VolGroup01
this will show the lv name needed to mount

mount /dev/VolGroup00/LogVol00 /tmp/mnt (or whatever your home mount point in that volume is)

Hope this helps.....

---

### Post by pavpan on 2008-05-18
I've (partially) figured out what's wrong:

4 Partitions:
1. /boot
2. Was planning on making it /, but right now its just empty space
3. Was planning on not touching it, but now its / (overwriting old /home)
4. swap

The new / (old /home) has about 9G free. Is there any good tool to extract any files that may be left? The files I'm looking to recover are simple text files, so there's a chance they are recoverable.

---

### Post by geo909 on 2008-05-18
Yes, I think there is. 

Try [System rescue CD]("http://www.sysresccd.org/").
It's a live CD with many rescuing tools. There is one (test-disk) for saving whole partitions. I guess there will be some tool for your case.

[Trinity]("http://trinityhome.org/Home/index.php?wpid=1&front_id=12") resque kit is another live CD of the same nature..

---

