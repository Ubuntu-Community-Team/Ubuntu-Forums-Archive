---
title: "Can't reload Ubuntu from USB memory stick"
date: 2017-03-05
forum: General Help
---

### Post by andy-kay on 2017-03-05
I'm running Ubuntu on a desktop computer but updates keep giving me a package download failure message, so I decided to re-install Ubuntu.

I downloaded the ISO file and copied it to a USB memory stick, left the stick in the port, and restarted the computer.

When the computer came back up it showed a blank screen and never moved on.

Am I doing this wrong? Any advice would be greatly appreciated.

---

### Post by Geoffrey_Arndt on 2017-03-05
On your running copy of Ubuntu,  if you're getting package download errors, that is usually an easy fix.     I would suggest to go into your "Software & Updates' and select a different server (in the servers window, choose other, select best server) . . to try the downloads from (as an initial test if that is the issue).

---

### Post by oldfred on 2017-03-05
How did you copy ISO to flash drive?
You do not copy flash drive, but have to use an installer that formats flash drive, extracts ISO and adds a boot loader.

       Lots of info on USB boot for installing
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
Also:
[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)
[https://wiki.ubuntu.com/Win32DiskImager/iso2usb](https://wiki.ubuntu.com/Win32DiskImager/iso2usb)

---

### Post by andy-kay on 2017-03-06
Thank you Geoffrey. I've fixated on a reload now but I'll bear your comment in mind for future reference.

You have identified my error thank you **oldfred**. 
I've now created a startup disk on the flash drive, 
but when I restart using this drive I get the error message "not a COM32R image" repeating every few seconds.

---

### Post by opsusec on 2017-03-06
In all honesty, I would have verified signatures and keys before I installed anything on my system.

Don't forget, there's always an option that's relatively inexpensive, to order the live cd delivered to you! I haven't run into any issues in the past four years.

---

### Post by oldfred on 2017-03-06
Try typing help, the enter.
[https://ubuntuforums.org/showthread.php?t=2249701](https://ubuntuforums.org/showthread.php?t=2249701)

What tools/method did you use to create live installer?
Some work better than others. And may depend on version you end up using.

---

### Post by sudodus on 2017-03-06
> **andy-kay said:**
> You have identified my error thank you **oldfred**. 
I've now created a startup disk on the flash drive, 
but when I restart using this drive I get the error message "not a COM32R image" repeating every few seconds.

This looks like a known bug that affects some tools for installing linux distros to USB drives.

- Which version of Ubuntu are you trying to install (name of the iso file)?
- From where did you download the iso file?
- Which tool did you use? 
- Did you check with md5sum, that the downloaded iso is good (that the download process was successful)?

I suggest that you try a ***cloning*** tool: mkusb in linux or Win32 Disk Imager in Windows according to the links already given by *oldfred* in post #3.

---

### Post by Geoffrey_Arndt on 2017-03-06
A quick workaround is by pressing the tab key . . then inputting the first or second text option (like "live32, live 64" or something close to that).

Probably the safest & easiest tool I've come across to make the live usb is:   [https://etcher.io/](https://etcher.io/)

---

### Post by andy-kay on 2017-03-07
> **oldfred said:**
> Try typing help, the enter.
[https://ubuntuforums.org/showthread.php?t=2249701](https://ubuntuforums.org/showthread.php?t=2249701)



Cool! Ubuntu is loading from the memory stick!
Thanks for your help **oldfred**, and thanks to everybody else that commented.

---

### Post by oldrocker99 on 2017-03-07
Your question has been answered, so please mark this thread as [SOLVED] using the Thread Tools at the top of the thread.

---

### Post by andy-kay on 2017-03-07
> **oldrocker99 said:**
> Your question has been answered, so please mark this thread as [SOLVED] using the Thread Tools at the top of the thread.
Ah... that's where it is... I looked for it but obviously didn't look hard enough.

---

