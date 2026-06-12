---
title: "Computer won't boot up on restart (New Dell running Ubuntu 14.02 solo)"
date: 2015-03-14
forum: General Help
---

### Post by Rick_Smith on 2015-03-14
Bought a new Dell Inspiron 3000 about a month ago. Of course it came with win8. Turned of secure boot, turned on legacy used ubuntu live cd erased win and loaded ubuntu (14.02 LTS) just fine and ran without a hitch. About a week ago I did a restart and during reboot it just went dead. The light indicating the computer was on was lit but there was no sound coming from the cpu and it didn't do diddly. Turned off the power hoping it would reboot and it did. Didn't think any more about it. Did another restart today and it did the same thing and continues every time I do a restart. I have to turn off the power and turn it back on to get it to boot up. 

Tried shutting it down and turning back on and it booted, crashed and gave an error report but started up again on its own. The error report was way over my head, could not be copied and pasted and was too damn long to write down. It did say to upgrade libfreestyle6 which I did through the command line. Didn't change a thing. I am up to date on security updates, have not loaded any weird software not in the software center other than themes and icons from noobslab. I did that on the second day and it didn't affect the system so I don't think that is the cause. And before anybody brings up the not so helpful point that I should have bought a computer with linux already loaded, I realize that, lesson learned, let's not go there. I hope this is not Dell pulling some crap, since they are Microsoft's bitch now, making it very difficult to run something other that Windoze. :mad: The system runs fine as long as I don't restart which is really not an option.

Anybody have an idea what is going on? Why has it worked for about a month and just started pulling this crap? Hope I have provided enough info. My undying gratitude to anyone who might have some idea what is happening.

---

### Post by pmi2 on 2015-03-14
> **Rick_Smith said:**
> ... before anybody brings up the not so helpful point that I should have bought a computer with linux already loaded...Not really, IMO.  More to be learned by choosing the linux flavor you like, and installing it yourself from a live CD.

Have you tried putting your Ubuntu live CD into the DVD drive, and then clicking restart?  In other words, restarting the way u usually do, but _from a live CD_ (or any other bootable media).

If you can restart to some removable media (CD, DVD, USB device), but not to your hard disk, I would try some version of Boot-Repair.

> [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
(since you have a recently bought system, note the directions for computers with EFI on the above page)

---

### Post by Rick_Smith on 2015-03-14
First off, pmi2, thank you for responding and making the suggestion you did. It got me started on the right track.
I downloaded and ran boot repair.
The message after running went much like this: the boot files of the OS (14.02) are far from the bios and they may not be detecting them. We created a /boot partition (EXT4,>200MB, start of the disk). We used gParted.
Now when rebooting the computer will show the screen where you choose from what to boot up from, like if you had a startup disk or flash drive but it only stays there a couple of seconds then boots right up into the OS. That's weird but it works now. I can restart the system. I'm going to call this solved for the time being and want to thank you again.

---

### Post by pmi2 on 2015-03-14
You are welcome.
> **Rick_Smith said:**
> ...Now when rebooting the computer will show the screen where you choose from what to boot up from, like if you had a startup disk or flash drive but it only stays there a couple of seconds then boots right up into the OS. That's weird ...I believe you can turn that off.  Assuming that when you enabled "Legacy", you got a traditional BIOS configuration, there will be some options in the BIOS Boot menu that allow you to tweak how the computer boots, and what is displayed on the screen while POST (Power On Self Test) is running.  On a modern and fast computer, POST runs for only 3~4 seconds, so that may be what you are seeing.  The Dell Support website has some information that may be useful on UEFI and your BIOS.

---

