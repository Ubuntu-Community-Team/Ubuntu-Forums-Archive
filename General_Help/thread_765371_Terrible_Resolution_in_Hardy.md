---
title: "Terrible Resolution in Hardy"
date: 2008-04-24
forum: General Help
---

### Post by Puppy fam on 2008-04-24
I just installed Hardy and I can't find a way to get my screen resolution over 640x480 with my nVidia driver enabled. Compiz effects work great, but the screen resolution utility won't let me go any higher than 640x480. Clicking on "Detect displays" does absolutely nothing. I have a huge, old CRT for my monitor... Could that be the problem?

Thanks!

---

### Post by upthelum on 2008-04-24
I can get a decent resolution but cant enable desktop effects or extras.

---

### Post by chrisccoulson on 2008-04-24
There seem to be a few people with NVIDIA cards with this problem.

Out of interest, what model is your CRT?

---

### Post by upthelum on 2008-04-24
I use a Phillips 190X5 19" monitor with Nvidia 7600GS which runs my host Linux fine but not so in VMWare. Other vmware images i use run fine so im sure its a teething problem, i dont really have time just now to play with hardy and get it set up the way i want, but will.

---

### Post by Puppy fam on 2008-04-24
It's a KDS (yeah, I've never heard of them either). Thankfully, I've figured out this issue: I had to use the "Screens and Resolutions" utility that's hidden in the "Other" menu under "Applications."

Now, off to figure out why the heck my USB drive isn't being recognized...

---

### Post by chrisccoulson on 2008-04-24
> **Puppy fam said:**
> It's a KDS (yeah, I've never heard of them either). Thankfully, I've figured out this issue: I had to use the "Screens and Resolutions" utility that's hidden in the "Other" menu under "Applications."

Now, off to figure out why the heck my USB drive isn't being recognized...

What you have done isn't a fix though - merely a workaround. For the benefit of other users, please report this as a bug on Launchpad. The Screens and Graphics tool is using the heavily deprecated Xinerama and can lead to completely broken Xorg configs. Xorg should correctly detect your monitors resolution, and if it doesn't, then this is a bug.

---

### Post by hessiess on 2008-04-24
should be able to edit etc/X11/xorg.conf manualy to get the resolution you want ;)

---

### Post by Teber on 2008-04-24
i have a similar problem, except that in my case the highest possible screen res is 1024x768, which should be 1280xsoemthing (forgot the exact number) reported it a stated earlier. hope this will be fixed soon.

---

