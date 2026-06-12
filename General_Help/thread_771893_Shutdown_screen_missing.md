---
title: "Shutdown screen missing"
date: 2008-04-28
forum: General Help
---

### Post by High Roller on 2008-04-28
Hello!

Whenever I shutdown Ubuntu Hardy I don't get that fancy status bar and Ubuntu logo that should be present.  Instead, the system stays in text mode and doesn't display the shutdown screen until the very last second and then quickly disappears.  Then the system shuts down.  No errors etc.

I ran Hardy throughout the beta phase and didn't have this problem at all.  Then once I re-installed upon final release I encountered this problem.

When booting the splash screen/status bar are present and work as they should.  My parents are having the same problem on their computer.

Is there any way I can go about fixing this?  Thanks in advance!  :)

---

### Post by High Roller on 2008-04-28
*bump*

---

### Post by niglch on 2008-04-28
I upgraded from Gusty to Hardy and I have noticed the same change. Whenever I shut down I no longer get the splash screen with the loading bar that goes backwards. I get a bunch of text and at the last second the splash screen appears with the bar all the way down. I can't tell if it is doing this because anything is actually wrong though.

---

### Post by SamSlater on 2008-04-28
Me too. Says something about the Network Manager & 'failed' then switches off.

---

### Post by exploder on 2008-04-28
Here are the bug reports.

[https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/216266](https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/216266)

and

[https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/216266](https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/216266)

I have seen this bug on three pc's. This is an LTS release?

You might want to add to the bug reports. I do not know if that will change anything though...

---

### Post by High Roller on 2008-04-28
> **SamSlater said:**
> Me too. Says something about the Network Manager & 'failed' then switches off.

I had this error at one point as well.  I removed networkmanager completely and the problem was still there even when the error was absent.  From what I gather, that error occurs almost all the time but is hidden behind the graphical shutdown.  Not to say that having an error is a good thing, but I'm led to believe that this isn't where the problem exists.

---

### Post by High Roller on 2008-05-12
I've found a workaround [here]("http://ubuntuforums.org/showpost.php?p=4934956&postcount=10").
It appears this problem is related to GDM.  This is an
odd way to fix the problem but it worked for me!

Post your results.

---

### Post by thahir1986 on 2010-06-22
try this one it's work for me.


apt-get install usplash

apt-get install usplash-theme-ubuntu

and /boot/grub/menu.lst , check

kernel /boot/vmlinuz2-2.x.x.x-generic root=UUID XXXXXXXXXXX ro quiet **splash vga=792.**

save and update-grub   :guitar:

---

### Post by Tornado6 on 2010-10-04
hope i'm in yhe right place, i install ubuntu netbook remix lucid and i installed some education stuff, now it's turn into edubuntu, how do i change the splash screen back to ubuntu?

---

