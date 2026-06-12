---
title: "Ubuntu has become too slow for me"
date: 2007-10-22
forum: General Help
---

### Post by d3dtn01 on 2007-10-22
A couple of months ago, I noticed that my Ubuntu OS (which at the time was the Feisty version) was becoming really slow. Apps loaded slow, switching between apps was slow, everything was slow. It got so annoying that I switched back to Windows for the past 2 months. So when I heard that Gutsy was out, I upgraded to see if anything would change. No change. It's still terribly slow. It was never like this before. I don't remember doing any major installs that could have changed the performance. 

Are there any obvious things to do to troubleshoot this problem? I'm tempted to just reinstall Ubuntu from scratch, especially since my wireless stopped working around the same time. But then I'm afraid that all my previous hacks (like getting my headphones to work) will be wiped out and I'll have to do them again. Hm, what to do.

---

### Post by steveneddy on 2007-10-22
Test your memory and have the HD checked out.

Ubuntu should not be slow, especially if you have two totally different installs from two different versions on the same PC, it must be a hardware issue.

:popcorn:

---

### Post by d3dtn01 on 2007-10-22
I have windows XP running on the other half of my machine and it runs fine (not slow at all). So I'm guessing it's probably not entirely a hardware issue.

---

### Post by dayvy on 2007-10-23
If your XP is running fine then it's not the hardware. It could be any number of things, i.e. buggy module, xorg or compiz issue, an application that's hogging all the resources. It's hard to say without some investigation. First thing to do is open a terminal and type: top 

This will show you what is running and how much of the resources are being used by each process. End this by hitting Ctrl C.

Disable "Visual Effects" and see if that makes a difference.

Make a list of your hardware and investigate the modules that are loaded. 

lshw (this will list the hardware in your system)

lsmod (this will list the modules loaded)

This is a place to start. The long and short of it is it's going to take some investigation. Do you have any unusual hardware installed?

d.

---

### Post by d3dtn01 on 2007-10-25
dayvy,

you rock. Thanks for the troubleshooting suggestions. I'll try them tomorrow. These are the type of ideas I was hoping to find.

---

