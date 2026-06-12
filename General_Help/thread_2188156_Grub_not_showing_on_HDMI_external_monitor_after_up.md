---
title: "Grub not showing on HDMI external monitor after updates."
date: 2013-11-15
forum: General Help
---

### Post by im_not_special on 2013-11-15
I'm stuck.
 
I include the following information as background because I have no idea were the problem is occuring.
 
I run a home rolled 12.04 remix with the gnome tool set grafted on to  the XFCE4 DE. I run the lts-quantal kernel so that I always track the  latest lts kernel (current = 3.5.0-43-generic / 3.5.0-43.66). I have  hybrid graphics with bumblebee-nvidia / nvidia 319.32.
 
I usually use my system (laptop) with the lid closed and plugged in to  an HDMI external monitor that is hard ported through an onboard  mini-display port to a mini-display to HDMI adapter. This set up ports  the "heavy" rendering to the DGPU for rendering through an internal  transparent proxy for rendering then ports the results back to the IGPU  for display which I then pull off of the IGPU through the mini-display  port / HDMI adapter.
 
I also have boot repair installed, but have not had to use it in several months.
 
Until recent updates, while running this set up, on boot my GRUB menu  would show on both my laptop screen (if it the lid was up) and my  external monitor at the same time; which is what I want.
 
After the updates GRUB will only show on my laptop screen with the lid either open or closed. I have it set  up for no splash and to show GRUB and everything loading as the system  boots (no "quiet"). All of it used to show on the external monitor after  power up from GRUB forward. 
 
Now stuff only shows on the monitor after GRUB boots the OS (after a 10  second delay) and starts to load / initialize the system. In other words  I am getting output on the monitor before the x-session is initalized,  while still in CLI mode, but only after GRUB boots the OS.
 
I had a big set of updates recently, so I'm not sure what broke it. The  GRUB configuration is correct and shows on the laptop screen as I want  it to. I checked bumblebee config and did not see any obvious changes  from the way I set it up originally when everything used to show on the  external monitor. I tried rolling back the kernel, but that did not fix  the issue. I also tried editing GRUBs parameters on the fly at boot to  change the video mode to see if I could get the GRUB output to show on  the external monitor. I tried setting i915.modeset=1, i915.modeset=0,  nomodeset and xforcevesa; none of these fixed the issue and all of them  caused various problems with the x-session once it was initialized.
 
I don't see anything obviously wrong and I'm out of ideas.

---

### Post by jamesisin on 2013-11-15
Have you been able to determine which packages were updated during that particular update?

---

### Post by im_not_special on 2013-11-16
Not yet. I had been lazy and hadn't updated for a while and had 70+ updates due. Is there an easy way to tell what was updated when?

-----------
Edit: NM, I found the update history in the software center. But I'm still not seeing any obvious canidates for having caused the function to have stopped working.

---

### Post by jamesisin on 2013-11-16
One possibility might be to roll back and add them in one at a time (ugh) until it breaks again.

But none of them were either grub or video related?

---

### Post by im_not_special on 2013-11-17
Not as far back as the history went; which was not very far. It was only the last three times I did updates. But it could have been an update before that that broke it. I sometimes go several weeks or even a couple of months without a reboot so I wouldn't have noticed after a round of updates if none of them required a reboot. The only recent update to have anything even remotely related to do with GRUB was for boot repair. But I don't see why that would break this.

I believe there was an update to GRUB itself a while back. I don't remember if it required a reboot. 

I tried using boot repair to purge / reinstall GRUB; which did not fix it.

What I find odd is that I can see CLI mode after OS boot. That makes me think the issue is isolated to GRUB and is not a driver / other issue.

I'm wondering if there is a way that I can change the graphics properties just for GRUB and not for the system as a whole. I.E., when I edited GRUBs boot properties on the fly at boot (nomodeset, etc) I changed the boot properties of the entire system and caused problems with the x-sessions. 

Is there a synatx I can insert in to the GRUB config that will change just the video properties of GRUB itself, but not effect the system as a whole.

I'm also wondering what effects to the system, if any, would be caused by changing to LILO or GRUB legacy? I haven't played with either one yet. Can 12.04 handle either one? Can boot repair handle GRUB legacy? Is there a program for fixing LILO? I like boot repair.

---

### Post by jamesisin on 2013-11-18
I shouldn't think the OS would have any clue which boot-loader you were using.  That being said, I'm surprised that changes you make in GRUB, vis-a-vis GRUB's video display mode, carry over to the OS itself.  Hmmm... maybe GRUB hands that off to the OS during boot.  If that's the case, perhaps there is a way in the OS to override what GRUB hands off?

---

