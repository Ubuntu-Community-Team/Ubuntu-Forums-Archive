---
title: "software raid over firewire"
date: 2007-01-23
forum: General Help
---

### Post by intentionally_lef_blank on 2007-01-23
Hi there

I installed edgy on a mac mini (cool). Everything works fine.
Now I want to use it with 2 external firewire disk in RAID 1.
I configured my old good md0 with mdadm and everything was right, disks work fine and the RAID works as well.

My problem is rebooting/shutting down the machine.
Every time the machine restarts only one disk is putted into the array. In the array I've sdb1 sdc1 but only sdb1 is included in the array at reboot.

I digged a bit and the problem is what happens in the boot sequence

1) sdb found on firewire
2) md0 starts
3) sdc found on firewire

So the problem is the array is started when only sdb is active, the array is started like if sdc was not present. When sdc is found on the firewire is too late and the array is already downgraded.

Can someone tell me How I can make md0 wait to start until the firewire 'discovery' has finished?
On the RAID array I'll have a non system filesystem so it wouldn't be a problem for me even to start the array after the full boot process has been completed.

thanks a lot!

---

### Post by matthewstory on 2007-01-23
edit your fstab and give md0 the noauto option . . . i believe this should solve the problem, but i could be wrong.  Otherwise you could remove the system start-up links for mdadm, and then hand start it everytime you boot up.

---

### Post by intentionally_lef_blank on 2007-01-24
Any mountpoint which involve md0 is already noauto.

And even disabling mdadm won't help since mdadm (the daemon)  is just a monitoring tool.
All the raid management is done at kernel module level AFAIK.

What I think is when the first firewire device is found the md kernel module starts the array but at that point sdc hasn't yet been found so the array starts downgraded.
I think dropping md module from the initrd may work, but I don't know how with initramfs-tools I can exclude this module from the 'most' option.

Thanks!

---

### Post by matthewstory on 2007-01-26
my experience with software RAID is limited, but can't you add devices to a degraded superblock with mdadm after startup.  I'm fairly certain that you can . . . read the man page on mdadm.

---

### Post by intentionally_lef_blank on 2007-01-26
yes, I can add the device after with mdadm but the array is going to be rebuilt so for the first 45 minutes (this is the time to re-sync the array) after the boot I'm basicly running on one disk which is not nice :)

---

### Post by jbfavre on 2007-02-05
Hi,
I'va had the same problem than you (but on PC :) ).
here's my workaround:
1. edit file /etc/initramfs-tools/initramfs.conf and replace MODULES= most by MODULE=list
2. edit file /etc/initramfs-tools/modules and fill it with the list of modules you want to add to initramfs. So you can load firewire stuff before raid's one or even skip raid module. It will be loaded by init later.
3. then, you can update initramfs by running: update-initramfs -u
4. and reboot :)

Hope this help.
Regards,
Jean Baptiste Favre

> **intentionally_lef_blank said:**
> yes, I can add the device after with mdadm but the array is going to be rebuilt so for the first 45 minutes (this is the time to re-sync the array) after the boot I'm basicly running on one disk which is not nice :)

---

### Post by intentionally_lef_blank on 2007-02-05
Thanks.

I fixed the problem a week ago in a very similar way.
I opened /usr/share/initramfs-tools/scripts found the md script (which is the script that brings up the md array when the machine boots) and I just added a sleep 20 in it.
Next I just used mkinitramfs to build a new initrd.
Now I have my md array working since boot which is nice.

Thanks!

---

### Post by jbfavre on 2007-02-06
Hi,
In fact, the solution I gave you is not optimal, from far. It worked but it can happened that the time to "discover" the firewire devices is not long enough: I've successfully tested it with cdrom module, but not without it :-(
I think your solution is better (because less intrusive) in the way that it doesn't need to custom module list: this can be a problem if you change your hardware configuration.
But, may I suggest you to copy the modified script in /etc/initramfs-tools/ (instead of /usr/share/initramfs-tools) in order to preserve the modification in case of package's upgrade.

Regards,
Jean Bptiste Favre

---

### Post by donthem on 2007-10-28
I am having a similar problem.  I was hoping you might have some insight into steps I can take to resolve it.  I set up a new raid-5 with mdadm with 2 IDE and one firewire.  I am guessing that the I am having the same problem as you in that the md0 is loading before the firewire drive.  If i could see your sleep thread code, that would be helpful.  The other thing is that after the firewire drive has not been used for a while it goes into a "sleep" mode (its a seagate).  So it will list with fdisk after a reboot.  but given enough time and it does not show up.  I am using ubuntu server and was hoping there was a way to keep it awake.  At the very least i would hope there would be a way to add it back to the array without having to re sync all the time.  
-Thanks

---

