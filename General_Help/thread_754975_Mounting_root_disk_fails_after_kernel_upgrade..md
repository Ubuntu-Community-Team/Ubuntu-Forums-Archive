---
title: "Mounting root disk fails after kernel upgrade."
date: 2008-04-14
forum: General Help
---

### Post by steve196 on 2008-04-14
Again an old issue, that comes back despite relatively new Wubi version:
After an update, with the new kernel i get:
Mounting /dev/disk/by-uuid/386E-3D77 on /root failed: No such device
With the old kernel everything is fine.

---

### Post by ago on 2008-04-14
Is the root line in menu.lst correct?

---

### Post by steve196 on 2008-04-14
The arguments in menu.lst are exactly the same with the old and the new kernel. Especially the uuids are the same. The root lines are also the same.and they show the right directory on the right harddisk.

---

### Post by ago on 2008-04-14
boot with the kernel option "debug"
and then look into the log in /tmp for more clues
you may want to try mounting it manually (use /dev/sdaX as opposed to UUID)

what are the kernels involved by the way?

---

### Post by Who on 2008-04-19
I have this problem too. Is it because I have a fat32 partition? It looks a bit like the problem I had back here
[http://ubuntuforums.org/showthread.php?t=604107](http://ubuntuforums.org/showthread.php?t=604107)

When I am done with the work I am doing now, I will reboot and get some more info - try mounting manually, etc...

Is there any way to get the logs from Linux not from Windows?

Who

---

### Post by Who on 2008-04-20
> **Who said:**
> 
When I am done with the work I am doing now, I will reboot and get some more info - try mounting manually, etc...
Who

Right, I tried

mount /dev/disks/by-uuid/<whatever it was> /root

I get 'Invalid Argument' if I use -t auto and "No such device" if I use -t vfat or -t msdos

Any help?

Who

---

### Post by ago on 2008-04-20
What was the last working kernel?
Can you see the content of /var/log/syslog and dmesg after mounting?

---

### Post by ago on 2008-04-20
Can you also try using /dev/sda1 (or whatever it is as listed in cat /proc/partitions)?
It might be that the UUID is not correct.

---

### Post by Who on 2008-04-20
> **ago said:**
> Can you also try using /dev/sda1 (or whatever it is as listed in cat /proc/partitions)?
It might be that the UUID is not correct.

Will do so, but seems unlikely as UUID is same for new kernel as it is for the old.

Also:
2.6.24-15-generic is working
2.6.24-16-generic is not working

---

### Post by Who on 2008-04-20
> **ago said:**
> Can you also try using /dev/sda1 (or whatever it is as listed in cat /proc/partitions)?
It might be that the UUID is not correct.

That fails in the same way as above

---

### Post by ago on 2008-04-20
Can you mount the same partition off the live CD?

---

### Post by Who on 2008-04-21
> **ago said:**
> Can you mount the same partition off the live CD?

I have no CD ROM drive - hence I'm using Wubi :P

I can mount the partition from my older kernel - but you know that...

What else should I try? I know you asked for some logs but I don't know how to get the right ones... Could you give me a bit more guidance?

---

### Post by ago on 2008-04-21
a live CD would help here...

With rev 492 you can press esc at boot and see if the last option works (read only demo).

---

### Post by Who on 2008-04-21
> **ago said:**
> a live CD would help here...

With rev 492 you can press esc at boot and see if the last option works (read only demo).

Sorry ago - this is turning out to be a bit of a nightmare!

I only have 128mb of ram - so any recent version of wubi doesnt run. I had to do the install using ubiquity noninteractive after killing the X session (srq+RSE) and it worked, but a live CD will almost certainly not :S

As far as getting info from my running Linux system goes - no probs, I can get anything - but I am not in a position to do CD or memory requiring stuff. Sorry!

Thanks for sticking with me here!

Who

---

### Post by thedoorguy on 2008-04-22
just prior to dropping to shell... the updated -16 version runs a scrip that tries to load root... when it can't find it in the normal place it looks in /host/ubuntu/disks where the file were located on my computer...  problem is /host is not being correctly identified.    I reported this bug to launchpad over a week ago and never got even one response.  

I dumped the wubi install. Way too may problems.  Never could get keep it running and no one on the big board offers any help for the problems I encountered.  With a disk load... I have very few difficulties.

---

### Post by ago on 2008-04-22
Was your bug marked as incomplete? if so it means more info is required to assess the situation.

---

### Post by thedoorguy on 2008-04-23
> **ago said:**
> Was your bug marked as incomplete? if so it means more info is required to assess the situation.

I didn't keep anything with the bug number and because I never received email about any reply, never went back.

When I had the problem... which I recreated each of the three  times I reinstalled wubi-ubuntu... the lines left on sceen after booting with kernel vers...-16 in recovery mode was something about going to script then trying to mount root from where ever disk install puts its... then when that failed the next line came up trying to mount it from location /host/unbuntu/disks... but the program couldn't a root there either, the next line was an alert message. I think that the /host/ubuntu/disks location didn't exist, then the program dropped to busybox.  (I think /host was not id'd correctly because the files were positively at c:\ubuntu\disks on my computer and the -15 version could find them and load ubuntu.)

I then restarted my computer... "esc" after selecting ubuntu, which took me to another menu with an option to use the -15 kernel which I would select and ubuntu would boot right up.

That's all I know.  Am using the disk version now so can't recreate the problem to provide more specific verbage.

thedoorguy

---

### Post by ago on 2008-04-23
In my case the kernel upgrade broke acpi support. See my reports here [https://bugs.launchpad.net/ubuntu/hardy/+bug/146692](https://bugs.launchpad.net/ubuntu/hardy/+bug/146692).

Difficult to say if it was the same issue for you.

---

### Post by Who on 2008-04-24
> **ago said:**
> In my case the kernel upgrade broke acpi support. See my reports here [https://bugs.launchpad.net/ubuntu/hardy/+bug/146692](https://bugs.launchpad.net/ubuntu/hardy/+bug/146692).

Difficult to say if it was the same issue for you.

My bios is too old (1999) and so acpi isn't used anyway - so I don't think it can be that...

Any more ideas?

Who

---

### Post by ago on 2008-04-24
> **Who said:**
> My bios is too old (1999) and so acpi isn't used anyway - so I don't think it can be that...

Any more ideas?

Who

You have to log in verbose mode and with "debug" as a kernel boot parameters. Then access the logs in /tmp and provide as much information as possible. I would suggest though to open a kernel bug in launchpad.

---

### Post by Who on 2008-04-24
> **ago said:**
> You have to log in verbose mode and with "debug" as a kernel boot parameters. Then access the logs in /tmp and provide as much information as possible. I would suggest though to open a kernel bug in launchpad.

Will do.

will the logs still be in /tmp once I reboot, beacuse if not, how do I 'get them out' as it were...? Maybe this is trivial, but I am not familiar with using un/partially booted systems! 

I just looked again at the messages when it does and doesn't work and noticed that in -15 the loop module is loaded just before the disk is mounted, but not in -16

Unfortunately, loading loop and then trying to mount still doesn't work - but perhaps it gives a clue?

Who

---

### Post by Who on 2008-04-24
> **Who said:**
> Will do.

will the logs still be in /tmp once I reboot, beacuse if not, how do I 'get them out' as it were...? Maybe this is trivial, but I am not familiar with using un/partially booted systems! 

I just looked again at the messages when it does and doesn't work and noticed that in -15 the loop module is loaded just before the disk is mounted, but not in -16

Unfortunately, loading loop and then trying to mount still doesn't work - but perhaps it gives a clue?

Who

So, I answered the first question myself: no. So I tried to plug in a USB device to save on to there, but I couldn't mount it (it was detected). I found the debug file in /tmp and had a look and it showed some vfat module was supposed to be loaded before we try and mount the main disk to /root - I did cat /proc/modules | grep fat and also tried dos, 32 vfat, do, ms, etc. I couldn't find anything fat like. WHen I tried to load the module myself it claimed it did not exist, but when I used modprobe -Qb as is in the script it just returned with no error, but no new modules showed up.

So, as I only have fat usb disks and I don't have a floppy drive I don't know how to give you the debug log. I can keep poking around if you tell ne where to look. 

This is _almost_ fun :P

Who

---

### Post by ago on 2008-04-24
Are the kernel and initrd for the same version?

---

### Post by Who on 2008-04-26
> **ago said:**
> Are the kernel and initrd for the same version?

Yes, they are.

I built a new initrd - using the verbose option and I've attached the output. To be certain - here's the command I used:

```
update-initramfs -c -k 2.6.24-16-generic -v > initrambuildlog.log
```

I couldn't see that the vfat module had gone in... but it does exist.

```
$ ls /lib/modules/2.6.24-15-generic/kernel/fs/vfat/
vfat.ko
```

ALSO. I noticed something that might be useful in the update output (from a dist-upgrade, but I get the same when running dpkg-reconfigure initramfs-tools)
```
Processing triggers for initramfs-tools ...
ln: creating hard link `/boot/initrd.img-2.6.24-16-generic.dpkg-bak' => `/boot/initrd.img-2.6.24-16-generic': Operation not permitted
update-initramfs: Generating /boot/initrd.img-2.6.24-16-generic
```

---

### Post by ago on 2008-04-26
The linking is not permitted in vfat. This is normal. But the iniramfs should fall back to a normal copy procedure so you should still end up with the initrd in /boot.

You can unpack the initrd and check what is in there.

mkdir initrd-dir
cd initrd-dir
gunzip -c -9 ../initrd-file | cpio -i -d -H newc --no-absolute-filenames

---

