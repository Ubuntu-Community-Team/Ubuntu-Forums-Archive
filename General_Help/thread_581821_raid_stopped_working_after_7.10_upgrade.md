---
title: "raid stopped working after 7.10 upgrade"
date: 2007-10-19
forum: General Help
---

### Post by jba on 2007-10-19
I've had a bit of problem booting my box since I upgraded to Feisty, but last night after going to Gutsy it stopped working completely. 

Here's the parameters:

I have two drives hda and hdb that are in a raid-1 configuration. A while ago, a few weeks after going to Feisty, the machine wouldn't boot with messages that drives hda and hdb weren't ready for command:

> hda: drive not ready for command

and then some dma error code. After a bit of digging I came up with the solution of adding 

> ide=nodma

to my kernel boot options and it started working again. Mind you that I still had errors saying something like 

> Device /dev/hda1 not ready for command

or similar for one or both of the drives, but the raid-disks /md0-3 were able to mount and start. When booted there were never any probs with the raid array and mdadm always reported no errors and the devices in sync. 

**Flush forward to present time**, after upgrading to 7.1 Gutsy. Now I'm getting similar errors for _both drives_ and the _md disk mounting stops completely_ and I enter the Busy Box prompt. 

Mind you that the disks look fine - I can start a RescueCD (with ide=nodma) and mount each of the drives manually and look at the files. But I cannot get the machine to boot anymore. 

I checked the /etc/mdadm/mdadm.conf and it has the same UUIDs as I see when running mdadm --examine /dev/... 

I'm getting the feeling that my disks aren't entirely healthy perhaps, but that didn't stop them from booting the system until last nights' upgrade to Gutsy. Could I have broken anything in my mdadm configuration. Anyone have any ideas what to look for ? 

One thing peculiar about mdadm.conf: All the md0 through md3 devices are listed twice, with the exact same data. Is that really correct ? 

Also, is there a way to start and access the raided disks (md0 etc) from a LiveCD if I want to touch the data ? I'm not so sure about touching one disk that I have mounted directly and then have the mdadm freak out when the disks differ. 

Finally, is there something that should be done to initramfs or something after an upgrade, for the purpose of mdadm ? Is there a way to make the mount wait longer for the disks to become available or something ?

---

### Post by yota on 2007-10-19
Same problem here, posting just yo let you know that you're not alone...

The only solution that works for me so far is to boot with the feisty's kernel (2.6.20-16-generic), with the 2.6.22 ther's no way I can get the arrays assembled.

To start the array from a live you can try something like:
```

mdadm --verbose --assemble /dev/mdX /dev/sda /dev/sdb ....

```

I'll post again if I can find a real solution.

---

### Post by yota on 2007-10-20
Ok, someone else found a solution that worked for me:

see [http://ubuntuforums.org/showthread.php?t=583003](http://ubuntuforums.org/showthread.php?t=583003)

long story short is to remove the evms package.

I wasn't able to assemble /dev/mdX because evms already did it under /dev/mapper/dm-X, now that I purged the package everything is back to normal and /dev/mapper contains just the control file.

Hope this helps!

---

### Post by fjgaude on 2007-10-20
Assuming you are using mdadm, and not dmraid, try this:

```
sudo mdadm --assemble --scan --verbose
```

and let us see the results. mdadm should find the /dev/md[n] array.

---

### Post by jba on 2007-10-22
> To start the array from a live you can try something like:

```
mdadm --verbose --assemble /dev/mdX /dev/sda /dev/sdb ....
```



Ok, I'll try that and see if I can make the Feisty kernel available. I'm a bit low on space on /boot so I moved the 2.6.20-16-generic image to elsewhere... So now I only have 2.6.22 available for Grub. 

Once that's done I hope to at least be able to boot into Feisty kernel and start using those other tips. 

Thanks !

---

### Post by evver on 2007-10-25
I also could not get raid to work after upgrading to Gutsy.  I would get errors like "no such device", etc...  No matter what I did Gutsy would not recognized the raid.  I then switched to using kernel 2.6.20-16, as mentioned above, and then everything worked -- no other changes needed.

---

### Post by jba on 2007-10-26
> **evver said:**
> I also could not get raid to work after upgrading to Gutsy.  I would get errors like "no such device", etc...  No matter what I did Gutsy would not recognized the raid.  I then switched to using kernel 2.6.20-16, as mentioned above, and then everything worked -- no other changes needed.

Ok, I'm having a problem here with switching to kernel 2.6.20-16. This kernel is the one I used before the upgrade to Gutsy and it is in the Grub boot list. However, when booting with this kernel I get something like this:

```
kernel panic-not syncing VFS Unable to mount root fs on unknown-block (0,0)
```

So something is corrupt with my old kernel config. I've googled this and found people succeeding by reinstalling the kernel in question (possibly something to do with a messed up sources.lst)

Since I cannot in any way boot into the system, how would I go about re-installing the odl kernel from a rescue / live CD linux ? 

From what I can find when browsing it would be something like this:

* boot into live CD
* mount raid manually ( mdadm --assemble /dev/md0 /dev/hda1 /dev/hdb1    etc )
* chroot /dev/md0 /bin/bash (**not sure about this step**... md0 is where my /boot is mounted, md1 is where / is mounted... which should it be ? ? ) 
* apt-get remove linux-image-2.6.20-16 
* apt-get install linux-image-2.6.20-16 

Is this a correct mode of operation ? Would this reinstall the 2.6.20-16 kernel on my raid device ? 

Also, should I be using the Gutsy sources (which I assume is configured now) or the old Feisty sources.lst ? 

Hmm, this is getting confusing.

---

