---
title: "Virtual Machine loading very slowly. Why?"
date: 2007-12-10
forum: General Help
---

### Post by Robbyx on 2007-12-10
I think I must have made an adjustment at some time to speed up Fiesty. I use Win2k in a VMplayer virtual machine. It has taken to loading very slowly, it used to be much faster. I always use the suspend to disk option when closing because that avoids reloading Windows. 

Are there any suggestions as to where I should look to speed it up?   The slowness is making VMplayer difficult to use with ease.

Robin

---

### Post by p_quarles on 2007-12-11
Have you tried defragmenting the virtual drive? Windows will always slow down as the fragmentation increases over time, and the virtual drive is being treated by Windows exactly like a "real drive." 

That said, I'm not sure what you mean about using "suspend to disk" to avoid reloading Windows. Does it automatically reload if you power off the virtual machine as normal? (I use Virtualbox for my VMs, so perhaps this is just my lack of familiarity with VMWare).

---

### Post by Scunizi on 2007-12-11
I've noticed the same and have thought that defragging will make a difference.  Probably will.  I'd also suggest that you look at how much "disk" space is being used in the VM.  If you're close to the limit it might cause issues.

---

### Post by HermanAB on 2007-12-11
Some things to check:
Disable USB
Disable unused drives: CD, Floppy
Disable concurrent snapshots (this one is a killer)

When you create a machine, always allocate the whole disk.

Cheers,

H.

---

