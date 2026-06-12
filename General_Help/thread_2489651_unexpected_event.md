---
title: "unexpected event"
date: 2023-08-05
forum: General Help
---

### Post by guezuh2 on 2023-08-05
Ubuntu wont boot any more &#803;  [B]"Bluetooth: hci0: unexpected event for opcode 0x0000"
Is there something to do to fix it?
[/B]

---

### Post by TheFu on 2023-08-06
Yes.  Figure out what the problem is.  I seriously doubt any bluetooth issue is preventing booting.  You aren't using a BT keyboard, right? Nobody is that foolish - er ... I like to think. If you are using a BT keyboard, the solution is simple, connect a PS2 keyboard to the system and boot.  Does it work?

For most boot issues, if you need help, the best way to head is to boot from an ubuntu install ISO flash drive, choose "Try Ubuntu", then install boot-repair, run it, and choose the "Boot Info" generation.  That will upload non-sensitive data about your system and boot setup to a website.  Post the provided URL back in this thread and ask for help.  Of course, you can review the information yourself (and you should) to see if anything jumps out.

In general, don't ask the **boot-repair** tool to fix anything.  Sometimes it makes things much worse.  If you can't wait for help, while in the Try Ubuntu environment, backup all data and settings you don't want to lose to an external drive, then perform a fresh OS install.  You can put the settings and data back post-install, then install the main applications.  If you practice this a few times, you'll probably be able to perform the restore in 30-45 minutes.

---

### Post by guezuh2 on 2023-08-07
No I don't it is a laptop. I was hoping it was easily fixed so I'm going to reinstall it. Think you.

---

### Post by TheFu on 2023-08-07
> **guezuh2 said:**
> No I don't it is a laptop. I was hoping it was easily fixed so I'm going to reinstall it. Think you.

Well, it may have been easily fixed, but we'll never know and you'll end up reinstalling whenever there is a problem in the future if you don't spend the time to learn troubleshooting.  Nothing wrong with that.  Corporations around the world solve computer problems by reinstalling MS-Windows all the time.  It is their go-to solution, because they don't care about the user's data.  Corporate IT just wants to get the computer in and out ASAP. The ramifications of the wipe don't matter to them.

---

### Post by guezuh2 on 2023-08-07
Well after all I was trying to download the tool you mentioned from the repository but wasn't found. Is there another place I can find it?

---

### Post by guezuh2 on 2023-08-07
The problem happens when I was booting and I connected a HDMI cable connected to a TV... It has nothing to do with Bluetooth or is it?

---

### Post by TheFu on 2023-08-07
> **guezuh2 said:**
> The problem happens when I was booting and I connected a HDMI cable connected to a TV... It has nothing to do with Bluetooth or is it?

I don't know.  If I knew, I'd share.  We need more information, which is why I suggested for you to install boot-repair.  That tool can gather all sorts of boot information and post it to a URL that experts can review, when asked.  Without that information, you get guesses. Nobody is interested in guessing when it could be 1 or 10,000 things. That's why I suggested you provide more data.

If someone suggests installing a package and it isn't in the repos, I'd expect you to google for a how-to related to ubuntu and that package, then follow it.  I don't have the exact instructions or I would have posted them.  I know there's a PPA and any reputable how-to website for Ubuntu would provide the PPA and instructions for setting it up.

There are other tools which can be used as well, but historically, boot-repair has the newest, best, boot-info script built in.   If you search these forums, you'll find where lots and lots of people are asked to run boot-repair, get the info, and provide the URL.  Mostly the people asking will be forum moderators, so much more trustworthy than me.  I try to provide good suggestions, but only you can decide if I'm worthy of trust or not.  I've been here a long time, trying to help. Sometimes I fail, unfortunately.

BTW, I'm not privy to all the new booting stuff or even with 22.04, so someone else will need to look over any boot-info URL you provide.  I'm sure some of those people are lurking, waiting for the URL to be provided so they can help.

BTW, you never said which release, what hardware, which DE flavor, what GPU, or any of those based details.  The boot-info script will gather that data, but is it always a good idea to provide that for any question here.

Anyway, good luck if you decide that reloading a fresh install would be best.

---

### Post by ajgreeny on 2023-08-08
As TheFu said, Boot-Repair is the best way forward for you.
For all details of that see my signature below but ***run the Boot-info script only, not any repair.***

---

### Post by tea for one on 2023-08-08
> **guezuh2 said:**
> No I don't it is a laptop.
> The problem happens when I was booting and I connected a HDMI cable connected to a TV... It has nothing to do with Bluetooth or is it? 
Power off the laptop
Remove the HDMI connection to the TV
Remove all peripheral devices (i.e. usb drives, dongles etc.)
Does the laptop boot normally?

---

### Post by guezuh2 on 2023-08-08
No it doesn't. I shows the failure legend that's it. It is a laptop an old lenovo

---

### Post by guezuh2 on 2023-08-08
Got it thanks. I'll try somewhere else.

---

### Post by MAFoElffen on 2023-08-09
RE: [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Your boot message about bluetooth is just a warning, and does not prevent systems from booting...

But you seeing that message... tells me that you "are" seeing boot messages, so it "is" booting the kernel, at least to a certain stage.

If you want help, please help us to be able to help you. Please be descriptive in what it does do, or does not do. We are not there being able to look over your shoulder and "see" what you see, so please paint us a picture to visualize.

At the point it stops, what do you see on your screen? If you press keys <Cntrl><Alt><F4>, does it toggle to VTTY4 with a login prompt?

---

### Post by ActionParsnip on 2023-08-09
Also make sure you have the latest BIOS

---

### Post by dragonfly41 on 2023-08-09
From post #2

> 
[COLOR=#000000]You aren't using a BT keyboard, right? Nobody is that foolish - er ... I like to think. If you are using a BT keyboard, the solution is simple, connect a PS2 keyboard to the system and boot. Does it work?
I was that foolish when I started using my Logitech BT keyboard booting through rEFInd GUI. Realised that BT kicks in later so I retained the old keyboard for when I need to navigate the GUI. Most times it boots directly into default GUI Ubuntu but when I need Windows (requiring selection of Windows) I have to switch to the old keyboard - just for that infrequent occasion.


[/COLOR]

---

### Post by MAFoElffen on 2023-08-09
A few posts since #12, where I pointed the user to where he "can find" the Boot_Repair" script... But also pointed out that that report may not point out his problem... The kernel is booting. (He gets kernel boot messaging).

Remember way back in 2011, when I wrote the "Graphics Resolution" Sticky, with a framework for Linux Diagnostics, that pointed out a flow chart for diagnosing Linux Systems? You didn't need to be aroud back then. The sticky is still there because the information there is still relevant.

His system is not working somewhere between the point of the kernel booting, and getting to his Graphical Desktop. We need to identify where that point is, where it fails. That affects what is broken, and how to go about how to repair it. To me, most suspect is that it might be a graphics layer problem. 

We are not sure of where that point "is' where it stops, because the User is not real descriptive of where his system stops, and what he see's. What do we know for sure? There was an "unexpected event". 

Members, please concentrate on directing the user to describe and to clarify his current situation. You all know how to do that. I am patient...

---

