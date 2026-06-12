---
title: "I have a problem with the ID of my sata HDD with raid"
date: 2008-02-19
forum: General Help
---

### Post by plnp123 on 2008-02-19
Hello to everyone.
Im having the first experiences wit ubuntu and i got the ultimate edition distro (based in 7.10)  to have already many apps at hand. however im experiencing some troubles and i think theyre cused by my SATA drive with RAID
My hdd has 5 partitions (1 for files fat 32, for inux ext3 1 swap one that is still empty reserved for windows and 1 for the recoevery) at first ubuntu worked fine and smooth however my first problem ocurred when some blocks became corrupt but i solved that with fdisk. Later there were a lot of troubles to run the OS and i had to work Live yesterday. Today i tried to boot again from disk to use this: [http://www.ubuntu-in.org/wiki/SATA_RAID_Howto](http://www.ubuntu-in.org/wiki/SATA_RAID_Howto) buti couldnt even run the live. i tried to boot from the HD and it was laggy before it froze. 
When i try to boot from CD I get this message

error logical block (number)
sata_id [3628]: main: HDIO_get_identity failed for '/dev/.tmp-8-0'

 I also tried to use the systemrescue cd but it doesnt work either. 
How can i get the SATA HDD to work
What happens if i change the conf  in the BIOS (Raid to something else)

Thank you for all the help

---

### Post by fjgaude on 2008-02-19
Gosh, what kind of raid were you using... dmraid or mdadm? Or were you just using the motherboard's raid setup?

What command did you use with fdisk when you used it?

We need more information to be able to maybe help.

---

### Post by plnp123 on 2008-02-19
I am using the motherboard RAID its the option in the BIOS.
Also i had a mistake it was fsck because it was an error in the file system.
Anoyher stmptom is that sometimes i get an error that claims that the HDD falure is inmininent and that i have to change the HDD
Also in the live mode using start or install, i get always the busybox but if i use the safe graphics mode i can enter the system.
i think that the problem is the SATA drive badly configured
In the safew graphics mode, gpart doesnt showed  any device, not even in the installation.  I tried then from the firdt HDD and it displayed "error bootng press any key to retry" and its an infinite loop

---

### Post by fjgaude on 2008-02-20
Ubuntu will not recognize your raid unless you have setup dmraid after it is installed. You will not be able to boot into Ubuntu using motherboard raid.

So much going on here I can't really be of much help.

Maybe someone else can get you going in the right direction.

---

### Post by plnp123 on 2008-02-20
Thanks i think I will go for a low level format so I can start again all over and install dmraid  correctly
Does someone has a tutorial to format a SATA or is any application better tahan the other?

---

### Post by fjgaude on 2008-02-21
There's nothing wrong with the GUI-based Gparted:

```
sudo apt-get install gparted
```

I tend to use cfdisk, which can be obained with apt-get or Synaptic.

I think you have to install dmraid also, can't remember.

---

