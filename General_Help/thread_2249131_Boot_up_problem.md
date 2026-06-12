---
title: "Boot up problem"
date: 2014-10-19
forum: General Help
---

### Post by timswait on 2014-10-19
My parents' Kubuntu installation seems to have suddenly and completely broken :( Unfortunately I'm not at home to help out, but it seems serious, just got these screenshots (actually photos of the screen!). They get to grub, as shown here:[https://drive.google.com/file/d/0B4U35RciYQ9kUEpFZC03d214TFpQYzBqMHJiSWdTZ3lCdldz/view?usp=sharing]("https://drive.google.com/file/d/0B4U35RciYQ9kUEpFZC03d214TFpQYzBqMHJiSWdTZ3lCdldz/view?usp=sharing")
but on trying to boot into Kubuntu this just comes up on the screen and nothing more:[https://drive.google.com/file/d/0B4U35RciYQ9kdTEtR2JWNm9kWWxOd3JHMG1COTdQdkUyOURR/view?usp=sharing]("https://drive.google.com/file/d/0B4U35RciYQ9kdTEtR2JWNm9kWWxOd3JHMG1COTdQdkUyOURR/view?usp=sharing")
I have no idea what is going on here. I told them to try the advanced options menu and to try an old kernel, but it's no different, they've also tried recovery mode and that is the same again :( The disk is encrypted on this installation, is this anything to do with it?

---

### Post by TheFu on 2014-10-20
Well, it appear they cannot mount the root partition - that is likely an encryption-related problem.  

What I would ask now is whether /boot was full - that is a common issue for people using either LVM or encryption because the default size of the /boot partition created during the install is 10x too small for average users.  To get it cleaned up is a fairly complex ordeal for anyone not intimately familiar with UNIX shell commands.  It might be easier to jsut have them reload the OS, no use LVM or encryption and restore their data from a backup.  Using encryption means having fantastic backups is 100% -110% mandatory. It is NOT optional.

Or perhaps there is a LUG nearby who you could contact to have someone help?

Of course, this is assuming the issue really is just the /boot partition got filled and not that the HDD has crashed or something else. Hard to tell from here .... or where you are.  Booting off a liveCD/flash drive and running **sudo parted -l** will tell us. It is probably easier to get them to boot off a live-CD, install the **boot-info** script, run it which will automatically post the results online for you and us to review.  Boot-repair (part of the ubuntu repo) will also post this data online and is another option. My signature has links for these tools.

After you get passed this issue - it would be smart to clean up old kernels BEFORE there is an issue. [http://blog.jdpfu.com/2013/02/23/cleanup-old-kernels-from-apt](http://blog.jdpfu.com/2013/02/23/cleanup-old-kernels-from-apt) is how I do it.

---

