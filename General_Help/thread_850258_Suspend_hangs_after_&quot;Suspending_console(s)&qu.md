---
title: "Suspend hangs after &quot;Suspending console(s)&quot;"
date: 2008-07-05
forum: General Help
---

### Post by Petroy on 2008-07-05
When trying to suspend my computer into RAM, the system hangs after the message "Suspending console(s)". Then I have to press the reset button on my computer's front in order to get back into Ubuntu. I have read several pages about that problem across the web, but I could not find anything that comprehendibly told me what to do.

Could someone please help me?

---

### Post by user17 on 2008-07-07
I seem to have exactly the same problem and have looked all over the place. Someone fixed this bug by reverting to an older kernel version, but doing so apparently disabled various applications.

Under Gutsy, I fixed my suspend problem (different symptoms) by following [these]("http://ubuntuforums.org/archive/index.php/t-350265.html") instructions, but now that I've upgraded to Hardy, I'm stuck!

EDIT: My system log in Hardy revealed a problem with my bcm4318 wifi card installation. The instructions at linuxwireless helped me to partially fix it, and after that my computer would suspend! It still won't resume afterwards -blank screen- but that's a different problem...

---

### Post by Petroy on 2008-07-14
Thank you very much. I seem to have had a similar problem. After installing the firmware as described at linuxwireless.org my computer no longer hangs while suspending.

Nevertheless, I now have another issue with suspending. It is caused by my second hard drive.
The kernel log says:

```
Jul 14 20:23:43 julian-desktop kernel: [  108.570098] PM: Entering mem sleep
Jul 14 20:23:43 julian-desktop kernel: [  108.570100] Suspending console(s)
Jul 14 20:23:43 julian-desktop kernel: [  108.570128] sd 4:0:1:0: [sdb] Synchronizing SCSI cache
Jul 14 20:23:43 julian-desktop kernel: [  108.570310] sd 4:0:1:0: [sdb] Stopping disk
Jul 14 20:23:43 julian-desktop kernel: [  108.710069] ata5.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Jul 14 20:23:43 julian-desktop kernel: [  108.710074] ata5.01: cmd e0/00:00:00:00:00/00:00:00:00:00/b0 tag 0
Jul 14 20:23:43 julian-desktop kernel: [  108.710075]          res 51/04:00:00:00:00/00:00:00:00:00/b0 Emask 0x1 (device error)
Jul 14 20:23:43 julian-desktop kernel: [  108.710077] ata5.01: status: { DRDY ERR }
Jul 14 20:23:43 julian-desktop kernel: [  108.710078] ata5.01: error: { ABRT }
Jul 14 20:23:43 julian-desktop kernel: [  108.710091] sd 4:0:1:0: [sdb] START_STOP FAILED
Jul 14 20:23:43 julian-desktop kernel: [  108.710092] sd 4:0:1:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Jul 14 20:23:43 julian-desktop kernel: [  108.710094] sd 4:0:1:0: [sdb] Sense Key : Aborted Command [current] [descriptor]
Jul 14 20:23:43 julian-desktop kernel: [  108.710097] sd 4:0:1:0: [sdb] Add. Sense: No additional sense information
Jul 14 20:23:43 julian-desktop kernel: [  108.710100] suspend_device(): scsi_bus_suspend+0x0/0x80 [scsi_mod]() returns 134217730
Jul 14 20:23:43 julian-desktop kernel: [  108.710144] Could not suspend device 4:0:1:0: error 134217730
Jul 14 20:23:43 julian-desktop kernel: [  108.710152] Some devices failed to suspend
Jul 14 20:23:43 julian-desktop kernel: [  108.710428] PM: Finishing wakeup.
Jul 14 20:23:43 julian-desktop kernel: [  108.710429] Restarting tasks ... done.
```

The system will stop the suspend process immediately and display the resume login screen.
After disconnecting the second hard drive (sdb, as mentioned in the kernel log) from the mainboard the system suspends perfectly.
Does anybody know how to fix that problem?

---

### Post by rfm33428 on 2009-03-22
I have the same error on my system, error 134217730.  Turns out that there was a drive that ubuntu couldn't put on standby.  Probably because it wasn't mount.  Might do the same thing for a partition too, I'm not sure.  In my case, it was the drive.

Once I disconnected the drive, Ubuntu's suspend worked great.  I use that drive for the 'pagefile' in WinXP.  Even though I don't use that drive for anything else, I will have to mount it so I can have my suspend feature working in Ubuntu & use it for my 'pagefile' in WinXP.


I suggest mounting all drives that Ubuntu doesn't recognize.  That screen with the error message & the message above it kind of led me to suspect that it was a drive issue.

It helped me & I hope it helps you too.:popcorn:

---

### Post by rfm33428 on 2009-03-22
I take that back, so sorry.  It was a drive issue though.  For me it was an old Seagate drive that didn't support power saving features.  Whether it was mounted or not, well.......was an error on my part.  I should have given it more thought before I posted.   I went through a lot before actually solving the problem I had.   

Still, I hope this helps.

---

