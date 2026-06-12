---
title: "Asunder halts during ripping cd's"
date: 2013-05-13
forum: General Help
---

### Post by kdoherty on 2013-05-13
Hello All,
In the past I have used Asunder to successfully rip my cd's  to a fixed bitrate mp3 format (224 bit).  Recently I have been having problems with the process.  The ripping starts and more often than not the process stalls.  There is no set percentage when this happens, it seems random.   

I have uninstalled Asunder and re-installed via Software Center, the problem persists.  I thought that Rythembox trying to access the cd upon inserting the cd might be a problem, so I disabled that option.  I have tried 192 bit encoding, problem persists.  Upon looking at sys.log there are no entries for this event.  

System specs:  Thinkpad T530 FHD, i5 3320, 8Gb RAM, Intel HD4000, Intel Centrino wifi, 500GB 7200 HDD, DVD recorder. ubuntu 12.04  (3.5.0-28) 

I appreciate any leads into solving this thing.

---

### Post by Dennis N on 2013-05-13
It could be a problem with the DVD recorder/player itself, such as a dirty laser. I had one that failed to complete the ripping and a replacement fixed that.

---

### Post by Dennis N on 2013-05-13
It could be a problem with the DVD recorder/player itself, such as a dirty laser. I had one that failed to complete the ripping and a replacement fixed that. Try cleaning it also.

---

### Post by kdoherty on 2013-05-13
Hi Dennis,  the DVD player works fine in WIN7,  I resorted to that to get the cd ripped.  Still open to other ideas.

---

### Post by Dennis N on 2013-05-13
> **kdoherty said:**
> Hi Dennis,  the DVD player works fine in WIN7,  I resorted to that to get the cd ripped.  Still open to other ideas.

I would install a different ripper. See if that makes a difference. There must be 6 or 8 in the repository.

---

### Post by kdoherty on 2013-05-14
Ok, I have installed and tried RipperX and that also meets its demise.  The application is very slow to read the cd, it gets about 3 tracks ripped then halts.  
However, this application had produced some output for errors.  The only problem is that now I can not find the error log.  (var/log/).  
If I recall there were segfaults and there was a mention of a "lame-plugin" within that fault.   So for a method to try and isolate the problem, I disabled mp3 encoding for the cd rip process and enabled ogg.  The application still fails to run the ripping process and stalls after 2 tracks.

An added detail,  I have another machine (Sony Vaio Linux Mint 13 Maya) that seems to be encountering problems with this disk set (series of 3 cd's in set) also.  So I placed a cd that I had previously successfully ripped into my Ubuntu machine and the cd does indeed successfully rip once again.  The machines appear to not like this cd set for some reason.  

any other ideas outside of me using Windows to rip stubborn  media?

---

