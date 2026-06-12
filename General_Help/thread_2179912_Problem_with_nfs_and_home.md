---
title: "Problem with nfs and /home"
date: 2013-10-10
forum: General Help
---

### Post by xeddog on 2013-10-10
I have a couple of computers, all running different flavors of linux.  My main machine (Stealth) is running Ubuntu 12.04 with the gnome-session-fallback.  I have a second hard drive in this machine that I use for /home, and that has been working fine on this machine.  On that machine I also have guest machines using VirtualBox.  Two of these guests are Ubuntu 13.10 (Weirdo), and Ubuntu-GNOME 13.10 (Corsair).  

I have two other physical machines, one Ubuntu-GNOME 13.04 (G-man), and the other is running Xubuntu 12.04 (Intrepid).  I set up autofs to share / directories between all of these machines and the guest machines mentioned above, and for the most part is is all working perfectly.

The part that is not working properly is sharing Stealth's /home directory.  From any other machine, virtual or real, I can mount Stealth's /, and I can access any and all files EXCEPT my home directory on Stealth.  All of the other machines will show *a* home directory, but not *my* home directory.  It looks like it is the original /home/<userid> directory that was created during the initial install of Ubuntu prior to moving it to the second drive.  But this initial home directory has been deleted and no longer exists.  

So for example, From Intrepid, when I mount Stealth's / directory I can see all of the proper directories on Stealth.  I can navigate to any of Stealth's directories and see what I should be seeing for Stealth.  EXCEPT, if I navigate to Stealth's /home/<userid> I only get a very short list of directories.  Things like Documents, Downloads, Movies, Pictures, etc.  Most of which are empty.  This is NOT Stealth's /home/<userid>, nor is it the home directory on any of the other systems.

Any ideas how I can fix this???


Thanks,

X

---

