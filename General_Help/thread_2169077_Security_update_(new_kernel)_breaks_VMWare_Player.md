---
title: "Security update (new kernel) breaks VMWare Player"
date: 2013-08-20
forum: General Help
---

### Post by r_avital on 2013-08-20
So this morning, Software-Updater wants to install security updates, and shows me it will install a new kernel, 3.8.0-**29**-generic -- so I proceed with the update.  Reboot.  No incidents.

Then I go to use my computer for some actual work, launch VMPlayer (latest version, 5.0.2), and VMWare tells me it needs to install a few modules into the kernel.  Makes sense.  [SIZE=4]_***[COLOR=#ff0000]Anyone who's ever used VMPlayer has seen this every time a new Linux kernel is installed.[/COLOR]***_[/SIZE] [SIZE=4][COLOR=#ff0000]_*** So I proceed.  VMWare reports errors, can't go on with the install.  ***_[/COLOR][/SIZE]Meaning, can't use VMPlayer.  At all.  Same exact behavior under Unity or MATE desktop.

I reboot into the previous kernel, 3.8.0-**27**-generic.  Run VMPlayer.  Runs fine.  Start an actual VM, runs fine.
On a hunch that doesn't take much genius, I run the vmware installer, uninstall VMPlayer, while still in 3.8.0-**27**-generic.
Reboot into 3.8.0-**29**-generic.  Reinstall VMPlayer.  Now it works.  Run a VM, runs fine.

YAY!  The old brute-force Windows uninstall/reinstall method works!

Now what?  Is this the new normal whenever a new Ubuntu Kernel is installed?  When will Canonical stop futzin with us?

Incidentally, "just run virtualbox" is not an answer.  Debates on the merits of one vs. the other belong elsewhere.

Edit:  Opened bug report on launchpad.

---

### Post by tripp98 on 2013-08-20
When you have a new kernel with vmware you have to reinstall.  This isnt a Ubuntu issue.  Its how vmware handles the kernels.  No matter what version of Linux you run you have to reconfigure

[http://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=1002411](http://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=1002411)

---

### Post by r_avital on 2013-08-20
Yes, tripp98.  As I clearly said, it's the reconfigure that fails.  One more time:  It's the reconfigure that fails.  It never failed before.   I'll go back to my original post and highlight it, to make it clear.

I've been using VMWare for 3 years, In Lucid, NEVER had to REINSTALL after a new kernel came in from an update.  NEVER.  NOT ONCE.  ALWAYS allowed VMWare to RECONFIGURE, but NOT REINSTALL.  Done this a dozen times.

So yes, this is an Ubuntu issue.

---

### Post by r_avital on 2013-09-09
Another kernel upgrade two days ago, 3.8.0-30-generic, same behavior:

1. Reboot after upgrade.
2. Run vmplayer.
3. vmplayer responds with message about installing modules into kernel.
4. Ubuntu notifies me of a crash.
5. Uninstall vmplayer.
6. Reinstall vmplayer.  All OK.

Yes, this is an Ubuntu issue.

Reported Bug #1214562 on Launchpad on 8/20/13.  Still unassigned.

---

### Post by r_avital on 2013-09-09
Another kernel upgrade two days ago, 3.8.0-30-generic, same behavior:

1. Reboot after upgrade.
2. Run vmplayer.
3. vmplayer responds with message about installing modules into kernel.
4. Ubuntu notifies me of a crash.
5. Uninstall vmplayer.
6. Reinstall vmplayer.  All OK.

Yes, this is an Ubuntu issue.

Reported Bug #1214562 on Launchpad on 8/20/13.  Still unassigned.

---

