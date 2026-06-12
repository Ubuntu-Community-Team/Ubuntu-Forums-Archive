---
title: "Ubuntu 7.10 boot &amp; Pidgin Q ..."
date: 2008-03-03
forum: General Help
---

### Post by xen-uno on 2008-03-03
Does Ub go through a disk check or defrag on boot? I've had a couple abnormally long, disk intensive boots ... first time after an unsuccessful attempt to get my wired XBox 360 controller to work, and the 2nd time after breaking Pidgin.

Regarding Pidgin ... I noticed that v2.4 was out (shipped Ub Pidgin build is 2.2 I think). Anyhow, I had what appeared to be a successful compile of 2.4, uninstalled 2.2, then did a make install with 2.4. Pidgin would not run, and didn't register itself either. I've searched through the directories deleting any Pidgin dung I could find, then re-installed 2.2. Needless to say, 2.2 doesn't run (from Terminal, for instance), and it also won't put an icon back in Applications>Internet. I was very adept at hacking the Window registry and have looked at Ubuntu's, but I didn't see any Pidgin entries. It's kind of looking like a total re-install may be neccessary, though Ub and every other application runs fine. Any ideas how to correct?

---

### Post by neilengineer on 2008-03-03
Better and easier install/update softwares via synaptics.   Compiling from source code is not a good way.

Maybe you can try to reinstall pidgin 2.2 using synaptics.

---

### Post by articpenguin on 2008-03-03
ext3 dosent need to be defragmented as it accutally looks for free space that the file can fit instead of throwing it anywhere like fat or ntfs do.

---

### Post by xen-uno on 2008-03-03
That's cool on the frag, but just what exactly was it doing on the long boots? 

Used Synaptic to get rid of vestiges of Pidgin, then re-installed. Works now except it won't start up on log in when placed in Startup, got around that by saving current session.

---

### Post by imtheguru on 2008-03-03
Get packaged versions of Pidgin from [http://getdeb.net/app/Pidgin](http://getdeb.net/app/Pidgin)

Cheers.

---

### Post by SoDanishWasLike on 2008-03-03
> **xen-uno said:**
> That's cool on the frag, but just what exactly was it doing on the long boots? 


The same happened to me, I went here for the solution: [http://ubuntuforums.org/showthread.php?p=3590794#post3590794](http://ubuntuforums.org/showthread.php?p=3590794#post3590794)

---

### Post by xen-uno on 2008-03-04
Interesting ... I'll have to break the boot again :). I'm getting 40 second boots (from dual boot screen to login prompt) except under the circumstances noted above, regardless of the Quiet settings (their speedup must have been with the VGA setting). Thanks ... now I can see what's going on during boot.

edit: What i did have once is an indefinite boot when the xbox 360 controller was plugged in via USB. Once I pulled the plug it proceeded normally.

---

