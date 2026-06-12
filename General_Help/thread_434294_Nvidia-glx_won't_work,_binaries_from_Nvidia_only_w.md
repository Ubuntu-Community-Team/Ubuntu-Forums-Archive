---
title: "Nvidia-glx won't work, binaries from Nvidia only work until reboot"
date: 2007-05-05
forum: General Help
---

### Post by Moosechees on 2007-05-05
Every time I reboot now, I'm met with a series of errors that look like:

[ 74.152361 ] usb 5-1  something something error -110 (or 101?)

 I'm dropped to a root prompt, so I hit ctrl-alt-delete which then continues the booting process.  I'm met with a few more errors that flash by too quickly for me to read, then I am temporarily dropped to a root prompt once again, but before I have a chance to do anything (about 3-5 seconds later) Gnome tries to load three times, then fails and drops me to a login prompt.

I log in, and run the install script from the Nvidia site in order to get up and running again.  The install usually goes successfully.  I 'sudo gdm stop' and a second later Gnome starts up and I can log in and everything is working just fine.

For whatever reason, I need to reboot. Computer starts up and then we're back to the beginning of this post, every time.

I tried using nvidia-glx , but I can't even get them to work at all now (previously they "worked" but didn't seem to support any 3d rendering).

I upgraded from 6.10 to 7.04 about a week or two ago, and I don't think I had this problem until a few days after that.

The only thing I can think of that could potentially have caused these problems: I'm dual-booting with Windows XP, which has the ext2 drivers installed, so all my ext2 drives were mounted. I then made the mistake of hibernating XP and booting into Ubuntu, which freaked out because every partition on my system, including the windows NTFS, was not unmounted cleanly.  However, I've run fsck on every partition and everything appears to be ok now.  

Other than that, I haven't been messing with anything the last few days.

Any ideas?

---

