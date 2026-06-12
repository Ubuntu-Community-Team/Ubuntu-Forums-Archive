---
title: "Trying to load Ubuntu and frustrated"
date: 2015-01-28
forum: General Help
---

### Post by doug23 on 2015-01-28
I am trying to load Ubuntu on a slightly older system that I have here. It is a 4 core 2.8G Pentium. The problem seems to be the something related to the disk formating. This system has fakeraid but it is TURNED OFF in the bios. I have two drives /dev/sda and /dev/sdb both 160G.

When I installed Ubuntu 14 it gets to the install screen and erase is checked. The next screen is the timezone map and all I get is a  ??? ??? popup that allows me to do nothing else but quit. I then installed Mint just to see what it would do. It did give me a little more info showing that apparently there was still /dev/mapper/xxxx  partition entries but the same ??? ???. So I entered command mode and used fdisk and dmsetup to entirely remove any partitions on the drive. Now when I run install on either ubuntu or mint I get a screen with installation type at the top and /dev/sda selected in the bottom window. Nothing shows as far a partitions or anything else. If I select install it tells me there is no root partition. If I select change it errors with an internal error message. Mint gives a little more info in a popup but it is still an unrecoverable error.

OK to go on. I load latest Debian. It installs very nicely showing me all the steps and partitions the drive and just works. I can partition and format ext4 /dev/sdb and mount it. OK now that the drives are partitioned reasonably maybe I can go back to Ubuntu. No dice. Same error. All the loads are 64 bit.

What goes with Ubuntu and why am I getting this error. I have spent the better part of a day trying everything I can think of and searching for possible causes.

I am not happy with Ubuntu's sparse messages. There is a real problem here that should be fixed! BTW Windows 10 loaded and worked fine on this system.

---

### Post by TheFu on 2015-01-28
Post the **boot-info** output or the URL from **boot-repair** tool please. My signature has links, if you need them.

---

### Post by doug23 on 2015-01-28
I wish I had known that as I did run boot-repair.  One thing I forgot to mention is that if you select lvm for install it does go through the entire install and appears to be writing to the hard drive but it fails to boot. I then ran boot-repair but it did not fix the problem of no boot.   So how should I run this? The non-lvm install never actually writes anything to the disk, it just errors. So should I do the lvm install and then boot the live disk and do the boot-repair results? I am not sure if yu are going to see anything significant in the boot-repair in the first instance.

---

### Post by TheFu on 2015-01-28
> **TheFu said:**
> Post the **boot-info** output or the URL from **boot-repair** tool please. My signature has links, if you need them.

Please.

---

### Post by mooreted on 2015-01-28
I have seen that happen as well. If you want Ubuntu on one drive and you want to use the other drive for data, you can disconnect one of the drives and install Ubuntu, then reconnect the second drive after the install.

---

### Post by doug23 on 2015-01-28
Unfortunately that does not work here. Same thing, puts me into partition window where you can do nothing. Change gives I/O error and install says no root partition. Crazy as this is suppose to create a root partition. The drive is formatted Debian but it obviously doe snot recognize that. Fdisk -l  does on the same system. I think this is a install software problem. It musr see something different then fdisk does. Heck I could manually partition and format the drive but it looks like that would not work either.

So you are not giving me any direction here. At what point do I run boot-repair? After lvm loads and does not boot? Non lvm does not even get to the load stage.

---

### Post by TheFu on 2015-01-28
Boot off a liveCD or flash drive and run either of those tools to generate the requested output URL. The post the URL back here.
No need to install the OS.

---

### Post by doug23 on 2015-01-28
OK, it looks like  [http://paste.ubuntu.com/9928398](http://paste.ubuntu.com/9928398)

The repair said successful. Also keep in mind that boot-repair was run against a previously working Debian install

---

### Post by TheFu on 2015-01-29
> **doug23 said:**
> The repair said successful. Also keep in mind that boot-repair was run against a previously working Debian install

So, it is working now?
I don't see anything wrong, though the fact that it thinks SecureBoot is enabled is a worry. Does your BIOS support secureboot?  If so, disable that.

---

### Post by doug23 on 2015-01-29
Did you discover anything from the boot-repair results?

It is working booting Debian. The problem is it will NOT install Ubuntu. I described that in prior messages. The test was run with ubuntu live against Debian on the HD. In the bios UEFI boot is disabled. Is that OK?  I think there is a bug in the Ubuntu install. It is seeing something it does not like. I am trying to install over the Debain.

---

### Post by doug23 on 2015-01-29
OK, I am at a dead end on this. The system appears to work fine with Debian, Windows 10 and others. Why Ubuntu won't install is beyond me. I take it you are not on the Ubuntu team? I suspect I should enter a bug report.

---

