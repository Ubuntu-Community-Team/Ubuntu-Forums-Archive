---
title: "Ubuntu 12.04 won't boot, getting error"
date: 2014-07-17
forum: General Help
---

### Post by Andi_GreyScale on 2014-07-17
I've been on 12.04 since it was released and have never had this issue. 

This moring it was fine. Now when I turn on my computer it tells me this-

Error: no such device: ee1ebf10-7f2b4baf-b283-281d867ce26.

grub rescue >

And that's it. No idea what to do. I did unplug my mobile HHD, restarted and it tells me to restart and plug in a proper boot device. Which makes no sense to me because the OS was installed on my SSD in the computer. I also can't remember which f key to press to get to my boot drive. I tried them all  none work. Ugh. 

Also, downloading 14.04 on to a thumb drive is not an option at the moment. =(

Please help, I use this computer for school and work and can't afford a new one.

Edit: I'm on my phone now.

---

### Post by yancek on 2014-07-17
> Error: no such device: ee1ebf10-7f2b4baf-b283-281d867ce26.

That's a UUID.  If you have looked in your grub.cfg menu, you will see a uuid for each system installed in the menuentry.  What is 'Mobile HHD'?  Some external device?  Were you booting to it?  What is the boot priority set to on your system?  Is the SSD set to first?  Is Ubuntu 12.04 the only system on the computer?

Do you have a Live CD of any Linux to use?  If you do run the following command to get the UUIDs and compare to the one above.

---

### Post by Andi_GreyScale on 2014-07-17
Sorry, I meant external hard drive but couldn't think of the right words at the time. 

I was not booting into it. My ssd, which I had listed as first in the boot list, is what I thought I booting into. Never had this issue before, and again, it was working fine this morning. But I can't double check my boot list because I can't remember which f key to press when first booting up. 

12.04 is the only system on my computer. 

I have zero idea what a uuid even is, I'm a novice user though I've been with Ubuntu since 11.10.

Sadly I don't have a live CD or thumb drive with Ubuntu on it. =(

---

### Post by at_first_light on 2014-07-17
My first guess would be that your OS resides on the internal drive, and the bootloader is on the external. If the external is connected can you boot?

---

### Post by Andi_GreyScale on 2014-07-17
Well, it gives me that error I posted in the OP when the external is connected.

Now I wonder if transferring whatever is on my external to a thumb drive could work. Just need to get a friend to do that for me.

---

### Post by Andi_GreyScale on 2014-07-18
Alright, the bootloader is not on my external drive. There was only a few files and they were videos and pictures.

---

### Post by Bashing-om on 2014-07-18
Andi_GreyScale; Hello,

IF you were booting with legacy MBR you would not find/see any of the boot files on the hard disk as those boot files reside in a protected area (1st sector of the hard drive). The secondary boot files could reside anywhere that the boot code from that 1st sector pointed too (the SSD even).
As you presently can not boot, the only viable thing you can do is to come up with a liveDVD(USB) to enable you to access these file systems and determine from the liveMedium what the booting situation is .

The anaolgy
[INDENT][INDENT]The HitchHikers Guide to the Galaxy ->
[INDENT][INDENT][INDENT][INDENT]never be without a liveDVD[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by yancek on 2014-07-18
Immediately prior to getting this error, did you make any change to system software or to your hardware?
You can try to check the boot priority in the BIOS to see if your internal is set to first.  When you see the first screen on boot, which usually shows a manufacturer logo, watch the bottom of the screen for the key to tap to enter BIOS and then use the keyboard arrow key to go to the Boot tab and check boot priority.  Getting any Linux Live CD so you can check the UUID would be helpful.

---

### Post by Andi_GreyScale on 2014-07-19
Strangely enough when I look for the key to press to get to my BIOS I get the normal manufacturer logo, but nothing in the bottom at all. Instead the little menu bar for my monitor pops up in the bottom right corner, no idea how to make it stop. I keep pressing each different F key, so far none work. 

I did not make any changes to my hardware or software lately. 

I think I can afford the Live CD of 14.04 so I think I'll order it.

---

### Post by yancek on 2014-07-19
You might be able to do an online search for the maker of the mother board or if it a major manufacturer like HP, Dell, Toshia, Lenovo, etc. they usually have a standard key to hit and they are not always an F key.  The first computer I had as a novice, I had to hit the Delete key to enter BIOS.

If you have access to another computer you can download the Ubuntu 14.04 and just burn it as an image to a DVD.

---

### Post by Andi_GreyScale on 2014-07-19
Ordered the Live DVD. Will get here hopefully by the 23rd. In the meantime I'll look for my computers books to see how to get to the BIOS.

---

### Post by Andi_GreyScale on 2014-07-19
Figured out how to get to my BIOS, was in the process of moving my ssd into the first slot when my cat shoved my hand and I accidentally clicked onto something else and now I can't get back to the BIOS at all, keeps telling me to reboot and select proper boot device or insert boot device in selected boot device and press a key. Even the normal logo startup isn't showing up any more. 

I am not happy about this. I don't know what I clicked, it happened so damn fast.

---

### Post by Andi_GreyScale on 2014-07-21
Alright, was able to get back to my BIOS and got the OS to boot. All fixed now!

---

