---
title: "Suddenly having dual boot issues Lubuntu and MBR legacy bios"
date: 2019-12-14
forum: General Help
---

### Post by fora-h on 2019-12-14
[FONT=&amp]Hello, I hope I can find the help here that I need with this issue -

For a week I had been booting into Linux (Lubuntu 18.04 permanent install on a super fast usb drive,  on a 2011 Windows 7 host machine.  (MBR,  bios). 

[/FONT][FONT=&amp]I had experienced a few  times since I began dual booting in this way, that the machine failed to boot, regardless of what system I was trying to boot into. No logo flashed up, just a black screen. I tried waiting for 15 minutes once, but the machine didn't manage to sort itself out. 
[/FONT]
[FONT=&amp][FONT=&amp]When this happens power light shows power is on. I can hear sounds of the system working. Then silence.[/FONT][/FONT]  

[FONT=&amp]
Each time it happened I had to power off using the power button. I tried removing the USB to see if this would at least help me to boot into Win 7,but it didn't. When powered up again still just a black screen.
[/FONT]

[FONT=&amp]I found a temporary fix (after shutting down, remove power cord and peripherals, remove battery, hold power button down 15 secs). I am not happy with the idea of continuing with this a temporary fix on a daily basis. 

I tried a fresh brand new USB with a different OS on it (Zorin) but that wouldn't boot either.

My first question is whether continuing like this could eventually permanently destroy the ability of my laptop to boot again?

[/FONT][FONT=&amp]Secondly, is there a way to fix the issue so the laptop always boots when I boot into the other OS?

Have stopped booting into Lubuntu for now, and Win 7 has been booting up easily. 

Sorry, no screenshots of partitioning. Have screenshot on hard drive, but forum asks for URL. I tried  drag and drop, but when I sent message, it failed security check.
[/FONT]

  [FONT=&amp]Although I have had some previous experience of dual-booting, best to treat me as a beginner, as I am a self taught home user regarding anything computer related.

Thank You
[/FONT]

---

### Post by yancek on 2019-12-15
> [FONT=&amp]For a week I had been booting into  Linux (Lubuntu 18.04 permanent install on a super fast usb drive,  on a  2011 Windows 7 host machine.  (MBR,  bios). [/FONT] 

I'm not sure I understand the above.  I would take that to mean you have Lubuntu installed on a physical USB drive by itself while windows 7 is installed on another drive since a default windows will not install to a usb.  Is that correct?  You also mention windows on "host" machine which might indicate you are using virtual software.  Which is it?  Also, what you are describing might be a hardware problem.  If you can boot Lubuntu (installed or from the install DVD/USB), go to the boot repair site at the link below and use the 2nd option described on the page to add the ppa, download and run it using the Create BootInfo Summary option only.  Do NOT make any changes and when it finishes, you will get a link which you can post here and that should give enough info so someone can make suggestions.

  [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

