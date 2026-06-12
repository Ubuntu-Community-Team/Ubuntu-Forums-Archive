---
title: "Could I run Windows XP and WinTV2000 inside a virtual machine??"
date: 2007-02-17
forum: General Help
---

### Post by presbp on 2007-02-17
I ordered a Hauppauge WinTV-PVR-150 but I got the HVR-1600 in the box.  So that happening I can only use the TV tuner in Windows.  

I was wondering if I could use QEmu and install Windows XP on my external harddrive as a virtual OS or machine or whatever it is called, install the card drivers for the HVR-1600 and the WinTV programs and have it so I can record my TV shows to my hard drive using Windows as  virtual machine and then do everything else in Ubuntu?

Being able to record my shows and watch TV on Ubuntu would be very useful indeed, especially since I am using games less than I used to.. so that most of the time when I am in Windows it is just because my shows are recording.  

Thanks alot

---

### Post by MoLE on 2007-02-17
Sadly, it's not possible.  One of the reasons why it's so important to check you have linux-compatible hardware before you buy.

Both Qemu and Vmware virtual machines emulate an entire system of hardware in software, and are thus abstracted from the underlying hardware the host OS runs on.

You're obviously in the same boat as quite a few people over on the [mythTV forums]("http://www.mythtvtalk.com/forum/viewtopic.php?t=4666&start=0").

The sad thing is that the PVR-150 works under linux.

If it was me, I'd be RMAing the card for what I actually ordered.

---

