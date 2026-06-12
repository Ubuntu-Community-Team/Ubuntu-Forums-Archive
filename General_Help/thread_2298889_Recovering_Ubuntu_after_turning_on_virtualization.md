---
title: "Recovering Ubuntu after turning on virtualization"
date: 2015-10-14
forum: General Help
---

### Post by david_edwards2 on 2015-10-14
I've done a lot of searching trying to find out how to recover my Ubuntu installation after enabling virtualization, however I have seemingly struck-out.

I have duel-booted Ubuntu and windows 8.1 on my laptop of course using the grub boot-loader to go between. However about 2 weeks ago, I had to enable virtualization to use the android emulator. When I turned this on, my laptop booted straight into windows. Which was fine at the time, I got done what I needed to get done. However I have recently disabled virtualization in an attempt to be able to use Ubuntu again only to find myself still staring at a windows loading screen. 

My first thought is that I need to re-install grub, but I'd like to be able to avoid that if at all possible. Any insight into my situation would be much appreciated!

---

### Post by ian-weisser on 2015-10-14
I do not understand what you mean by "Turn on virtualization."
What, exactly, did you do?

---

### Post by david_edwards2 on 2015-10-14
I went into the BIOS and enabled the virtualization technology on my laptop. 

[IMG]http://cdn.sysprobs.com/wp-content/uploads/2009/10/virt_bios.gif[/IMG]

---

### Post by mastablasta on 2015-10-15
nope. GRUB loads after BIOS. they do not interact much other than when BIOS hands over it's motherboard to Grub. in your case for some reason it doesn't even get to Grub.

I would check instead that some sort of fast boot is not enabled in windows 8. I think by default windows 8 actually hibernates when you perform a "shutdown"

reinstalling grub is easy with boot repair tools, but like I said make sure you do not have some fast boot or any other windows boot features that makes the OS more awesome turned on :)

another option (but I am not expert on this) is that one of the windows updates overwrote the grub.

by the way - I kept virtualisation on. you  need it to run 64bit OS in vbox.

---

### Post by david_edwards2 on 2015-10-18
> **mastablasta said:**
> nope. GRUB loads after BIOS. they do not interact much other than when BIOS hands over it's motherboard to Grub. in your case for some reason it doesn't even get to Grub.

I would check instead that some sort of fast boot is not enabled in windows 8. I think by default windows 8 actually hibernates when you perform a "shutdown"

reinstalling grub is easy with boot repair tools, but like I said make sure you do not have some fast boot or any other windows boot features that makes the OS more awesome turned on :)

another option (but I am not expert on this) is that one of the windows updates overwrote the grub.

by the way - I kept virtualisation on. you  need it to run 64bit OS in vbox.

Thank you for helping me understand this a bit more, everything is up and running!

---

