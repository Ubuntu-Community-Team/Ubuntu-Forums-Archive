---
title: "Messed up my graphics drivers"
date: 2013-04-12
forum: General Help
---

### Post by Hungry Man on 2013-04-12
I tried to install FGLRX drivers on Ubuntu 13.04, but that didn't work out.

I then went back to the open source drivers (via update-manager) but I couldn't boot into a graphical OS.

I got a black screen with a prompt to log in.

I got in, launched lightdm manually, and reinstalled teh OSS drivers... and now I have them installed, and I even seem to be using them (Chrome://gpu reports that I am, and I can move things around the screen).

But everything is screwed up - I can't get Unity to launch, I'm still booting into the black screen, and I can't seem to fix this.

Help?

edit: I removed fglrx completely, and I now boot into a UI, but it's just a desktop background. No Unity.

edit2: I can now launch Unity manually... but it doesn't have any of my old settings, and doesn't have any plugins etc. So that's still not working great.

edit3: I went into CCSM and reenabled all of the plugins like Unity and gave default settings. IDK what else but something broke Unity, I can no longer launch it.

---

### Post by Hungry Man on 2013-04-13
Is there a way to update-grub from the grub interface - preboot? Might help me.

---

### Post by ronald577 on 2013-04-13
No i don't think there is any update for the grub interface preboot.

---

### Post by Hungry Man on 2013-04-13
Hm. I may just be stuck having to reformat the partition. What a shame. Oh well, I'm resigned to it.

---

### Post by Hungry Man on 2013-04-16
So this happens on a vanilla kernel on 13.04. I think it may simply be a 13.04 problem... are there beat drivers?

---

### Post by Mark Phelps on 2013-04-16
Ubuntu 13.04, and now 12.04.2, brought with them a new X-server version which is NOT compatible with the fglrx drivers for AMD cards older than the HD 5x series.  So, if yours is an HD 4x or older, it's not going to work with fglrx drivers in 13.04 -- and won't in the future because AMD is not going to update their legacy card drivers.

---

