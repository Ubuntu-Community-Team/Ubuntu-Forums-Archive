---
title: "[SOLVED] Problems installing applets"
date: 2008-06-13
forum: General Help
---

### Post by IowaMike on 2008-06-13
Noob to Linux, really got fed up with Windows after yet another vaporlock. Managed to config a dual boot with XP & Hardy Heron with much help from reading the board. I now have a new issue trying to install additional programs or applets (whichever you call them) Keep getting the following error:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I went to terminal and ran "sudo dpkg --configure -a". end result was a system lockup. Had to boot from Ubunto 8.04 cd using the "boot to 1st disk" option.

Any help is appreciated.

---

### Post by forestpixie on 2008-06-13
Can you run it again and get the error message if there is one please.

---

### Post by IowaMike on 2008-06-13
Setting up initramfs-tools (0.85eubuntu39.1) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.24-18-generic

gzip: stdout: No space left on device
update-initramfs: failed for /boot/initrd.img-2.6.24-18-generic
dpkg: subprocess post-installation script returned error exit status 1

---

### Post by forestpixie on 2008-06-13
Can you post the output of

```
df -h
 cat /boot/grub/menu.lst |grep kernel*
```

---

### Post by IowaMike on 2008-06-13
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb4              14G  2.7G   11G  21% /
varrun               1008M  100K 1008M   1% /var/run
varlock              1008M     0 1008M   0% /var/lock
udev                 1008M   88K 1008M   1% /dev
devshm               1008M   12K 1008M   1% /dev/shm
lrm                  1008M   43M  966M   5% /lib/modules/2.6.24-16-generic/volatile
/dev/sdb3              46M   42M  1.3M  98% /boot
/dev/scd1             698M  698M     0 100% /media/cdrom0
/dev/sdb1              24G  9.9G   14G  43% /media/disk
mike@AMD3200:~$  cat /boot/grub/menu.lst |grep kernel*
# kernel	/vmlinuz root=/dev/hda2 ro
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## Xen Linux kernel options to use with the default Xen boot option
## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
title		Ubuntu 8.04, kernel 2.6.24-18-generic
kernel		/vmlinuz-2.6.24-18-generic root=UUID=f4cc8b58-b2ab-4860-8658-c68d0773fa12 ro quiet splash
title		Ubuntu 8.04, kernel 2.6.24-18-generic (recovery mode)
kernel		/vmlinuz-2.6.24-18-generic root=UUID=f4cc8b58-b2ab-4860-8658-c68d0773fa12 ro single
title		Ubuntu 8.04, kernel 2.6.24-16-generic
kernel		/vmlinuz-2.6.24-16-generic root=UUID=f4cc8b58-b2ab-4860-8658-c68d0773fa12 ro quiet splash
title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
kernel		/vmlinuz-2.6.24-16-generic root=UUID=f4cc8b58-b2ab-4860-8658-c68d0773fa12 ro single
kernel		/memtest86+.bin

---

### Post by forestpixie on 2008-06-13
It's another boot partition that is too small - open synaptic and search for linux-image and remove the -16 one. There will also be residual configs after you've done - remove them as well. Then run the df -h command again

check this line in the output
> /dev/sdb3 46M 42M 1.3M 98% /boot

You need approx 25Mb for each kernel I think.

After you've done it will be worth looking into resizing that partition so that it is a bit bigger.

As an aside could you tell me where you got the information for the size and reaasoning behind your /boot partition.

---

### Post by IowaMike on 2008-06-13
I wondered about that when the boot menu showed -16 & -18 Kernels. I found a page that said about 512 MB for swap, 50 MB for /boot and remainder for /. Can't find the link at the moment, will post it later. It involved using manual partitioning during install. I'll do the other you suggested later as well, need to get some sleep. Thanks for the inputs thus far.

---

### Post by forestpixie on 2008-06-13
Have a good sleep - you need to really have about 100Mb as /boot , but I don't bother with all those /things too much and only have / and /home then it can have as much as it wants.

---

### Post by IowaMike on 2008-06-13
Now I get the original error when I try to open synaptic. Any commnad line option to remove the -16 kernel?

---

### Post by forestpixie on 2008-06-13
OK I've done this on a virtual machine to make sure that it did work. Start up in recovery and drop to a root prompt and run these

dpkg purge linux-image-2.6.24-16-generic

but it will probably complain about the dpkg error you could try to run that first

dpkg --configure -a

If you can't run the dpkg without the kernel remove I would use the livecd to resize the boot partition. If you do that before you post back -= boot the livecd and get a scrnshot of the gparted window.

---

### Post by IowaMike on 2008-06-13
"dpkg purge linux-image-2.6.24-16-generic" returns the following:

dpkg: need an action option

"dpkg --configure -a" returns the following:

Setting up initramfs-tools (0.85ebuntu39.1) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.24-18-generic

gzip: stdout: No space left on device
update-initramfs: failed for /boot/initrd.img-2.6.24-18-generic
dpkg: subprocess post-installation script returned error exit status 1

---

### Post by IowaMike on 2008-06-13
That was booting into 2.6.24-18-generic recovery. should I have booted into the -16 recovery instead?

---

### Post by forestpixie on 2008-06-13
no boot the new one and  try apt-get purge instead , that was what I actually used in the virtual machine, but I found a thread tha suggested dpkg instead.


```
dpkg --purge linux-image-2.6.24-16-generic
```

---

### Post by IowaMike on 2008-06-13
apt-get returned:

E: dpkg was interrupted, you must manually run "dpkg --configure -a" to correct the problem.

the --purge code returned an error for "dependency problems prevent removal"..etc

---

### Post by forestpixie on 2008-06-13
I'm not sure then - don't want to break your system. I would either wait for someone else to see it or go for resizing the partition. If you want to resize I will watch the thread. Sorry otherwise.

---

### Post by IowaMike on 2008-06-13
wondering if it's making a difference that I'm using Ubuntu AMD64 as opposed to the i86 version. I appreciated the time you've taken to try to help. Maybe a clean install is the answer but I'm afraid to after all the issues I had getting to dual boot in the 1st place.

---

### Post by forestpixie on 2008-06-13
No the commands should be the same. I wouldn't do a clean install.. at least not yet, why don't you boot the livecd then open the partition editor and post a scrnshot of it and we can see how painless that would be. 

If you can make the partition bigger then the dpkg configure command will work.

I don't have to sleep for another bunch of hours yet so can stay and help you if you want :)

---

### Post by forestpixie on 2008-06-13
Alternatively report your thread and ask a mod to retitle the thread to something more appropriate to the thread - anyone looking quickly would see a thread about applets :)

Maybe along the lines of

/boot too small - how can I remove old kernel

It would also help anyone searching titles on the forum.

---

### Post by IowaMike on 2008-06-13
I'll try the LiveCD partitioner after I get off work and post a screenshot if I can't resize.

---

### Post by forestpixie on 2008-06-13
Ok bear in mind that resizing can take a while so don't panic - good luck and I will catch up this tomorrow.

---

### Post by IowaMike on 2008-06-15
I brainfarted & deleted the boot partition before I resized so I ended up reinstalling 8.04. Only lost a couple e-mails & bookmarks so no real harm done. After the upgrades installed I still have -16 & -18 on the boot menu. Don't want to mess with anything further since it's working. Thanks again for your help and patience.

---

### Post by forestpixie on 2008-06-15
You're welcome - if you installed with a /boot partition I hope you made it bigger :)

Can you mark thread solved please

---

