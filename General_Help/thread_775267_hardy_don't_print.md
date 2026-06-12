---
title: "hardy don't print"
date: 2008-04-30
forum: General Help
---

### Post by linuxted on 2008-04-30
I was hoping this issue would get fixed in hardy, but alas I still cannot get my printer to work.

Anyone have a workaround?

The printer is identified but the jobs just don't do anything.

Yes, the printer is powered on and the usb is connected to the computer.

Any diagnostics I could do please let me know and I'll provide the info

desperate

---

### Post by Ziggy72 on 2008-04-30
There are many issues with printers in linux. Some printers are well supported with drivers by their manufacturers - others are not. If you want anybody to give informed help you will have to supply, as an absolute minimum, the name and model of your printer. Searching the forums, while tedious, can sometimes be rewarding.

---

### Post by linuxted on 2008-04-30
> **Ziggy72 said:**
> There are many issues with printers in linux. Some printers are well supported with drivers by their manufacturers - others are not. If you want anybody to give informed help you will have to supply, as an absolute minimum, the name and model of your printer. Searching the forums, while tedious, can sometimes be rewarding.

hp photosmart7150 is the printer
I used to be able to go to System->Printer and enable it... that doesn't work anymore

---

### Post by linuxted on 2008-04-30
> **linuxted said:**
> hp photosmart7150 is the printer
I used to be able to go to System->Printer and enable it... that doesn't work anymore

bump


i'm desperate

---

### Post by natrixgli on 2008-04-30
I find it easiest to do this:

1) Open a terminal and display the last few lines of the print system's log file:

```
tail -f /var/log/cups/error_log
```

Then try printing something and see what if any error messages show up. If you get errors, paste them here. (or anything that pops up, really.)

The 7100 series should work ok. But the errors will help! 

Cheerio,

-n8

---

### Post by linuxted on 2008-05-01
> **natrixgli said:**
> I find it easiest to do this:

1) Open a terminal and display the last few lines of the print system's log file:

```
tail -f /var/log/cups/error_log
```

Then try printing something and see what if any error messages show up. If you get errors, paste them here. (or anything that pops up, really.)

The 7100 series should work ok. But the errors will help! 

Cheerio,

-n8

I get the following:

E [30/Apr/2008:22:27:30 -0700] CUPS-Set-Default: Unauthorized

Don't know what it means but it doesn't look good

Thank you for your help!

---

### Post by adonet on 2008-05-09
I've got a similair problem. In Gutsy my HP LAserjet4000 printer prints fine. Its connected to a sitecom printserver. In Hardy it doesn't

I got this message 
```

E [07/May/2008:23:29:20 +0200] Release-Job: Unauthorized
E [07/May/2008:23:29:26 +0200] PID 7563 (/usr/lib/cups/backend/lpd) stopped with status 1!
E [07/May/2008:23:29:26 +0200] [Job 32] Canceling job since it could not be sent after 5 tries.
E [07/May/2008:23:32:49 +0200] Purge-Jobs: Unauthorized
```

I don't know what to do except returning to Gutsy

---

### Post by foosed on 2008-05-09
Same is happening to me in ubuntu studio 8.04 with an HP Photosmart C5180. Had no prolems in gusty, didn't even have to install anything, it just worked.

---

### Post by linuxted on 2008-05-11
Ok, its been a while and I still have no printer.   I don't know how to say this without sounding whiny, but this is pathetic.   I could understand it if it was a new feature or an untried printer, but this *used* to work on previous versions of Ubuntu.

I'm desperate for help on this.   Any pointers on what to do would be greatly appreciated.

An OS that can't handle a printer is making me contemplate going back to Windows.  Sigh

---

### Post by linuxted on 2008-05-15
> **linuxted said:**
> Ok, its been a while and I still have no printer.   I don't know how to say this without sounding whiny, but this is pathetic.   I could understand it if it was a new feature or an untried printer, but this *used* to work on previous versions of Ubuntu.

I'm desperate for help on this.   Any pointers on what to do would be greatly appreciated.

An OS that can't handle a printer is making me contemplate going back to Windows.  Sigh

For anyone who is having similar issues, I see there is an "hpoj" package.  It didn't seem to help but two heads are better than one... maybe it will spark some ideas.

---

### Post by prostar on 2008-06-06
I've got to resurrect this thread...  This is a major issue.  I've searched many threads and not seen many solutions.  Previously this would relate to a permissions problem on /dev/usb/usb??? or something similar.  Now I am reading about "apparmor".  I don't know what it is, but it sounds like some kind of watchdog similar to MacAffee(sp?).  If something so major as to start blocking access to devices was going to be installed, it should have mentioned there may be some permissions to fiddle with.

If anyone knows what to do, I have an AMD 64, and Epson CX-4200 on USB that worked great 2 days ago on Gutsy...

---

