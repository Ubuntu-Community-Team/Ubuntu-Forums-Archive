---
title: "Freeze during boot with 12.04"
date: 2013-08-12
forum: General Help
---

### Post by JKyleOKC on 2013-08-12
The battery in my UPS failed yesterday and shut me down while a VM was running. After correcting the power situation, I rebooted and found a large white square appearing where the mouse cursor should be on screen. While attempting to fix that by changing the mouse theme, on the theory that one or more pointer files had been corrupted by the unexpected power-down, more problems appeared -- culminating in a freeze during boot-up, with the keyboard CAPS and SCROLL LEDs blinking and an hourglass mouse cursor showing on the screen.

Using recovery mode and forcing check of all drives didn't indicate any problems and when I "resumed normal boot" the system came up okay, but I'm not at all confident all is well again. The system is Xubuntu, 12.04.2 with all current updates installed. While trying to diagnose the problem I did try rolling back to the previous kernel version, but it froze in exactly the same way.

The things I need to know now are (1) what's the significance of the flashing LEDs, and (2) what packages are most likely to be the ones I need to reinstall to put things right again. Doing a full clean reinstall is not an option at this point until I can do a full backup of the dozen or so VMs that reside in my $HOME directory. Since the system appears to be functional, although a bit flaky so far as mouse settings are concerned, I'll hold that for a final option...

---

### Post by JKyleOKC on 2013-08-13
Bump -- here's my system details from logwatch: ```
    CPU:     2 AMD Athlon(tm) 7550 Dual-Core Processor at 1250MHz
    Memory:  2897 MB
    Machine: i686
    Release: Linux 3.2.0-51-generic
```While the system is usable, it's still flaky...

---

### Post by DuckHook on 2013-08-14
Hi Jim,

Hope all is otherwise well (apart from flaky box).

A similar problem happened to me some time ago when I brainlessly shut down while a forgotten VM was still running on another panel of my desktop. Shutdown process stopped at a kernel panic and nothing worked except a hard poweroff (REISUB would not work because keyboard and everything else was frozen, flashing and frantically beeping like a dying cat). System would not reboot until I used recovery mode with a much older kernel, and was never the same again thereafter. Trying to squash the subsequent issues was akin to playing whack-a-mole while blindfolded. After about three days of wasted time and effort, I finally bit the bullet and reinstalled, using the opportunity to go for an updated distro. Never got that VM to ever run again. Luckily, I had backups, but my install was toast. I'm afraid I have no real solution for you except sympathy and moral support. If the system still boots up, then I would suggest that you backup as soon as you can with the aim of reinstalling.

I am not knowledgeable enough about either OSes or VMs to know for sure, but I suspect that system shutdowns while a VM is running are especially toxic because modern VMs hook myriad Linux system resources in order to provide faster and better user experiences. In the old days, the VM just translated system calls, so a crashed VM didn't bother Linux. But these days, there are so many passthroughs, captures and paravirtualizations hooked into the kernel that a VM crash has the effect of corrupting the base OS. I have no idea if this guess is correct, but I wouldn't be surprised if something like it were true.

Hope that some kernel guru can jump in here to help you.

---

### Post by squakie on 2013-08-14
Hi guys!  Sorry for your problems Jim.  I agree with Duckhook - while I have no knowledge to point to and say "this is it", I think DuckHook is right on with his thoughts on all the hooks of the VM's and what can happen to your system.  I didn't get the blinking lights on my keyboard (it wasn't perhaps Morse for SOS was it? ;) ), but I had this very thing happen to me as well - a VM running, forgetting about it, and just physically pushing the power off button (why, I don't remember unless I was just trying to be more stupid than I already am).  Same result - things didn't work right, only solution for me was to backup and reinstall.  I don't have a clue if there is a "repair" like option for reinstalling Ubuntu or not, but if so, that might help you out as well.

Hope you guys are all doing fine!

EDIT:  btw DuckHook, I love the playing whack a mole in the dark thing!  And DuckHook - sorry for my private rant ot you about the replies on my server issues from a month or so ago.  I was trying purposely to play dumb hoping someone would point out what I was missing, but it wasn't working and I just got mad.  Sorry about that!

---

### Post by JKyleOKC on 2013-08-14
Thanks to both of you! The diagnosis sounds accurate so I'll be backing up all the critical stuff and doing a re-install of Xubuntu 12.04.2. I do have a separate /home partition so I may be able to get by with simply reinstalling the system -- but even so I'll lose several years' worth of customization (XFCE 4.10, NFS, dual-NIC for LAN routing, and so on). I'll back up /etc and hope for the best there...

Meanwhile here's a few of the oddities I've noticed in the last couple of days:

Two of the panel applets (sensors and weather) lose their settings each time I log out/in, but work properly once I enter the settings again. The mouse pointer sometimes vanishes for no apparent reason. The freeze-up doesn't happen until well into the "autostart" phase of logging in; sometimes it leaves the splash screen on the monitor and other times the screen goes black.

The VM that was running at the time of the failure was totally borked, but I managed to copy its critical data files over to a flash drive and rebuild it in the same virtual disk with no noted complications. Others do not seem to be affected but I've not done anything with most of them, and won't until I've copied all the virtual disks to a backup drive.

Wonder if possibly purging vbox and re-installing it might help? If I'm going to wind up doing a clean install anyway, might as well do some experimenting first to see what we can learn...

Also am considering creating a new user and seeing if the symptoms carry over to that one or are restricted to just my original user profile. [COLOR="#FF0000"]EDIT:[/COLOR] Did this, and the symptoms did not carry over. I haven't yet added the new user to the vbox group, however, and that may make a difference. More coming up...

All ideas are welcome! And thanks again!

---

### Post by DuckHook on 2013-08-14
You are right. You've nothing to lose experimenting. Therefore, here are some of my ideas:> **JKyleOKC said:**
> Two of the panel applets (sensors and weather) lose their settings each time I log out/in, but work properly once I enter the settings again.You might try purging and reinstalling the applets. I take it that you are using lm-sensors?> The freeze-up doesn't happen until well into the "autostart" phase of logging in; sometimes it leaves the splash screen on the monitor and other times the screen goes black.You might try hitting <Esc> during bootup to get rid of the splash screen and see which process it hangs on. Alternatively, <Shift> then edit "quiet splash" out of grub to see everything.> Wonder if possibly purging vbox and re-installing it might help?Can't hurt, and if it turns out that the corruption was just confined to Vbox, this might solve everything for you (by reinstalling just virtualbox). You could also try blacklisting vbox driver on your next boot just to see if that helps. If so, then you've narrowed the matter down to vbox.> ...Did this [create new user], and the symptoms did not carry over.It never occurred to me to try this when I borked my system. If this stabilizes your system, then it may simply have something to do with some config files that have been somehow mangled.

Can you post the contents of *dmesg* and your *syslog* (especially after recovering from a freeze)?

---

### Post by JKyleOKC on 2013-08-15
Yes, it uses lm-sensors. As for the splash screen, I wasn't clear. It's the XFCE splash screen, after logging in. Up until I log in, the reboot is perfectly normal -- and I've removed "quiet splash" from /etc/default/grub so that I always get the blow-by-blow text during the boot process. However, the screen goes dark from time to time -- I apparently have something misconfigured in the text console that causes an error message when Plymouth attempts to switch to the vesafb drivers. This, however, has been normal ever since I upgraded this system to 12.04.

The content of dmesg and syslog really doesn't help at all; /var/log/dmesg.0 is a zero-byte file, as is the content of dmesg.2.gz and dmesg.4.gz; the other dmesg files are from logins where no lockup took place. In syslog, it's quite obvious that the critical data just before I give up and force power-down was buffered and did not get written to disk; the successful boot sequence's first line starts in the middle of the previous line, and the immediately preceding lines vary from one instance to another.

Interestingly enough, when I logged out of the new "test user" and logged back into my original profile, the system looked perfectly normal. I've not yet tried adding the test user to the vbox group, though. One thought that occurred to me today is that my original profile was set up to log in automatically at the first reboot -- that might be causing something to get into a race condition if the power-down happened to cause disk damage that slows down the full boot process; anything that delays the login long enough for the boot processes to complete could allow proper operation. I'll try removing that auto-booting option and see what happens next.

Times are indeed interesting, as the Chinese might observe...

---

### Post by DuckHook on 2013-08-15
Okay. So the freeze occurs at some point during loading of X or the DE. The primary boot process seems to go fine but, to my knowledge, this includes loading of the *vboxdrv* module, which would be odd because you would think that this is the step that kills your boot process. Have you tried blacklisting *vboxdrv* (temporarily) and seeing if this makes the freezes go away?

---

### Post by JKyleOKC on 2013-08-15
Not yet; however I just did a restart after removing the check from "no password at login" and the system did still log me in automagically. Obviously there's another option somewhere that I've forgotten about. Anyway, this time it came up clean, just as before the power-down incident. Both panel applets retained their settings, and even though I've purged the saved sessions, it is quite obviously a saved session from sometime. The mystery deepens...

EDIT: Found the config, in /etc/lightdm/lightdm.conf where autologin was set and also saved session. Commented both of them out but have not yet restarted. I think I'll wait a while and see if it's still working right...

---

### Post by JKyleOKC on 2013-08-16
Here's the next instalment of the saga. After doing away with the autologin, I still get the lockup if I log into my original profile after doing a restart. However if I log into the test user, which now has sudo privileges just like my original, all seems to be working with one glaring exception: the mouse cursor is using the DMS-Black theme although it's set globally to DMZ-White, and making changes (to the mouse) with the Settings Manager dialog has no effect at all.

Once I've logged in as the test user, I can log out, then log back in as my original self, and everything works except for the mouse cursor staying black.

I've re-installed the NVidia-current package, and also the xorg mouse package, with no change in anything.

Next, I blacklisted the vboxdrv module, and rebooted. As before, logging into my original profile caused the lockup. Forced shutdown, restarted, and logged into the test user. Everything worked, except of course that user is not authorized for VirtualBox so I didn't try to run that. Logged out, then back in as myself, but this time it locked up rather than being usable!

I forced shutdown again, rebooted, logged into the test user, and from there removed the blacklist entry for vboxdrv. After saving blacklist.conf I rebooted, and things were back to normal: that is, lockup if I initially log in as me, all works if I initially login as test user, and after logging in as test user I can then log in as myself and all seems to be working.

I did note that the date display from the Orage panel applet sometimes vanishes, although the applet continues to run. Also the other two panel applets seem now to be holding their settings. This may indicate progress, or may simply be change...

The problem definitely seems to be connected with the video area and the mouse; I've considered reinstalling the entire xorg system via Synaptic. I'm confident that the total failure once I blacklist vboxdrv and remove all of its hooks indicates a problem there but I'm unclear on how to force a rebuild of the vbox driver set, and also uncertain whether that would help, or just make things worse...

Any new ideas?

---

### Post by DuckHook on 2013-08-16
This is where I'm clearly beyond my depth, but it seems to me that if you could compare the config files between your new user and your primary account, this might show up the differences between the two and give you a clue about what leads to the lockup. However, I haven't the foggiest notion how to do that. For one thing, I don't know precisely what init/config/startup files/processes are invoked to start user accounts, so wouldn't know where to even begin looking.

Another idea is to look at *dmesg* or your *syslog* for those times that you *successfully* log in (using your two-step process). There may still be a hiccup that gets recorded, but that the system is able to overcome by virtue of already having been logged in.

Aside from the above, I'm frankly out of fresh ideas.

Of course, there's the old idea that it may make more sense to reinstall, but you know the pluses and minuses of that process better than anyone.

---

### Post by JKyleOKC on 2013-08-17
> if you could compare the config files between your new user and your primary account, this might show up the differences between the two and give you a clue about what leads to the lockup. However, I haven't the foggiest notion how to do that. The following script, run as "sudo cmpcfg jk testu" to provide access to most of the files for both users, takes care of comparing the config files in the home directories. However it doesn't drill down into the configuration directories of which there are so many. Once I remember the correct syntax for conditional statements in bash, though, I think I can make it recurse properly to compare those also.

```
#! /bin/bash
#  Script to compare config files of two users

cd /home/$1/
for f in .[A-Za-z]* ; do
    echo "===comparing config $f for users $1 and $2==="
    diff $f ../$2/$f
    echo "===end comparison for $f==="
done

exit 0

```Unfortunately, most of the config files in "jk" don't exist in "testu" and the problem could be in almost any of those. I'm pretty much convinced by now that the only way to make the system fully trustworthy again is going to be a clean re-install (followed by about two weeks of tweaking to get everything set up properly again), but I'm still trying to track the cause down simply so that I know more about what's going on behind the curtain. I've disassembled the MS-DOS kernel (back at version 4.1) and have a more than passing knowledge of what has to be happening, but finding the exact spots at which to begin excavating is the problem.

So far, most of the differences in files that exist for both users appear to be minor, such as differing date stamps or authentication keys. I'd post the output from this little script, but it's more than 1150 lines and most of those appear insignificant. Only the ".xsession-errors" files seem promising, but I've not been able to get a feel for why they have so many seemingly repetitive lines for both users...

---

### Post by JKyleOKC on 2013-08-20
Today's kernel update (20 Aug 2013) together with the nvidia-current update, which resulted in rebuilding all the DKMS modules (and possibly restoring all the hooks to original values, though that's just a guess on my part), seems to have removed the flakiness. The system is now able to boot into my original user profile with no freezing, and the mouse pointer seems to be operating properly. I'll wait a bit before doing the re-installation of everything, but I'm prepared for it with backups of all the VMs, and also the entire /etc directory -- and a procedure established for expediting update to the backups using "cp -puR" which will help in future.

I'm not marking the thread "solved" yet, since the original questions haven't gotten answered, but it may be well along the path of dying quietly...

---

### Post by DuckHook on 2013-08-20
Good to hear that the stars aligned and things worked out. With the complexities of modern OSes, sometimes we just accept the mysteries and make suitable offerings to the computing gods.

---

