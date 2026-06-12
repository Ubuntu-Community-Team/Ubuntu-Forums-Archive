---
title: "Problem with close bracket"
date: 2013-07-31
forum: General Help
---

### Post by MibunoOokami on 2013-07-31
Hi everyone, it's good to see the site up and running again.

Long story short, my wife's netbook has started experiencing a problem, where the close bracket ] button seems to be stuck, only it's not. I've cleaned the keyboard and the problem is still there. It seems to be an intermittant problem that first occurs when you turn the netbook on, it beeps heaps thinking the button is being pressed and then it spends a few minutes writing heaps of close brackets and it is a bit frustrating for my wife, particularly when she's trying to login to check her emails but her password box is filled with close brackets.
My guess is that it's a software problem and I wonder if I could just use xmodmap or something to disable the key, but first I'd like to hear some thoughts on what might be causing this.

Thanks all

---

### Post by lah7 on 2013-07-31
If the system has a series of beeps as soon as the netbook is turned on, I would think that the POST (**P**ower-**o**n **s**elf-**t**est, before Ubuntu is loaded) is detecting the key being stuck, and beeps as a warning. I've seen this happen before with the ESC key on a laptop before. If that's the case, it's likely to be either hardware failure or the key itself is damaged. Try taking the key off and check it's mechanics; test without the keyboard connected or consider buying a replacement keyboard for the laptop.

You may be able to block the key software-wise, but this doesn't really resolve the problem. I would suggest checking the hardware itself first, since it's likely to be a fault with the key itself or the keyboard.

---

### Post by CaptainMark on 2013-07-31
The easiest way to tell if something is a hardware or software problem is boot up a live cd, preferably of a completely different family from what your using and different kernel version. Better still use a BSD live cd. If the problem is still persistent then it's definitely your hardware.

I agree with lah7 though, if the beeps are occurring during the POST then its probably hardware, I sympathise with you, I have a laptop with the same problem on the Ctrl key, it's pretty much useless now

---

### Post by MibunoOokami on 2013-08-01
> **lah7 said:**
> <snip> Try taking the key off and check it's mechanics; test without the keyboard connected or consider buying a replacement keyboard for the laptop.

I can't seem to get the key off, I think it's going to break before unclipping, so I'll try disconnecting the keyboard instead.

> **CaptainMark said:**
> The easiest way to tell if something is a hardware or software problem is boot up a live cd, preferably of a completely different family from what your using and different kernel version. Better still use a BSD live cd. If the problem is still persistent then it's definitely your hardware.

I agree with lah7 though, if the beeps are occurring during the POST then its probably hardware, I sympathise with you, I have a laptop with the same problem on the Ctrl key, it's pretty much useless now

Startup disk creator doesn't seem to want to burn the BSD ISO image to USB, that might be because it lists the Ubuntu one first and I don't know how to clear it. Will the startup disk creator create startup disks for other linux versions?
My wife's netbook wouldn't boot from the external cd drive I attached, even after I included it in the boot order list and put it as the first thing to boot from.

---

### Post by lah7 on 2013-08-01
> **MibunoOokami said:**
> I can't seem to get the key off, I think it's going to break before unclipping, so I'll try disconnecting the keyboard instead.
Do let us know how it goes without its keyboard connected. It'll be even better if you do have a USB keyboard handy to try. This will definitely determine if it's a hardware vs software problem.

> **MibunoOokami said:**
> Startup disk creator doesn't seem to want to burn the BSD ISO image to USB, [COLOR=#000000]Will the startup disk creator create startup disks for other linux versions?[/COLOR]
I forgot about USB Startup Creator :roll: I use the disk utility* [gnome-disks] *to image ISOs directly to USB flash drives, and that still does the trick, since I mainly install from USB drives. Note that doing this method below doesn't create a session that you can "reuse" (it's essentially just how a CD would handle, discarding data upon shutdown, which is fine for loading a live session only)

1) Type "disks" into the Ubuntu dash.
2) Select your USB drive on the left, press the **cogs** at the top-right, then click **"Restore disk image..."**
3) Select the ISO, this can be _any_ linux distrubuton, not just Ubuntu.
4) Wait for the image to be imaged across.
--- That's an alternate way to image the ISO if Startup disk creator isn't behaving for you.

---

### Post by MibunoOokami on 2013-08-01
> **lah7 said:**
> <snip>Do let us know how it goes without its keyboard connected. It'll be even better if you do have a USB keyboard handy to try. This will definitely determine if it's a hardware vs software problem.

I removed the keyboard and have restarted the netbook twice, there have been no beeps at start up and no close brackets appearing in any windows accessable with a mouse. When you say hardware you're just talking about the keyboard right? Or is there also other hardware associated with the keyboard? My hardware knowledge is lower than my software knowledge.

Thanks.

<edit> It looks like the keys are held in place with little metal clips made from the aluminium base.

---

### Post by CaptainMark on 2013-08-02
It's probably just the keyboard but unfortunately replacing a laptop keyboard can be expensive business. I think the USB creator package only works on Ubuntu based distros, I've never been able to make an open suse live USB with it, you can try Unetbootin if you're still going down this route, it's installable straight from the software centre

---

### Post by lah7 on 2013-08-02
> **MibunoOokami said:**
> When you say hardware you're just talking about the keyboard right? Or is there also other hardware associated with the keyboard?

From the responses it definitely looks like you've got a faulty keyboard on the unit, the PC itself is fine. If it's under warranty, you can try getting a replacement and it'll solve the ]]]]]]]]]]] nightmare. Like CaptainMark said, it could be quite expensive. :(

You could live with it, or try re-positioning or leaving the key off and attempt to repair yourself. Although faults like this are not easy to fix. It could be pressure between the key and the contacts, since it's repeatedly touching and the keyboard thinks you're pushing the key. If it's happened ever since you've first used the device, it may well had problems during the manufacturing.

*This sort of thing happened with my auntie's laptop, the ESC key (even worst!) kept closing windows and beeping during start-up, it never had Ubuntu on either, and pressure on the side of the unit helped or sometimes didn't.* It's going to be a bit fiddly.

---

### Post by MibunoOokami on 2013-08-03
> **CaptainMark said:**
> It's probably just the keyboard but unfortunately replacing a laptop keyboard can be expensive business. I think the USB creator package only works on Ubuntu based distros, I've never been able to make an open suse live USB with it, you can try Unetbootin if you're still going down this route, it's installable straight from the software centre

> **lah7 said:**
> From the responses it definitely looks like you've got a faulty keyboard on the unit, the PC itself is fine. If it's under warranty, you can try getting a replacement and it'll solve the ]]]]]]]]]]] nightmare. Like CaptainMark said, it could be quite expensive. :(

You could live with it, or try re-positioning or leaving the key off and attempt to repair yourself. Although faults like this are not easy to fix. It could be pressure between the key and the contacts, since it's repeatedly touching and the keyboard thinks you're pushing the key. If it's happened ever since you've first used the device, it may well had problems during the manufacturing.

*This sort of thing happened with my auntie's laptop, the ESC key (even worst!) kept closing windows and beeping during start-up, it never had Ubuntu on either, and pressure on the side of the unit helped or sometimes didn't.* It's going to be a bit fiddly.

Whew, replacing the keyboard is ridiculous expensive :shock: and unfortunately it's no longer under warranty. My wife primarily uses it at a table only moving it now and then, so she either have a USB one or we'll just buy a new netbook.
Thanks for your help guys.

---

