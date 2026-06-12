---
title: "Screen freezing on Linux (Ubuntu &amp; Opensuse ) system"
date: 2021-04-09
forum: General Help
---

### Post by Beetlebum_007 on 2021-04-09
Hi, I originally had a Windows system installed on my pc which I changed to Opensuse. I used a free dvd which came with the March (2021) issue I think.
This installed without any issues at all but when I started to use the system from first use the screen would freeze. I discovered if I pressed ctrl+alt+backwards delete and I logged in again the problem would appear to go away.
However, this became a bit frustrating having to do it every time I used the computer so I downloaded a new ubuntu 20.04 .iso which I installed. I thought maybe there was an issue with the free software I got from the Linux mag. The problem seemed to become worse. The machine stated to freeze during installation. After a few tries I managed to install and successfully update the software but I'm left with exactly the same problem. The only difference being I am unable to press ctrl+alt+backwards delete to log out and log in again. Whether that's an issue with the freezing or the new ubuntu is like that I'm not sure.
I never had this problem with the original Windows OS it only appeared when I changed to Opensuse and then continued with Ubuntu. Does anyone have any ideas what the issue could be? I'm unsure if it's hardware or software and I don't know how to check the system. All suggestions will be greatly appreciated. Thanks in advance.

---

### Post by CelticWarrior on 2021-04-09
Have you selected the option to install third-party drivers, etc.?

---

### Post by guiverc on 2021-04-09
You have provided minimal specific details, but from your description I'd test the hardware of the system first, starting with motherboard, memory & PSU, disks etc.

You didn't provide any specifics as to what opensuse, was it a tumbleweed? or a normal release of leap, if so which?  the kernel stack etc. thus isn't known, and I can't compare with the Ubuntu 20.04 LTS system you used (again with limited detail; was it an ISO that uses the GA kernel stack, or an ISO that resulted in HWE being used).  The more details the more clues we have to go on.

If my system crashes, I don't dare try and boot it again until I've run various diagnostics. First I boot a known *live* system and explore for clues, and `fsck` (*file system check*) the installed systems etc. Only when I've decided there isn't hardware reason do I try and boot my system normally.

If the system is running, did you explore logs?  Crashes (other than kernel panic) will leave clues via .crash files (/var/crash/) or clues in systemd journal...  This applies to both opensuse & ubuntu.

Was the opensuse & ubuntu using a like stack?   if they were, I'd explore using the system with a different stack (different opensuse leap system or different Ubuntu release).

The fact that windows was good doesn't provide that much detail; it maybe bad areas of the disk (ie. check SMART health) and as the GNU/Linux was new installs, they are using (by chance) a bad area of the disk that windows didn't use... logs will show this, as well as exploring the hardware.

I'd suggest being as specific as possible (20.04 server? desktop? 20.04.1? 20.04.2? or *flavor* of 20.04 etc) as those all influence what install you have by default (though post-install you can make change it too), and we don't have that information. 20.04 server & *flavor* installs default to GA kernel, 20.04 desktop (or 20.04.2 *flavor*) however default to a HWE kernel by default so 20.04 alone doesn't tell us what exactly you have. Some applies with opensuse...

---

