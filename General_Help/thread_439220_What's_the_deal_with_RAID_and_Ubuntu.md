---
title: "What's the deal with RAID and Ubuntu?"
date: 2007-05-10
forum: General Help
---

### Post by Crakie on 2007-05-10
I am considering to set up a RAID 0 configuration, but there is annoyingly little comprehensive documentation on it. Here are some questions I have about RAID 0 and Feisty (which I am running currently):

1) Ubuntu does not support the JMicron and ICH8R sata-controllers on my Abit AB9 Pro very well... since Dapper I need to fiddle with kernel options to get it working. Perhaps not a good idea to ask even more of it?

2) Would I be able to boot straight from a RAID 0 array? I can imagine it is a problem since at boot no drivers could have been loaded. If it is indeed a problem, how do I go around that? 

3) Do you really need to server/alternate install CD for it to set up RAID?

4) If I understand correctly, RAID drives cannot be partioned but one can use LVM to overcome that?

---

### Post by ohgod on 2007-05-10
1) Not sure.  Perhaps the kernel that comes with Feisty recognizes this controller now?  You could check the hardware compatibility list.

2) As long as the kernel recognizes the array correctly, this shouldn't be a problem (I setup a mail server not too long ago that boots off a RAID 10 array).

3) Only for software RAID, I believe.  If you can get the kernel to recognize your RAID array as a disk, you should  be able to install any version you wish.

4) Hardware RAID arrays should appear to the OS to be normal drives.  So you should be able to do anything with the array that you could with a signle disk (once again assuming you can get the kernel to recognize it).

Hope this helps.

---

### Post by NT4usB on 2007-05-10
I gave up on the Promise chip on my 850 board and went with a software RAID. Lots of journeys to Synaptic but didn't need the CD.
One big 240GB blob.
Been using it for a couple months for Myth recordings.  Rock stable so far.

---

### Post by Crakie on 2007-05-10
Thanks guys. I think the RAID support on motherboards does not count as hardware raid, correct? So that leaves software RAID. Since the kernel is not loaded at boot time, I am worried Grub might stop functioning. Are you booting from the array, NT4usb, or from another drive?

---

### Post by ohgod on 2007-05-10
Well, the RAID support on your motherboard is not 'hardware RAID' in the sense it's got software on the bios controlling the arrays (as opposed to expensive RAID controllers).  But as far as you're concerned it is hardware RAID.  The RAID controller on the board will handle the array, and the OS won't know anything about it.

So if you boot into the bios you should be able to create an array that way.  Then with luck Ubuntu will see the array as a normal drive and treat is as such.

---

### Post by NT4usB on 2007-05-10
> **Crakie said:**
> ... Are you booting from the array, NT4usb, or from another drive?

The OS is on a separate drive. The raid is just storage.

---

### Post by psusi on 2007-05-10
I suggest that you read [https://wiki.ubuntu.com/FakeRaidHowto](https://wiki.ubuntu.com/FakeRaidHowto)

If you want to use the motherboard's fake raid support, you can, if you put in the effort.  If you don't need to dual boot with windows, then you can just use pure software raid instead, which is easier and better supported.  To do this you will want to undo any raid in your bios, then use the alternate cd to install.  Set up a /boot partition on the primary disk, then make a second partition using the rest of the disk, with a partition of the same size on the second disk configured as md raid 0 for your root.

---

### Post by Crakie on 2007-05-11
Ah I see, software-raid seems the way to go then. My suspicion of Grub not being able to load from Raid 0 seems correct, but putting /boot elsewhere (not on the array) should solve that. I guess my current HD would be perfect for that.

---

