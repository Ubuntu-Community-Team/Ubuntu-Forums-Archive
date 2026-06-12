---
title: "Ubuntu freezes during boot, after upgrading video card"
date: 2020-02-06
forum: General Help
---

### Post by qkelly on 2020-02-06
Hello, I just upgraded my video card and now when Ubuntu starts trying to boot, it freezes. :(

My old video card was an NVIDIA GeForce GTX960. My new video card is an NVIDIA GeForce 1660 SUPER. Other system vital stats:

Ubuntu version: 18.04 LTS
CPU: Intel core i5-8400
motherboard: ASUS Prime H370M

When I power on the desktop, I get my manufacturer splash screen as normal. Next, Ubuntu starts booting as normal (I can tell by the purple-ish black color of the screen). But then, a few weird colored lines appear and the screen freezes:

[ATTACH=CONFIG]284979[/ATTACH]

I can get to my UEFI BIOS settings, and I can also get to GRUB without issue. This makes me think that this is a software issue, rather than a hardware issue. I've booted into recovery mode and run "sensors" to verify that the core temperatures are all within normal ranges, between 28-38 degrees C. I've also reset the BIOS settings to defaults, but that hasn't helped.

Do I need to install the NIVIDIA driver from recovery mode? If so, what command do I need to use to do that? I've been searching, here and on other forums, for the right command but I'm only seeing very old posts on it.

---

### Post by CatKiller on 2020-02-06
Which driver version were you using? I know that Turing didn't get any support at all till the 410 branch, and the 1660 came out quite a bit after that. Whichever driver branch was current in spring 2018 would have been fine for your 960, but not for a new card.

If you were on a driver branch that was too old you can switch to a different one from the root shell that you can invoke from the Grub menu, or from a live USB if you chroot to your install. Note that you can't cleanly go from one branch of the Nvidia driver to another: you need to purge all the nvidia stuff from the old one and then install the new one, otherwise it doesn't work. I think, although I haven't checked, that the standard repositories go up to either the 430 or 435 branches. You can add the graphics drivers PPA if you want the 440 branch.

It's also possible that it's not driver related at all, and you forgot to plug in the extra power connectors or something.

---

### Post by qkelly on 2020-02-06
> **CatKiller said:**
> Which driver version were you using? I know that Turing didn't get any support at all till the 410 branch, and the 1660 came out quite a bit after that. Whichever driver branch was current in spring 2018 would have been fine for your 960, but not for a new card.

If you were on a driver branch that was too old you can switch to a different one from the root shell that you can invoke from the Grub menu, or from a live USB if you chroot to your install. Note that you can't cleanly go from one branch of the Nvidia driver to another: you need to purge all the nvidia stuff from the old one and then install the new one, otherwise it doesn't work. I think, although I haven't checked, that the standard repositories go up to either the 430 or 435 branches. You can add the graphics drivers PPA if you want the 440 branch.

It's also possible that it's not driver related at all, and you forgot to plug in the extra power connectors or something.

Hi CatKiller, thanks for the quick reply! I did make sure to plug in the supplementary power connector on the 1660 card. As for what branch of the driver I'm using, I'm not sure. I did just switch my DVI cable over to my onboard video card, so I can at least boot up normally for now. When I id, I ran "sudo lshw -c video" and it says "driver=nouveau" for my NVIDIA card. Does that help?

---

### Post by CatKiller on 2020-02-06
> **qkelly said:**
> When I id, I ran "sudo lshw -c video" and it says "driver=nouveau" for my NVIDIA card. Does that help?

Well, yes. It means you aren't using the proprietary driver at all yet. Your best bet would be to treat it like the first boot after a fresh install; add *nomodeset* temporarily to your Grub boot line to boot up into a low-resolution desktop, add the PPA, install the latest driver branch (440, currently) and then reboot.

---

