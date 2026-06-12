---
title: "ripit4me crashes after clicking wizard button"
date: 2006-10-31
forum: General Help
---

### Post by PapaWiskas on 2006-10-31
I know a lot of people supposedly have ripit4me working in WINE.

I have a few apps working just fine in WINE, DVDDecrypter, DVDShrink, PGC Edit, to name a few.  

But ripit4me loads fine, but when I click on the wizard button, ripit4me disappears, like it does in windows, and what should happen is DVD Decrypter should be loading up and appear, but it dont, everything just goes away.

I have tried various settings and can not figure out what I am doing wrong, any help would be appreciated.

Thanks.

---

### Post by PapaWiskas on 2006-11-01
bump...

---

### Post by Trespasser on 2006-11-02
I have struggled with RipIt4Me in Wine for months now with little success. RipIt4Me opens fine but when it attempts to create the PSL2 file it suddenly crashes 50% of the time. The times when it does create a PSL2 file and calls DVD Decrypter the resulting PSL2 file is incomplete (in other words RipIt4Me didn't read the whole disc when it created the PSL2 file). For example under Windows a DVD movie I used with RipIt4Me found 32 suspect areas but under Wine it found only 3. There is obviously a lack of proper communication between RipIt4Me and drive D (my DVD+RW) because of the malformed PSL2 file. There is also a lack of proper communication between RipIt4Me and DVD Decrypter because if you specify Movie Only in RipIt4Me that is not what loads up in DVD Decrypter (but that could be due th the malformed PSL2 file). I submitted RipIt4Me to AppDB at WineHQ yesterday hoping they might find a solution for it.

You do have mfc42.dll in your System32 folder?

Have a good day, everyone.

---

### Post by PapaWiskas on 2006-11-02
Well you are getting further than I get, I cant get it to bring up dvddecrypter, even though I can run decrypter as a stand alone app just fine.

And yes I do have the mfc42.dll in my system32 folder.

I dont understand how people can say they are running ripit4me just fine, but yet I cant find any documentation on it at all anywhere on how to set it up.

---

### Post by Trespasser on 2006-11-02
Do you have the Default Configuration set up as Win 2000 or Win XP or Win 2003 in winecfg? You also need to open up the RipIt4Me.ini in /home/user and fill in the path to FixVTS.exe. I created a folder titled RipIt4Me, placed RipIt4Me.exe and FixVTS.exe in it, then moved the folder to /home/user/.wine/drive_c/Program Files. I made a link for RipIt4Me (right click on RipIt4Me.exe and choose Make Link), then moved it to Desktop.

Like I've said before, RipIt4Me is definitely not working properly under Ubuntu (I doubt under any Linux distro). My advice is to use VMware Player, set aside about 12-14 gb as a vmx file, and install XP (or Win 2000). That's what I did and RipIt4Me works great (even on Monster House...:-D). Maybe someday RipIt4Me will work under Wine or some smart individual will port it over...but as of today we're SOL when it comes to ARccOS or RipGuard encrypted DVDs in Linux.

---

### Post by PapaWiskas on 2006-11-03
I have tried all configurations, and I did edit the .ini file a while back, just double checked it.  And still no dice.
I dont have 14 gigs to spare for a .vmx, this is my laptop and I really dont want to use all my space for Windows.  I guess I will just use the one XP box I have for the sole purpose of ripit4me, I really hate that I have to do that.
Why hasn't there been a linux app that deals with ARccOS or RipGuard?

---

### Post by sygin on 2007-03-20
Hi,

I had the same problem. I solved it by coping a mfc42.dll file from windows 2000 SP4 installation into system32 directory. After updating mfc42.dll all works.

I was using a mfc42.dll I got from [www.dll-files.com](www.dll-files.com) - this is the one that did not work.

Cheers
Sygin

---

