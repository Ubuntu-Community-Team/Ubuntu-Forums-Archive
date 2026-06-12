---
title: "Screen corrupted / fuzzy on boot.  Driver issue.  How to change?"
date: 2019-06-26
forum: General Help
---

### Post by derek11 on 2019-06-26
I'm having issues with getting a driver to load or work properly with the Intel 4500MHD graphics. I am cycling between Ubuntu and Mint, and have the same issue on either one.

Specifically, when the machine boots, 9 times out of 10, I will end up with a fuzzy screen of messed-up text. Maybe 1 time in 10, I can get it to complete the boot process and work just fine, until I shut the machine down. If I keep the machine awake, or coming out of sleep, I am fine, once it's working. 

I have determined that no proprietary drivers are installed for my Intel graphics. I followed some older threads, and tried adding nomodeset to the grub, and it allowed me to boot properly every time, but only at 800x600 resolution, with no way to change it. Not liking this, I have removed nomodeset and put it back to as it was.

I am seeking help to understand how to load the proper Intel driver on this computer. What I have found online states that Intel has a kind of tool or package to help identify and install the driver properly, but it is written for someone who knows more than I do about installing packages (I'm clueless). For example, I don't understand when a webpage says, "just install the package..." because I don't even know how to do this correctly. 

In short, I am such a newb that I require line-by-line instructions as to what to type.

Any help or ideas would be appreciated!

---

### Post by CatKiller on 2019-06-26
> **derek11 said:**
> I am seeking help to understand how to load the proper Intel driver on this computer. 

Good news! You already have the "proper Intel driver" installed on your computer, so you can stop trying to do that. It's part of the kernel.

It sounds like your computer is failing to get EDID from your monitor (or laptop screen, with that part?) Since it's working *sometimes* it seems more likely to be a cabling issue than a configuration issue. You could try specifying the mode information that would normally be provided by EDID yourself, anyway, though, to see if it helps.

---

### Post by derek11 on 2019-06-27
Thanks for the reply. Any idea how to provide the EDID?

Oddly, I have found others who have had a similar issue, in old threads, and the consensus was it's a driver issue.  Problem is, they never 100% explain how they fixed it, in a way that I can implement.  

And if it's just a cable, then why is it that I have zero issues (for days) closing/opening the cover after it loads properly, and only have issues at boot?

---

### Post by CatKiller on 2019-06-27
> **derek11 said:**
> And if it's just a cable, then why is it that I have zero issues (for days) closing/opening the cover after it loads properly, and only have issues at boot?

The negotiation and retrieval of the EDID happens when the display is set up; all the time the computer is on or suspended it's still using that configuration. When you reboot, it sets up the display again. 

It's possible that the monitor is arbitrarily giving false information 90% of the time for reasons of its own, but it seems much more likely to be that the signalling for the negotiation is interrupted by bad cabling. 

Ctrl-Alt-Backspace restarts the X server. That may have the same effect as your repeated restarts, but be quicker. 

> Any idea how to provide the EDID? 

You can either use the manual to find the HorizSync and VertRefresh ranges (EDID contains more, but that's often the critical bit) and put that in xorg.conf; or save the EDID from a time when it's loaded successfully, using a tool like read-edid, and specify that file in xorg.conf. An alternative is to specify a full modeline in your xorg.conf calculated using the CVT formula.

xorg.conf isn't there by default, but will be used if you provide one. You might even be able to get away with just a Monitor section snippet in xorg.conf.d rather than creating a full xorg.conf.

---

