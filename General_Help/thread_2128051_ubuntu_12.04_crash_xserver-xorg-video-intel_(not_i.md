---
title: "ubuntu 12.04 crash xserver-xorg-video-intel (not installed)"
date: 2013-03-21
forum: General Help
---

### Post by dwsmith on 2013-03-21
I receive this crash at leat once an hour.  How can I fix this?  
I have downloaded the drivers for intel, I have added the ppa for the xserver-xorg and updated, and upgraded.  I don't know what else to do.

The executed path is /usr/share/apport/apport-gpu-error-intel.py

---

### Post by gifford on 2013-03-21
Are we talking about the new Intel drivers that were just released around 3-10-2013? Or older drivers?

---

### Post by dwsmith on 2013-03-22
I just downloaded 4 days ago so it should be the new one.

---

### Post by IanGrayland on 2013-03-22
Same problem here. Happens when scrolling in Firefox, Thunderbird mails and LibreOffice calc (when working on the annual accounts spreadsheet. eek!)

"Are we talking about the new Intel drivers that were just released around 3-10-2013?"

Yes. That's when the problem started here, as far as I can tell.

---

### Post by AIREE.Shadow on 2013-03-22
please give us some information from x-server logs

---

### Post by FeliceMente on 2013-03-22
I have the same problem on Ubuntu 12.10 (64 bit version).
Everything perfectly worked before the update of some days ago but, since then, I continuously get crash reports from apport (/usr/share/apport/apport-gpu-error-intel.py).
For the moment, I disabled it and the computer seems to work perfectly so, could it just be an apport problem?
Anyway, mu computer is a Samsung NP300E5X-A04IT, with Intel Intel HM75 chipset and Intel HD3000 integrated graphic: [http://www.samsung.com/it/support/model/NP300E5X-A04IT-downloads](http://www.samsung.com/it/support/model/NP300E5X-A04IT-downloads).

---

### Post by IanGrayland on 2013-03-22
"could it just be an apport problem?"

no, the screen freezes while scrolling resulting in a crash report in /var/crash
the time of the report matches the time of the freeze
the crash is listed as xserver-xorg-video-intel

i'm on 64 bit precise lts with the quantal lts backports viz: 12.04.2

---

### Post by FeliceMente on 2013-03-22
> **IanGrayland said:**
> "could it just be an apport problem?"

no, the screen freezes while scrolling resulting in a crash report in /var/crash
the time of the report matches the time of the freeze
the crash is listed as xserver-xorg-video-intel

i'm on 64 bit precise lts with the quantal lts backports viz: 12.04.2

I checked my /var/crash dir and I have those files, too. I had the same behaviour you described but, after disabling apport, I no longer had problems.

---

### Post by gifford on 2013-03-22
There seems to be an issue with 12.04 64 bit and the intel drivers. [http://www.webupd8.org/2013/03/intel-releases-linux-graphics-drivers.html#more](http://www.webupd8.org/2013/03/intel-releases-linux-graphics-drivers.html#more)

---

### Post by ManamiVixen on 2013-03-22
What Chipset do you have? The drivers from Intel's site were really meant for the chipsets older than the i915. More up-to-date chipsets really don't need the downloaded driver unless for some special purpose.

---

### Post by kevin1 on 2013-03-23
Having done a full update of my 12.10 64 bit system today I am getting frequent freezes & crashes.

Is it possible to roll back the drivers to the pre-update state?

Thanks,

Kevin

---

### Post by linux_one on 2013-03-23
seems like a terrible bug, I made the following thread for it;
[http://ubuntuforums.org/showthread.php?t=2128691](http://ubuntuforums.org/showthread.php?t=2128691)

---

### Post by kevin1 on 2013-03-24
Thanks linux_one.

Driver uninstalled as per your linked bug report. Here's hoping.

Kevin

---

### Post by jonnyboysmithy on 2013-03-24
I've also been having this error  (/usr/share/apport/apport-gpu-error-intel.py). But only since I upgraded  my kernel. 
I'm running 12.10 with the 3.5.0-21-generic kernel. The 3.5.0-26-generic and a couple version below also get this crash very often many times a  day. So now I just use the older kernel. Odd isn't it? Could someone check to see if this works for them? Btw I havent installed any drivers and everything is vannila.

---

### Post by linux_one on 2013-03-24
yes, seems a temporary solution, I updated 
[http://ubuntuforums.org/showthread.php?t=2128691](http://ubuntuforums.org/showthread.php?t=2128691)

---

### Post by jonnyboysmithy on 2013-03-24
Also with the newer kernels my SD card has stopped working. I get the error mmc0: error -110 whilst initialising SD card from dmesg.
I made a bug report for it: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1158982](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1158982)
Since I use the older kernel this hasn't been a problem. Coincidence that both these bugs show up in the same kernels??

---

### Post by jonnyboysmithy on 2013-03-24
EDIT:double post

---

### Post by IanGrayland on 2013-03-26
problem resolved here by going back to 3.5.0-25 kernel. testing ok for 24 hours now. scrolling through this forum is a good test...

12.04.2 LTS 64bit with all the lts-quantal stuff, intel i915 graphics. no proprietary drivers.

problem was with 3.5.0-26 and 3.5.0-27 kernels. scrolling in firefox, thunderbird and - following prior crashes - scrolling in libreoffice calc. sometimes crashes resulted in corruption of display characters. a couple of times the whole bloody lot locked up solid leaving only a movable cursor and no other input available.

---

### Post by xpucto on 2013-04-04
I had the same problem asIanGrayland and the problem was resolved also by going back to 3.5.0-25 kernel.Why did Ubuntu team release unstable updates? Such a pain in the a.. after simple update. It shouldn't be like that especially for new users.

---

### Post by jonnyboysmithy on 2013-04-09
Just want to post this solution as found in the comments here: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1140716](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1140716)
> 
[TABLE]
[TR]
[TD][luca (llucax)]("https://launchpad.net/%7Ellucax")             wrote             on 2013-04-04:                          [/TD]
                       [TD="class: bug-comment-index"]           [ #75]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1140716/comments/75")           
[/TD]
         [/TR]
            [/TABLE]
                               Hi, I just wanted to let you know that I've been using the problematic kernel but using SNA acceleration as indicated in:
[http://askubuntu.com/questions/225356/how-can-i-enable-the-sna-acceleration-method-for-intel-cards-under-ubuntu-12-04](http://askubuntu.com/questions/225356/how-can-i-enable-the-sna-acceleration-method-for-intel-cards-under-ubuntu-12-04)
(posted here some time ago) and never got a hung problem again. I have  problems with the backlight after suspending though, but I had that  problem before too. Without using SNA I can fix it by adding  acpi_backlight=vendor to the kernel boot, but with SNA this doesn't  work anymore (only the "raw" intel backlight works, not the acpi or the  toshiba, but stupid gnome-settings-daemon insists on using the broken toshiba driver).
 Anyway, using SNA at least my laptop (Toshiba Z830) is extremely faster.


              


I've been using the solution as posted above.
 I still get /usr/share/apport/apport-gpu-error-intel.py errors but no hard freezes.
Theres a new kernel availiable so I'm not sure if the issue is still present in the new kernel.

---

### Post by linux_one on 2013-04-11
for the moment best solution is to use older than 3.2.0-38-generic kernels, even the latest 3.2.0-40-generic has the same bug.
for me the /usr/share/apport/apport-gpu-error-intel.py errors soon after login always made system hang after some times or more! so was a good indicator not to continue.

---

### Post by IanGrayland on 2013-04-11
looking good here with 3.5.0-28.47 upgrade installed this morning from proposed repo.

been running all day with no issues.

---

### Post by FeliceMente on 2013-04-26
I upgraded to 13.04, and everything seems to work perfectly, with no video problems.

---

