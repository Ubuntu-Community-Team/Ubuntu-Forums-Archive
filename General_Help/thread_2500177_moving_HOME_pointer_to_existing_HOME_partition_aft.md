---
title: "moving HOME pointer to existing HOME partition after re-installing OS [Solved]"
date: 2024-08-24
forum: General Help
---

### Post by ozark_hillbilly on 2024-08-24
hello,

after my system crashed i was forced to reload 20.04 LTS desktop from a Live USB.

I put the OS on partition sda1 as /. My existing Home partition is on sda3.

I am not doing something in the correct order evidently as after making modifications the Ubuntu software locks up while loading.

Attached are screenshots of GParted showing partition assignments and UUID info.

Another question I have is can I go ahead and start installing my apps even though system information will be stored in the 'new' HOME for now until 
I can redirect Home to the existing partition? Will it be necessary to merge/copy certain 'new' HOME files back to the original HOME partition after this to keep everything properly
updated? Or if the apps were previously installed that is not a concern?

I understand the fstab file has to be updated with the sda3 UUID, unmounted, remounted, etc. The sequencing order is not clear to me.
I have found websites that describe moving HOME to a newly created partition but nothing about moving to a pre-existing HOME partition.
I do not operate in the Linux background normally as my software has run stable for the past couple years so the "use it or lose it" mantra applies to me.

When installing the OS with the Live USB I never saw an area where you can tell the system to use a separate partition for HOME.

If push comes to shove I do have HOME backed up on another drive and could just reformat the entire drive and let HOME reside on sda1 and copy my backup to it but
that defeats having the preferred separate HOME.

---

### Post by oldfred on 2024-08-24
You can essentially skip all the initial steps & just add the mount of /home into fstab.
But if you have saved any data or settings in your /home, you may want to copy them first.

To move /home uses rsync- Be sure to use parameters to preserve ownership & permissions 
[Move Home]([https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)) & 
[https://ubuntuforums.org/showthread.php?t=2455822&p=14010437#post14010437](https://ubuntuforums.org/showthread.php?t=2455822&p=14010437#post14010437)
[https://ubuntuforums.org/showthread.php?t=2343317](https://ubuntuforums.org/showthread.php?t=2343317)

---

### Post by ozark_hillbilly on 2024-08-25
Solved - created new install with home in same partition. No longer have a separate partition. KISS - keep it simple stupid. I need to avoid any unnecessary headaches from having a limited Linux skillset.

---

