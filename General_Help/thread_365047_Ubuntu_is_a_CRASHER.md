---
title: "Ubuntu is a CRASHER"
date: 2007-02-19
forum: General Help
---

### Post by newpants2003 on 2007-02-19
i had 6.10 for half year. (using ubuntu since 5.04)

recently the system become seriously unstable!!!

most frequency crashing software:
gnome-panel  (crash for no reason, some times keep crash and reload for 5,6 times)
firefox (crash for no reason, i did type this twice, because it crashed at the first time doing it)
kaffeine (just crashed when playing someting)
system monitor does not start.
whole system freeze, dont know what is wrong.
etc...
this morning when i turn on computer, it doesnt start at all, right after the ubuntu log show up, it tell me something ATA not transformable (i dont remember exactly) i was in the middle of my work, so pissed off. i just keep going reboot, something magic happened, the system does boot again just like nothing happed. 

the next time when i boot the thing (half hour later, because the system freeze) it tell me the there is a error in the file system and check forced , and failed. mount the file system into read-only mode. run the fsck manually, did not solved the problem entirely.

i spent so much time for config and install software, i am so busy everyday. i dont feel i want to do all over again. VERY disappointed for ubuntu.

---

### Post by rsambuca on 2007-02-19
Kinda sounds like failing hardware to me.:(

---

### Post by PrinceArithon on 2007-02-19
That sucks....for me I get random crashes from different programs...99% of the time they are from programs I rarely use.

I'm sorry to hear it didn't work for you.

I'll give you some information that might make you feel a little calm...even though I know you don't want to have to install all the software again....so here goes the information.

Next time you reinstall Ubuntu, if you reinstall, it will install onto your system differently.  Everytime you install an OS it will install differently and never the same on your system...so you may get a great install next time.  The same goes with Windows...I have installed Windows XP a bunch of times on different computers, and my own.  Sometimes it installed like gold, and other times it installled like a disease infested homeless man with a stomach full of cheap wine.  So don't feel too bad...sometimes you just get a bad install....

---

### Post by RAOF on 2007-02-19
It's possible your hardware is dying.  Back up your data!

Things you can test include a memtest from the Grub menu.

---

### Post by gradedcheese on 2007-02-19
> 
Everytime you install an OS it will install differently and never the same on your system...so you may get a great install next time.

I would argue that, given the same parameters, software should be deterministic :)  That is, if you installed, then reinstalled, each time you should have the exact same result.

I also  think this guy's hardware is failing.  Perhaps this would be a good time to do the memtest (overnight) and maybe an fsck to check the disks out.

---

### Post by aberry5555 on 2007-02-19
It sounds to me, too, like either your hard-drive or RAM is failing, although I think it's more likely hard-drive as dodgy RAM tends to simply crash your computer or chuck a zillion error messages as you reach the damaged sector. A fairly simple diagnostic test to try would be to find an old computer, take your hard-drive out of your PC and stick it in the old one. If you get the same error messages then it could very well be your hard-drive, and if you don't get any error messages then you can be sure it's part of your PC. If you get the same errors use the Live CD to back-up your data and try formatting the whole disk and reinstalling, if it's still dodgy chuck it in the bin and buy a new disk :S

Good luck!

---

### Post by kerry_s on 2007-02-19
> **newpants2003 said:**
> i had 6.10 for half year. (using ubuntu since 5.04)

recently the system become seriously unstable!!!

most frequency crashing software:
gnome-panel  (crash for no reason, some times keep crash and reload for 5,6 times)
firefox (crash for no reason, i did type this twice, because it crashed at the first time doing it)
kaffeine (just crashed when playing someting)
system monitor does not start.
whole system freeze, dont know what is wrong.
etc...
this morning when i turn on computer, it doesnt start at all, right after the ubuntu log show up, it tell me something ATA not transformable (i dont remember exactly) i was in the middle of my work, so pissed off. i just keep going reboot, something magic happened, the system does boot again just like nothing happed. 

the next time when i boot the thing (half hour later, because the system freeze) it tell me the there is a error in the file system and check forced , and failed. mount the file system into read-only mode. run the fsck manually, did not solved the problem entirely.

i spent so much time for config and install software, i am so busy everyday. i dont feel i want to do all over again. VERY disappointed for ubuntu.


Sounds like your hard drive is about to die, try opening your computer up and disconnect the hard drive(power and ide) for a couple of minutes then plug it back in, now see how long it lasts. If that don't do nothing check your ram, if you have more than 1 stick switch them around. I just had a similar experience this mourning, turns out my power connector is just so lose that it was losing power, i plugged in a different 1 and it was good to go.

---

### Post by newpants2003 on 2007-02-19
after running fsck in the recovery mode, the Grub died...
cant even boot to windows now.

what's best way to make back up, min my reinstall work.

---

### Post by aberry5555 on 2007-02-19
I think if you cant even get to windows then you might not be lucky enough to recover any data.... try booting in to the live cd and see if it can read from the hard-drive, if not then Im afraid your data may be permanently lost.

---

### Post by newpants2003 on 2007-02-19
i just did, the hard drive for linux is crashed. only swap left, the / become unknown partition.
looks like i dont have anything to backup now... that make me so sad.
i dont use windows for quite a while, every thing is on linux. cant believe what just happened.

---

### Post by Resurrection on 2007-02-19
I'm sorry, but I believe everyone is correct in that it is your hardware that has failed.  Most likely either harddrive(s), RAM, or motherboard.  I recommend before you do anything else, take the affected hard drive(s) out and try to put them in a different computer.  Don't try to boot them, just add them as a second drive.  If the hard drive is physically working, you should be able to access them.  For any Windows partitions you have you should be able to just plug the drive in and Windows should be able to access the partitions.  For Linux partitions, you will have to access them via the Live CD.  

I am not saying that Ubuntu is absolutely not to blame, but this seems that you have hardware issues.  Even when software works perfectly, you still have to back up your data.

---

### Post by newpants2003 on 2007-02-19
just did a fresh install on the same hard drive, doesnt give me any error.
but the gnome-panel crash problem quickly show up again.

---

### Post by aberry5555 on 2007-02-19
Unlucky :S the only thing I can suggest looking in to would be to try and find some file recovery software, as it sounds like the MFT is now corrupt. look for something called Stellar Phoenix (not free) though Im not sure it will read linux partitions. Just goes to show what happens if you don't back up, I know how annoying it is it's happened to me a few times! Good luck trying to recoupe any data you can.

**edit**

That part was meant for the previous post, unfortunately if you are getting the same errors coming back again then I'm pretty sure your hard drive is corruping itself, which means that there is a physical fault with it. I think you need to take it back to the shop you bought it from if it's less than three years old or, if not, you need to buy a new drive.

---

### Post by newpants2003 on 2007-02-19
it crashed again. it does looks like something wrong with the hard drive, my windows and another ubuntu is fine on another hard drive.
but why there is nothing wrong when i format and install? i did format the hard drive in NTFS, checking by windows, looks ok too.

---

### Post by aberry5555 on 2007-02-19
maybe it was the MFT being corrupted. If your master file table gets corrupted it can prevent alot of files working properly, and corrupt more data, on every partition. presumably now you re-did the whole hard drive it rebuilt the MFT, your hard-drive might be OK, but for now I would test it for a few days and not put anything important on it.

---

### Post by newpants2003 on 2007-02-19
what may cause the problem? i didnt touch the hard drive at all since installed. the ubuntu works very nice in the beginning, feel like more update installed, more unstable and slow it got to.

---

### Post by PrinceArithon on 2007-02-19
> **gradedcheese said:**
> I would argue that, given the same parameters, software should be deterministic :)  That is, if you installed, then reinstalled, each time you should have the exact same result.

I also  think this guy's hardware is failing.  Perhaps this would be a good time to do the memtest (overnight) and maybe an fsck to check the disks out.



Yeah, from the way that the thread went it definitely seems the hardware is dying out.  LOL

I still disagree with you, about the OS being deterministic.  You have to remember that when you are loading things, especially something big like an OS, it runs the chance of missing something, or some of the data not transferring right.  After all data transfer is a bit of a crap shoot sometimes, especially with very high volumes.  So the thing is, it might not all load right or the same way as the last time.  Therefore it ends up being a little different each time.  

Still it will basically work the same each time, you just may have different problems at times.

---

