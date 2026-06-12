---
title: "Excessive SWAP usage"
date: 2012-12-23
forum: General Help
---

### Post by GameX2 on 2012-12-23
Hi,

I have a laptop with 8GB of RAM, and I do virtualisation on it, with VMware.  Using VMware "Unity" mode which hide the Desktop of a virtual Windows XP, it's probably the most compatible and easy way to run Windows-only programs such as Photoshop or Illustrator.

I've allowed a maximum of 6GB of RAM to my XP guest, which previously was the ammount that gave me the most fluid experience.  The problem I have (And that I haven't got before) is that SWAP usage is excessive.  I've got a SWAP partition of only 512MB, since I do no need that much, I don't use hybernation, and I've got a small hard drive (320GB, 3-4 operating system..).

VMware start using the SWAP, even when my RAM is at only 10%.  RAM never goes above 20%, although SWAP can reach about 60%, which slow down my system.  I've been desactivating the SWAP to verify, and my system was faster for a moment (Well, only for a while - for some reason, Firefox and VMware later closed by themselve - and I had to retype this post all over!).
Isn't SWAP used as a last resort?  I've got 85-90% of RAM free, why is SWAP used?  I've even set VMware to use only reserved memory (Avoid using SWAP, if possible)?

I've also changed the vm.swappiness to 20 that way:

```
sudo sysctl vm.swappiness=20
sudo swapoff -av
sudo swapon -av

```

Made the settings permanent, by adding the line "vm.swappiness=20" to the file " /etc/sysctl.conf ".  Is this settings supposed to optimize the SWAP?  Only when my RAM reach 80% of usage, SWAP is used?
Well, I don't know why, but that's not working.

How can I fix this?


Thanks!

---

### Post by hunterkasy on 2012-12-23
I am posting this just so others know how to do it

What is swappiness and how do I change it?

The swappiness parameter controls the tendency of the kernel to move processes out of physical memory and onto the swap disk. Because disks are much slower than RAM, this can lead to slower response times for system and applications if processes are too aggressively moved out of memory.

    swappiness can have a value of between 0 and 100
    swappiness=0 tells the kernel to avoid swapping processes out of physical memory for as long as possible
    swappiness=100 tells the kernel to aggressively swap processes out of physical memory and move them to swap cache 

The default setting in Ubuntu is swappiness=60. Reducing the default value of swappiness will probably improve overall performance for a typical Ubuntu desktop installation. A value of swappiness=10 is recommended, but feel free to experiment. Note: Ubuntu server installations have different performance requirements to desktop systems, and the default value of 60 is likely more suitable.

To check the swappiness value

cat /proc/sys/vm/swappiness

To change the swappiness value A temporary change (lost on reboot) with a swappiness value of 10 can be made with

sudo sysctl vm.swappiness=10

To make a change permanent, edit the configuration file with your favorite editor:

gksudo gedit /etc/sysctl.conf

Search for vm.swappiness and change its value as desired. If vm.swappiness does not exist, add it to the end of the file like so:

vm.swappiness=10

Save the file and reboot.

---

### Post by GameX2 on 2012-12-23
[http://img267.imageshack.us/img267/5339/capturedu20121223210458.png](http://img267.imageshack.us/img267/5339/capturedu20121223210458.png)

Why is my SWAP so high, when my RAM is almost not used?
My SWAP is now at 67%, and RAM hardly go beyond 16% ! :O

(God, 85%, I expect crashing... RAM is only at 11%, what's going on?)

---

### Post by offgridguy on 2012-12-23
This subject is dealt with at length in this thread.:D

[http://ubuntuforums.org/showthread.php?t=2096393](http://ubuntuforums.org/showthread.php?t=2096393)

---

### Post by GameX2 on 2012-12-23
Thanks, I'll read that.

Ubuntu just crashed, took about 5 minutes - RAM was at 09% when SWAP reached 100%..
Maybe that 500MB of SWAP is just not enough, even without hibernation and 8GB of RAM (I do not plan of creating a 16GB SWAP partition, that's too big for my hard disk).

I'll read!

EDIT:

I've disabled my SWAP partition, set VMware to use only reversed memory, no SWAP, and installed zram-config.
The performance is MUCH better, and installation of the softwares in the VM is extremely faster, as well.  But there's still something I find odd; I would like to understand.

[http://img145.imageshack.us/img145/5505/capturedu20121223221117.png](http://img145.imageshack.us/img145/5505/capturedu20121223221117.png)

Now, my 500MB SWAP partition is disabled, but why do I still have 7% of SWAP used?  Even weirder, in the System Monitor, I see 3.9GB of SWAP availible.
Where does this 3.9GB of SWAP come from?

I believe the problem is solved now, the VM was really fast - that's just weird.  I disabled my SWAP partition, and Ubuntu somewhat manage to use 3.9GB of SWAP...

---

