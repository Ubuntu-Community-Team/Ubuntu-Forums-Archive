---
title: "Problems setting up Thunderbird profile on USB"
date: 2016-11-11
forum: General Help
---

### Post by skanger on 2016-11-11
As per this article:

[http://kb.mozillazine.org/Running_from_a_USB_drive_(Thunderbird)](http://kb.mozillazine.org/Running_from_a_USB_drive_(Thunderbird))

I've been trying to set up Thunderbird to read my profile off a USB flash drive so I can use Thunderbird on multiple computers but keep the profile itself portable.

I set this up easily under Windows but with Ubuntu I'm having problems. I copied and pasted the path to the folder on the USB drive that contains the profile into the profile.ini file but Thunderbird messages that it can't find the profile. At this point I'm not familiar enough with Linux to create a shortcut with the -profile argument (if that would even work in Linux). The profile.ini file with its profile path setting seems like a more logical place to start. Each computer I have with Ubuntu on it could be set up the same. way.

In this area I find Windows to be easier to work with since its very easy to right-click on an icon and add an argument to the target file to be run. I'm not going back to Windows again, so I'm looking forward to getting familiar with these basic operations in Ubuntu.

Thank you for any help, suggestions or recommendations.

---

### Post by howefield on 2016-11-11
From a terminal try..

```
thunderbird -p
```

Delete any profiles that appear and create a new one to the correct path.

---

### Post by TheFu on 2016-11-11
Also be aware that compiled plugins are not cross platform. Most addons should be fine, however.
I've never moved a profile from Windows to Linux, but I have gone from Linux to OSX. Worked well enough. The default file system directory separator could be an issue.  Windows supports /, but Linux/OSX do not support \\ as separators.  Don't know if that matters or not.

---

### Post by oldfred on 2016-11-11
i have used (I think) same profile from 2006 with only Windows XP. 
Then installed Ubuntu and moved profile to NTFS partition and dual booted. Did not always even have most updated version in both installs at same time.
Then copied profile to laptop that was dual booted with XP & Ubuntu. And back every time I traveled.

Eventually retired XP but still had NTFS shared. Finally obsoleted NTFS and moved that same profile into ext4 data partition.
Regularly houseclean and compress sqlite databases.

But path has always been the issue.
And external drives may not always mount at same path. 

Probably best to make sure you have good label on flash drive so it always mounts with label and use that path in profile.ini.
```

[General]
StartWithLastProfile=1

[Profile0]
Name=default
IsRelative=0
Path=/mnt/data/mozilla/thunderbird/lyu25irb.default
Default=1
```

My data partition is /mnt/data
And in data partition is a mozilla folder for both Thunderbird and Firefox.
IsRelative must be changed if not internal default path.

[http://kb.mozillazine.org/Moving_your_profile_folder](http://kb.mozillazine.org/Moving_your_profile_folder)
[http://support.mozillamessaging.com/en-US/kb/Profiles](http://support.mozillamessaging.com/en-US/kb/Profiles)
[http://www.mozilla.org/support/thunderbird/profile](http://www.mozilla.org/support/thunderbird/profile)

---

### Post by skanger on 2016-11-11
Thanks for the helpful replies.

The solution was to set IsRelative to zero as oldfred mentioned.

I should probably start a new thread about the problem that preceded this one, but I'd like to mention it here before marking the problem solved.

I bought a Windows 10 tablet and that OS constantly gave me problems with my USB flash drives. It repeatedly messaged me that my flash drives had problems, were corrupt, needed repair and/or reformatting. I used these drives and their files with WIndows XP, Ubuntu and with printers, never having a single issue. I found that after allowing Windows 10 to "correct" the non-existent problems my files had been corrupted, particularly my Thunderbird profile! A number of inboxes and sent mail folders are empty due to the corruption. This is a separate issue and I'll move it to a new thread, but this is what started a lot of problems for me. My question is should I work to restore the corrupted folder in WIndows XP (where they were created and used for years) or Ubuntu?

One other aside, I installed 16.04 over Windows 10 on this tablet and while it functions, its not yet usable because a number of features don't work and it runs at a snail's pace. I had created a thread for this problem but received no replies in over a week:

[https://ubuntuforums.org/showthread.php?t=2342000](https://ubuntuforums.org/showthread.php?t=2342000)

I'm hoping someone here might have an insight into this. Thank you all for replying and helping.

---

### Post by oldfred on 2016-11-11
If your tablet is built with standard hardware it should be supported, but if not standard it may or may not later get necessary drivers & support.
And all tablets are not as standard as desktops & laptops.

---

