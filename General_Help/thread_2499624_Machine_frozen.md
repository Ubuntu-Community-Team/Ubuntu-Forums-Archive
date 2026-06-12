---
title: "Machine frozen"
date: 2024-08-04
forum: General Help
---

### Post by jgw on 2024-08-04
This is the same bad machine.  This time it was booting, starting firefox then quitting.  I finally got firefox from even starting.  Now, when I boot up I just let it sit there, running, as far as I know doing nothing.  In about 5/10 minutes, however, it cleverly writes two lines below hundreds of times.  The only thing that changes is the beginning numbers (299etc  none of the numbers, as far as I can tell are the same after the 299 ones:

```

299.997904 systemd-journald[226]: Failed to write entry (35  items, 996 bytes) despite vacuuming, ignoring:Input/output error
299.998840 systemd-journald[226]: Failed to rotate /var/log/journal/29fa95c588114ee7a64b46faf8bed4/system.journal:read-only file system

```

I also know it starts with something but that goes away so fast I cannot read it and don't know how to stop it so I can see it.

Thoughts?

---

### Post by dragonfly41 on 2024-08-04
You might find it useful to switch to another Firefox profile without some tabs, extensions installed.

[https://support.mozilla.org/en-US/kb/profile-manager-create-remove-switch-firefox-profiles](https://support.mozilla.org/en-US/kb/profile-manager-create-remove-switch-firefox-profiles)

Also Stacer can offer a nice dashboard for administration.

---

### Post by jgw on 2024-08-04
Thank you for the reply...........

If I ever get this think to actually run so I can do something I plan to remove and replace firefox.  The current one is also in snap and I kinda liked it not in snap.

---

### Post by #&amp;thj^% on 2024-08-04
These are concerning at least to me they are:
```
Failed to write entry (35  items, 996 bytes) despite vacuuming, ignoring:Input/output error
Failed to rotate /var/log/journal/29fa95c588114ee7a64b46faf8bed4/system.journal:read-only file system
```
Looks to me like this one is is in a read only phase, when is the last time you ran  fsck?

Just a reminder, Do not run fsck on a mounted device, you will need to unmount the target first to avoid damage to your files.

---

### Post by jgw on 2024-08-05
Tried your suggestion (httops) and it failed - couldn't find it
Installed stacer - forgot about it, thanks.........

Thank you for the reply!!

---

### Post by jgw on 2024-08-05
I ran fsck whilst booting yesterday - no problems

I also ran the dell pre boot tests.  That one checks all hardware and reports.  If I could figure out a way to get it into a folder I could post it but I haven't figured that one out. 

Thanks for the reply!

---

### Post by jgw on 2024-08-05
I now have the machine running.  What I did was to disconnect one of the hard drives.  I think it all has to do with firefox.  Tomorrow I will continue my quest.

---

### Post by jgw on 2024-08-06
I have now re-installed the drive.  Before I did that I, in theory, deleted firefox.  I then searched for "firefox' in the same drive (SDD boot drive) and there was more than a complete page of them.  I deleted every one of them.   Now, again, I now have two drives. its all booted up and seems to actually working.  This being the case I seem to have been right about the firefox thing.

---

### Post by dragonfly41 on 2024-08-06
It might have been easier to create a fresh Firefox profile. If you run in terminal

firefox --help

you see the command line options .. including ProfileManager.

---

### Post by jgw on 2024-08-06
Thank you for the reply............

I just gave up.  First I checked to see if I had the program, I didn't.  I then deleted every "firefox" I could find, rebooted, re-installed and then synced firefox and now I am back up and running.  

I was going to not install in snap then then just gave up and installed in snap.  I will see how it works.

So, far.

---

### Post by HermanAB on 2024-08-08
In my experience, the whole snap system is best uninstalled.  One problem is that the people who make snap packages do not test them sufficiently. The other problem is that the snap system is not as good as it is claimed to be and allows the whole machine to freeze up, which should never happen on a Linux system.  So snap is still a combination of immature cruft.

---

### Post by jgw on 2024-08-09
Now this machine is no longer booting up.  Its very strange.  It takes about 3 boots before it actually boots.  It makes no sense.  I have no idea what is going on.  

Thoughts?

---

