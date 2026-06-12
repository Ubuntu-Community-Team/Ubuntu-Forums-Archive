---
title: "Video / display problems in vmware"
date: 2006-11-04
forum: General Help
---

### Post by jrjazzman on 2006-11-04
I'm running vmware workstation on dapper.  My guest os is win xp.  In xp, I'm experiencing some strange problems that seem to be related to the display:

- Cursor doesn't blink. It's either stuck on or off. Off is bad, cuz you can't see where you're typing
- Tooltips on menu buttons, etc. don't appear.
- When I launch a build in visual studio, it hangs for about 10 seconds. Once the build starts, it seems as fast as normal. 
- Any type of slide, fade or window animation (eg the maximize/unmaximize animation) is very slow. And I'm not talking about directx type stuff.. this is just the basic stuff that comes with xp, visual studio, eclipse, etc. 
- Various other animations, such as the progress bar in the starting windows screen are very slow.  I don't really care about this particular progress bar.. just another symptom.
- Windows Start menu. When you are hovered over a menu item that has a sub-menu, it takes a long time (10 seconds - never) for the menu to to fly out.


I've tried vmware workstation, server and player.  The problems exist on all editions.  I've also tried creating a new vm and reinstalling Windows.  I'm on a laptop with i915 video.  I don't seem to have any issues in the host, Ubuntu.  

Any ideas what could be causing this?

---

### Post by philippe_carlo on 2006-11-04
Can you describe you hardware (your real one - not the virtual one)? Also, how much RAM memory did you assign to windows XP? Anything less than 256 is not going to give reasonable performance. For 'building purposes', that minimum is raised to 512MB, and probably, 786 is better. You processor should be be fast enough, it works fine on my ~1.6 GHz Centrino. But it really shouldn't be much less.

---

### Post by jrjazzman on 2006-11-04
> **philippe_carlo said:**
> Can you describe you hardware (your real one - not the virtual one)? Also, how much RAM memory did you assign to windows XP? Anything less than 256 is not going to give reasonable performance. For 'building purposes', that minimum is raised to 512MB, and probably, 786 is better. You processor should be be fast enough, it works fine on my ~1.6 GHz Centrino. But it really shouldn't be much less.

thosiba satellite laptop
Pentium M processor 1.86 ghz
2 gb ram
100 gb hd
intel i915 video

I gave 1 gb to windows.  The only hardware issue that I know of is I get 89 fps on glxgears in full screen.  But that's 3d, and shouldn't make a difference with vmware.  My 2d video speed seems fine in linux.  The problem doesn't seem to be video.  Some things are just *too* slow for it to be video.

---

### Post by gruffy-06 on 2006-11-05
You may want to install VMware Tools inside the guest OS. Click on VM>Install VMware Tools. This significantly increases the performance inside the guest OS.

You should also disable any transitioning effects inside the guest OS, like fading tooltips, anti-aliasing and smooth-scrolling. This should also increase performance.

---

### Post by jrjazzman on 2006-11-05
> **gruffy-06 said:**
> You may want to install VMware Tools inside the guest OS. Click on VM>Install VMware Tools. This significantly increases the performance inside the guest OS.

You should also disable any transitioning effects inside the guest OS, like fading tooltips, anti-aliasing and smooth-scrolling. This should also increase performance.

I've already done the things you mention.  There's only so much you can turn off though.  My cursor doesn't blink, no tooltips, start menu doesn't know you're sitting on a sub-menu that should be opened, etc.  These don't  seem like video performance issues.  Seems like there's some other problem.

---

### Post by jrjazzman on 2006-11-15
I was able to fixed this and would like to post the solution in case anyone else has this problem.  

It was caused by the system dropping into slow ACPI states.  For some reason, the system doesn't realize that the VM needs CPU power, so the processor gets slowed down a lot.  Here's how I solved it:



```
#!/bin/bash
# this script fixes the problem of the computer going into lazy acpi modes
gksudo chmod o+w /sys/module/processor/parameters/max_cstate
gksudo echo 1 > /sys/module/processor/parameters/max_cstate 
/usr/bin/vmware
gksudo echo 8 > /sys/module/processor/parameters/max_cstate 

```

You can put this in a file and run it instead of your normal way of starting vmware

---

