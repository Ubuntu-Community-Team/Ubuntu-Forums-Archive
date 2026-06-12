---
title: "Grub Customizer stopped working with 12.04.4 kernel 3.11.0-19"
date: 2014-04-05
forum: General Help
---

### Post by 2CV67 on 2014-04-05
Afew weeks back, I made a clean install of 12.04.4 with kernel 3.11.0-15, dual-booting with W7 on an Asus Eeepc netbook.
I updated it to the then current kernel 3.11.0-17 & installed Grub Customizer, which I successfully used to get the grub screen arrangement I want.

Today I updated to kernel 3.11.0-19 & tried to tidy up the grub screen, but Grub Customizer no longer controls things.
I made the changes I wanted in GC & saved them, but the grub screen is unchanged.
When I open GC, 'list configuration' shows me what I want, but not what is on the screen!
GC is now version 4.0.4 which is the same as I am using successfully on another PC with 13.10 and the same kernel 3.11.0-19.

I looked for the /boot/grub.cfg file & was surprised to find I have 2!

There is /boot/grub.cfg - which looks like the actual grub screen
& also /boot/grub.cfg.new - which looks like what GC is showing me & what I want to have.

I suppose I can always just rename the files, but I would rather understand & fix the underlying problem, if possible.

Is there a good explanation for this situation?

Thanks!

---

### Post by akmartinez1 on 2014-04-11
I might be having slightly the same issue but I do not see 2 cfg files and I didn't update anything that I could tell.

My Grub Customizer was working fine until I decided to change the background image that I was using.  Once I changed it in Grub Customizer my changes to colors and images stopped working but I am still able to change the boot order of my OS's.

So what's not working for me is changing the font colors, highlight colors, and background images, at least from what I can tell so far.

Running a dual boot system with Win8.1 and Ubuntu 13.10.

---

### Post by 2CV67 on 2014-04-11
As I couldn't find any clues for my problem, I ran 'Boot Repair' & accepted the usual  recommended fix.
That removed & purged grub (& GC) then reinstalled grub.
I reinstalled GC & it now works OK.

So - no idea what the problem was, but it went away with new clean grub & new GC...

---

### Post by akmartinez1 on 2014-04-11
I'm still very new to Ubuntu and Linux, could you tell me how you ran the Boot Repair?
I could probably look it up but would like to know how you did it just in case I find something different.
I'll probably give it a try.  Will it work on a dual boot setup?  Or will it mess up my Win8.1 boot?

Thanks,

---

### Post by erind on 2014-04-11
> **2CV67 said:**
> As I couldn't find any clues for my problem, I ran 'Boot Repair' & accepted the usual  recommended fix.
That removed & purged grub (& GC) then reinstalled grub.
I reinstalled GC & it now works OK.

So - no idea what the problem was, but it went away with new clean grub & new GC...

I have the same problem and my workaround is the same, run Boot-Repair,  purge and reinstall grub - but still it's just an awkward workaround - the thing is that the same issue will come up again in the next kernel upgrade. 

From what I've seen, this is a problem/bug ( either Grub2 or Grub Customizer ), with no fix yet. So I'll do some testing on my own when the next kernel upgrade is due, will run Grub-Customizer and see what creates the extra file ***grub.cfg.new***. Hopefully I'd find something. Last time I tried to rename this file to ***grub.cfg*** (as far as I remember) didn't change a thing, so I had to run Boot-Repair again.

---

### Post by 2CV67 on 2014-04-12
> **akmartinez1 said:**
> I'm still very new to Ubuntu and Linux, could you tell me how you ran the Boot Repair?
I could probably look it up but would like to know how you did it just in case I find something different.
I'll probably give it a try.  Will it work on a dual boot setup?  Or will it mess up my Win8.1 boot?

Thanks,

I think your problem may not be the same as mine, so I wouldn't recommend letting Boot Repair completely wipe your grub just yet, as there a is always a risk of no boot after that!

Why not try removing & reinstalling Grub Customizer first?

I would do that via Synaptic package manager, using the 'Completely Remove' option.

If that doesn't work, you could run the analysis part of Boot Repair & post the output of that in the appropriate forum.

Information on Boot Repair is here:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

My reason for warning before allowing actual repair is that you MUST know where you want to reinstall grub after it has been wiped out & you may not know that answer.

I am NOT an expert on any of this, so if anybody else can help...

---

