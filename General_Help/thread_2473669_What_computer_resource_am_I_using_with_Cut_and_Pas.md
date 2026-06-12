---
title: "What computer resource am I using with Cut and Paste"
date: 2022-04-09
forum: General Help
---

### Post by raul-mccai on 2022-04-09
I'm using Audacity an audio editing manipulation software and cutting and pasting large blocks of sound from one window to another.
 The details are, I think, irrelevant.
I know I am using a computer resource when I put that much data in a cut and paste of different materials recursively.
The thing I'm trying to fix is a slowing  down of the response time  on Paste
When I start out it is fast and after a while, it slows down dramatically. I'll position my cursor hit CTL and v,  and it takes forever to paste. 

So what is that resource?  
I was sure it is the Memory cache.
But when (in root) and I clear the page cache, the inodes, and memory buffers the lag time does not improve.
But now I think I'm wrong.  
Any other things I could be clearing to speed things up? 
thx

---

### Post by TheFu on 2022-04-09
disk i/o and storage, is my guess.  Audacity edits with uncompressed audio.
Set the temporary scratch storage used by audacity to be on the fastest storage you have. That would ideally be an NVMe SSD.  Also, ensure there is plenty of room available in that partition and when you are done with a project, clean up the project files in the scratch area.

---

### Post by Impavidus on 2022-04-10
I don't know Audacity very well. If you cut and paste, are the data put in the system clipboard or only in a clipboard internal to Audacity? My guess is the latter. Plain text can be copied to the system clipboard, but other applications wouldn't know how to paste audio, so copying it there doesn't make sense. So it's just copied to RAM used by audacity. Eventually, RAM will get full and the system will use swap, slowing things down. Does Audacity properly delete old copies whenever you create a new copy, or does it keep a number of old copies? Some applications do.

Keep an eye on RAM use when using Audacity. I think this has to be fixed in Audacity itself, not via other parts of your system.

---

### Post by raul-mccai on 2022-04-11
> **Impavidus said:**
>  the system will use swap, slowing things down.

Thx 
I'll try **swapoff -a **and **swapon -a  **and see if that speeds things up.

---

### Post by TheFu on 2022-04-11
> **raul-mccai said:**
> Thx 
I'll try **swapoff -a **and **swapon -a  **and see if that speeds things up.

I doubt it will.  Did you set the temporary directory for work files to the fastest storage you have?  I've worked with Audacity.
If you don't want to swap, buy more RAM. It isn't too expensive now.

---

