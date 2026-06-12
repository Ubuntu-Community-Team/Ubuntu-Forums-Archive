---
title: "Computer won't boot from HD"
date: 2007-02-26
forum: General Help
---

### Post by katch22 on 2007-02-26
My problems started after trying to install Ubuntu, but I am not actually sure they are Ubuntu related. Heres the story... I hooked up an old 12GB HDD as slave to my winxp machine to make sure there weren't any old files on it I wanted, that went fine. Then I took out my windows HDD and put in just the 12GB one as master. I launched Ubuntu from the LiveCD and played around few minutes and then decided to go ahead and install it to the HDD. Everything seemed to go smoothly. When the install program asked, I chose to format the drive and did everything it suggested. At the end, it pops out the cd and tells me to reboot. Upon rebooting I get "Boot Disk Failure". Of course I make sure the BIOS sees the HDD and it is primary master. Hrmm... I am figuring at this point Ubuntu maybe isn't all I had hoped it would be. So I figure I will come back to it later since I need to get some things done online. So I take out the HDD I just tried to install Ubuntu on and plug my winxp HDD back in.. and... SAME THING! 

OK, I have since determined that my computer will not boot from any HDD but will boot from any bootable cd (winxp or ubuntu livecd) or floppy... Also, if I boot from winxp cd and run the recovery console (DOS prompt basically), I can see my HDD and the files on it. I also took the HDD that I had installed Ubuntu on and threw it in another system and it worked! Also my winxp HDD boots on another system! So the HDD's aren't the problem. 

My BIOS detects the HDDs correctly, and of course I set it to boot from HDD first but it always gives me Boot Disk Failure when I try to boot from HDD. Yet these same HDDs boot in another system. At this point I have even tried flashing my BIOS to no avail. I have built and maintained many, many pc's over the last ten years and have seen (and solved!) a lot of strange problems but this really has me stumped. 

Anyone here have any idea what the problem could be?? Like I said, it doesn't seem like Ubuntu could have caused this problem, but since the problem started after trying to install it I thought I would ask here. Much appreciation if anyone can shed some light on my problem!

---

### Post by chewearn on 2007-02-27
Don't know whether it is related to your problem, but I have encountered boot failure on an old PC; after hours of investigation, I finally figured out that it is the way the IDE cable is connected.  

You see, the old PC is a desktop type, rather than a tower.  Due to the location of the harddisk bay, the neatest way is to plug the IDE cable by the middle connector to the motherboard.  Normally, you would want to use one of the end connector.  When I got the old PC, the previous owner has somehow use this configuration and I did not think to change it.

---

