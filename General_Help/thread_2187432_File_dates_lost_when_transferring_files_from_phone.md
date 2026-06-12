---
title: "File dates lost when transferring files from phone using Nautilus (mtp, usb)"
date: 2013-11-12
forum: General Help
---

### Post by ajw-free on 2013-11-12
**UPDATE 2 October 2015:   GREAT NEWS!  THIS BUG HAS FINALLY BEEN FIXED in time for UBUNTU 15.10.**
**                                         The gvfs package has been updated and contains a fix!  Timestamps are now preserved.**
**                                         See:  [https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/1175947](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/1175947)**

PROBLEM: file dates are lost when I copy files from my phone to my laptop using a usb cable..

DETAILS: 
I wish to transfer files (photos etc.) from my Samsung S4 phone to my Ubuntu 13.10 laptop (upgraded from Ubuntu 13.04).

If I plug in the usb cable, the phone is automatically detected as an mtp device (mtp://[usb:002,009]/) and I can browse the files on my phone using the file browser Nautilus. I can also see the correct file dates in Nautilus (for files located in the phone).

I am able to copy files to my laptop hard drive (using drag and drop or ctlr-cv), but all the original file dates are lost.

The original file dates are replaced with the current time of transfer. 
i.e. the dates on the files copied to my hard drive are the time of transfer.

I consider this to be a serious bug, as file dates should be preserved. 

Is there a fix or work-around for this problem? 

Is this just my Samsung S4 phone or are others experiencing the same problem?

UPDATE:  I have now checked the problem with a live CD distro of Ubuntu 13.10, and with Ubuntu 13.04, and the problem is still present.
I also tested with a Samsung S2 phone, and the problem is the same. 
I have also tested file transfer on a Windows 7 PC, and the problem is not present (i.e. With Windows, the file dates are preserved), and so I conclude that the problem is with Ubuntu.

On Ubuntu's Nautilus file browser,

If I right-click properties on the copied file, it shows two dates.  "Accessed" and "Modified". Both are set to the time of file copying.
If I right-click properties on the source file (stored in the phone), "Accessed: unknown" and "Modified" is the date of when the file was created.

I have placed a high res screenshot here:
[https://dl.dropboxusercontent.com/u/36840647/mtp%20screenshot/Screenshot%20from%202013-11-12%2021%3A59%3A18.png](https://dl.dropboxusercontent.com/u/36840647/mtp%20screenshot/Screenshot%20from%202013-11-12%2021%3A59%3A18.png)

The screen shot shows the contents of the phone on the right side and the properties of IMG_0786.jpg.  On the left side is shown the copied file and its properties.  Clearly the dates are different.

---

### Post by Lars Noodén on 2013-11-12
If you copy ctrl-c and paste ctrl-v the files from one Nautilus window to another, the original dates and times should be preserved.

---

### Post by ajw-free on 2013-11-12
> **Lars Noodén said:**
> If you copy ctrl-c and paste ctrl-v the files from one Nautilus window to another, the original dates and times should be preserved.

I tried using the ctrl-c ctrl-v method but the result is the same as when I use drag and drop.

i.e. the dates on the files that I copy to my hard drive from my phone are not preserved.

The file date (time-stamp) is changed to the current time at which the copy action takes place.

---

### Post by Lars Noodén on 2013-11-12
Strange.  I'm using Nautilus and both ctrl-c/ctrl-v and drag-and-drop preserve the file dates on the files I have tried.  What type of filesystem is your phone getting mounted as?  That might be it.  What about other methods does it preserve the dates if you transfer with rsync?

---

### Post by philinux on 2013-11-12
I thought the modified date wss preserved. Check in file properties.  However cp command has a preserve flag.

[http://askubuntu.com/questions/226033/how-can-i-preserve-file-modification-times-when-copying-to-a-nas](http://askubuntu.com/questions/226033/how-can-i-preserve-file-modification-times-when-copying-to-a-nas)

---

### Post by ajw-free on 2013-11-12
When I plug in my Galaxy S4 phone via a USB cable, it automatically  mounts and appears in Nautilus as an "mtp" type device.

I have edited my original post above to include some more information.
I have included a link to a screenshot which clearly shows the file date problem - please take a look.
I have placed a high res screenshot here:
[https://dl.dropboxusercontent.com/u/...%3A59%3A18.png]("https://dl.dropboxusercontent.com/u/36840647/mtp%20screenshot/Screenshot%20from%202013-11-12%2021%3A59%3A18.png")

I have also tested a Galaxy S2 phone, and it gives the same problem (i.e. file dates lost on transfer from phone to PC). 
I also tried the same with Windows 7, and the problem is not present (i.e. file dates are preserved).  I conclude that the problem is in Ubuntu.

---

### Post by Lars Noodén on 2013-11-13
You can check which filesystem is being used by your phone with [df](http://manpages.ubuntu.com/manpages/trusty/en/man1/df.1.html).

```

df -h | grep "^/dev/"

```

What does it say?

---

### Post by coffeecat on 2013-11-13
@ajw-free, I cannot reproduce your problem when I plug my Samsung Galaxy Ace GT-S5830 phone into my Ubuntu 13.10 system. Drag and drop copy from the phone to a folder in my home using Nautilus preserves the modified date and time.

However, with my Samsung Galaxy tablet, I do see what you see - modified date is changed to current when copied.

I agree with you - changing the date/time is not just a bug, it's data corruption. I'll do some more digging around to try to discover why I'm seeing this with one Android device and not another.

**EDIT:** Oops - it was obvious really. It seems my phone is being mounted in PTP mode, and my tablet in MTP. MTP capability is fairly new in Linux. It sounds as though it needs more work.

---

### Post by ajw-free on 2013-11-13
df -h | grep "^/dev/"
/dev/sda7        39G  5,9G   31G  17% /
/dev/sda5       775G  185G  551G  26% /home


The phone does not appear as a device on this list.
It has something to do with the fact that it is an mtp device (I am not a specialist in this).

According to this posting [http://askubuntu.com/questions/342319/where-are-mtp-mounted-devices-located-in-the-filesystem](http://askubuntu.com/questions/342319/where-are-mtp-mounted-devices-located-in-the-filesystem)

the mountpoints are in /run/user/$USER/gvfs/

I can see can my phones's presence via
ls -als /run/user/1000/gvfs/mtp\:host\=%5Busb%3A002%2C008%5D/Phone/

e.g.
ls -als /run/user/1000/gvfs/mtp\:host\=%5Busb%3A002%2C009%5D/Phone/DCIM/WIFISD/
total 10538
   0 drwx------ 1 user user       0 Nov  3 22:52 .
   0 drwx------ 1 user user       0 Nov  9 16:45 ..
5593 -rw------- 1 user user 5726647 Nov  3 22:52 IMG_0786.JPG
4946 -rw------- 1 user user 5063709 Nov  3 22:52 IMG_0787.JPG


Unfortunately any attempt to copy files using command line cp gives an error message.

e.g. 
cp -p /run/user/1000/gvfs/mtp\:host\=%5Busb%3A002%2C009%5D/Phone/DCIM/WIFISD/IMG_0786.JPG .
cp: cannot open &#8216;/run/user/1000/gvfs/mtp:host=%5Busb%3A002%2C009%5D/Phone/DCIM/WIFISD/IMG_0786.JPG&#8217; for reading: Operation not supported

Only Nautilus copy operations appear to copy the files, but do not preserve the original dates.
The strange thing is that one can actually see the orignal dates via Nautilus in the phone's memory (see my screenshot).
Somehow, they are not preserved in the file transfer.

This needs attention from a developer. It must be fixed asap.

---

### Post by ajw-free on 2013-11-13
> **coffeecat said:**
> @ajw-free, I cannot reproduce your problem when I plug my Samsung Galaxy Ace GT-S5830 phone into my Ubuntu 13.10 system. Drag and drop copy from the phone to a folder in my home using Nautilus preserves the modified date and time.

However, with my Samsung Galaxy tablet, I do see what you see - modified date is changed to current when copied.

I agree with you - changing the date/time is not just a bug, it's data corruption. I'll do some more digging around to try to discover why I'm seeing this with one Android device and not another.

**EDIT:** Oops - it was obvious really. It seems my phone is being mounted in PTP mode, and my tablet in MTP. MTP capability is fairly new in Linux. It sounds as though it needs more work.

@coffeecat.   I'm glad that someone else is able to reproduce the problem.

Yes- it is data corruption, and needs to be fixed by a developer asap. 
I'm not sure how/where to report it?

The problem is definitely related to MTP. This bug was present in Ubuntu 13.04 too.

Android smart phones are now widely used and the usb transfer protocol is changing to MTP (as opposed to "usb storage"). Data transfers need to be reliable. It is surprising to me that this bug was not fixed shortly after 13.04 was released.

---

### Post by coffeecat on 2013-11-13
It would be an upstream bug, but whether in Nautilus, or gvfs or the mtp packages I wouldn't know. Launchpad would be an appropriate place to report a bug affecting Ubuntu though:

[https://bugs.launchpad.net/ubuntu/](https://bugs.launchpad.net/ubuntu/)

I haven't been able to find anything related to this in Launchpad, so it's probably worth reporting there. Here is a bug-reporting guide for Launchpad:

[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

---

### Post by diaz8 on 2014-03-07
Hi, 

The bug is reported at: 
[https://bugs.launchpad.net/bugs/1175947](https://bugs.launchpad.net/bugs/1175947)

but i don't think the problem will get solved soon. 

Regards.

---

### Post by Vaphell on 2014-03-07
i don't have any device to test the issue, but if you can get original timestamps in command line, writing a script that copies stuff and preserves/restores the ts on these files should be relatively easy.
then it could be GUIfied if you don't feel like dropping to terminal.

---

### Post by AlbertP on 2014-08-17
Copying with cp -p in the terminal works for me, that preserves the file date.
Ubuntu 14.04-based Linux Mint 17, using MTP on a LG Optimus L5 II phone.

---

### Post by darkhole on 2015-03-29
I had this problem a few months ago, but today I test it, copy some file from phone (Xperia Z1 C6903 Android version official 4.4.4) to Ubuntu (14.04) and the date of files was preserved and also the EXIF info. Can you test again?

---

### Post by vivideo on 2015-06-28
Same here. I connected my HTC One M8 to my Ubuntu 14.04 system. Although I could read all content, the timestamp gets lost when copying with Nautilus/Nemo. I wonder how to use the cp-command with the MTP device '[usb:002,012]' as source location.

Any ideas?

Thanks!

---

### Post by ajw-free on 2015-10-02
**UPDATE 2 October 2015:   GREAT NEWS!  THIS BUG HAS FINALLY BEEN FIXED in time for UBUNTU 15.10.**
**                                         The gvfs package has been updated and contains a fix!  Timestamps are now preserved.**
[B]                                         See:  [https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/1175947](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/1175947)


[/B]I recently upgraded from Ubuntu 15.04 to Ubuntu 15.10 beta 2. After doing a package upgrade on 30 September 2015 I noticed that the gvfs package updated.


 I have now tested transferring files via USB from my Samsung Galaxy  Note 4 phone to my Ubuntu 15.10 desktop and I am pleased to report that  the timestamp  is correctly preserved.


 I should add that it has been a very frustrating long wait (over two  years), for this critical bug to be fixed.  Such a long delay is  potentially damaging to Ubuntu as bugs of this nature should receive top  priority.  Mobile phones and tablets are now a way of life and it is  simply unacceptable to lose the date information on a file that is  transferred from a phone to a PC - it is a form of "data corruption".


 I am grateful to the software developers who fixed the bug in time for the release of Ubuntu 15.10.

---

### Post by vivideo on 2015-10-02
> **ajw-free said:**
> **UPDATE 2 October 2015:   GREAT NEWS!  THIS BUG HAS FINALLY BEEN FIXED in time for UBUNTU 15.10.**
**                                         The gvfs package has been updated and contains a fix!  Timestamps are now preserved.**
[B]                                         See:  [https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/1175947](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/1175947)
[/B]

Thanks for sharing. Great news, but late. For me, FTP bypassed this annoying bug. Maybe I'll stay with Filezilla to get the job done 8-)

---

