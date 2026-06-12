---
title: "Ubuntu 17.04 64-bit randomly locks up"
date: 2017-10-10
forum: General Help
---

### Post by noob2linux2 on 2017-10-10
Ubuntu 17.04 randomly locking up

First off I am sorry if this is in the wrong section. I am new to linux. I didn't know if this should be in hardware or installation or new to Ubuntu. So I settled on General Help. If this should be in another section please move it there.

I am trying to build a basic computer that will be a media center. A computer connected to my TV running Ubuntu and Kodi with a couple of hard drives for media (movies, tv shows, music, etc).

The computer has:

new case
new motherboard: ASRock AB350 Pro4 AM4 ATX AMD Motherboard
new CPU: AMD Ryzen 3 1200 3.1GHz Quad Core AM4 Boxed Processor with Wraith Stealth Cooler
new RAM: 2 4GB modules (don't have the exact model with me)
new HD: Toshiba P300 1TB 7,200 RPM SATA III (for OS)
new network card: Intel EXPI9301CT Gigabit PCIe X1 Adapter (the one on the motherboard didn't work with the Live USB (no driver))

existing 500 watt power supply
existing pci2 video card (but I'm not running the proprietary software for it).

I am running Ubuntu 17.04 64-bit.
I do not have the kernel version with me (I'm at work) but did do a full update this morning (the kernel was updated).

1.5 GB boot partition
75 GB root partition
rest of HD (800+ GB) for home partition

I currently have one other hard drive connected. I have disconnected that hard drive (both power and SATA) and the problem still occurs. I will disconnect if necessary if I need to run any tests/scripts/etc.

I don't know if all of that is needed or not but I thought better safe with regards to providing it.

The installation went fine. I have updated everything (including the BIOS for the motherboard). It starts and runs fine for hours. Then it will randomly just lock up. Sometimes I can still move the mouse but clicking opens nothing. When this happens the only resolution is to reboot the machine.

I am totally new to Linux. Is there anything I can run that will tell me what is happening when this happens? A log file or something that I can have created/create that will output where the problem may be? I am really hoping I do not have to return the new stuff and get different hardware. I am not a hardware person and had to pay someone $75 to put all of this together for me. I am hoping a repeat is not necessary.

Any help would be really great. Thank you.

---

### Post by jim38 on 2017-10-10
You could go to var/log/syslog  then open the syslog . It will open with a text editor then "search" that file  for errors, it will have timestamps with the date and time 
If you can remember the time the computer locked up look in that area for errors. It might say something like "dump stack" , just an idea? not sure

Also,

Does the computer boot back up after reboot or does it get stuck looking for the hard drive, it might say something like "insert boot disk...." I can't remember for sure
Mine had a problem with the SATA wire not plugged in very good to the hard drive

---

### Post by noob2linux2 on 2017-10-10
jim38 -

Great timing. I just created a pastebin account and pasted the output from when I restarted this morning (before going to bed but after it crashed while I was sleeping). I just got hoome about an hour ago and restarted it. I had found the /var/syslog entry in one of the posts I read today. I have pasted it to pastebin. I included everything from the restart this morning until when I restarted it about an hour ago. Because when I got home tonight it was locked up again. To my completely uninformed/inexperienced mind it all looks like Greek... unless you speak Greek, then it looks like Gaelic or something.

Rebooting solves the problem until the problem decides it has rested enough and wants to play again. Rebooting goes normal. The only strange thing (and this is not consistent) is that sometimes I power off and it boots right into the desktop (which it should do as I have auto login enabled). But sometimes it asks for my password (likes it's coming out of screensaver or something).

Here is the link to my pastebin: [https://pastebin.com/nxDQd3fN](https://pastebin.com/nxDQd3fN)

Thank you for your help. Any additional information I can provide please let me know. 

Stacer does show one crash report: _lib_systemd_systemd-resolved.0.crash

And the video card I am using (I have enabled proprietary drivers) is NVidea GK 208 GT 710B using driver: NVidea binary driver version 375.66

Thank you again.

---

### Post by noob2linux2 on 2017-10-11
Quick update. I mentioned in my previous post that last night it was locked up when I got home. I restarted and tried using the Proprietary driver for the video card. That apparently made no difference. It was locked up again this morning. So I guess we can remove that from the mystery that is the random lock ups.

Would downgrading to 16.04 be a potential fix? Or is there something else going on?

Thank you again anyone who can offer some assistance.

---

### Post by ian-weisser on 2017-10-11
You need *last night's* syslog, not today's after-reboot and after-daily-logrotate.

Check your timestamps carefully, then look for the syslog from overnight (hint: syslog.1)

EDIT: Reminder - syslog rotates every 24 hours. It's based on clock time. Occasionally logrotate happens to coincide with a poweron or reboot, but don't get confused by coincidence.

If you (unwisely) decide to give us the entire log, please indicate the time at which you believe the problem occurred.
Life is too short for us to try to read everything for you.

---

### Post by noob2linux2 on 2017-10-11
OK. Well, it was off this morning and I just restarted it. I will try to see if I can find anything.  I just checked after reading your post. The syslog right now starts from when I just started the computer.

I am pretty sure it will do it again tonight. I will just keep using it until after midnight and then if it crashes during the morning before I go to work I can grab the syslog then. Unless it locks up while I am using it.

Thank you for the information. It is very much appreciated.

---

### Post by jim38 on 2017-10-12
noob2linux2,
Your pastebin link doesn't work anymore, I looked at it the other day and saw a high cpu usage with [I]hugepaged. 
[/I]Maybe this is were it locked up? What are you doing when it locks up?
 
There are some apps out there that you can put on your desktop that will show all the processes and cpu usage in real time
like  the "Conky" app might help.

---

