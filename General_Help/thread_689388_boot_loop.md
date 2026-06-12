---
title: "boot loop"
date: 2008-02-06
forum: General Help
---

### Post by adiron on 2008-02-06
I run gutsy and recently I updated with a few new packages. During the process I had Amarok and firefox running and for some reason they turned into their negative colors. Then, after the packages downloaded my computer said I needed to reboot for them to take effect. I rebooted and my computer loaded until right before the screen where I enter my name and password. Then it reboots. It does this every time unless I press F12 for the boot setup. Then after I exit boot setup it will load the name and password screen, but when I type them in nothing shows up on the screen.

You might have guessed, I'm a newb, so be gentle.

---

### Post by az on 2008-02-06
[https://help.ubuntu.com/community/FaultyHardware](https://help.ubuntu.com/community/FaultyHardware)

---

### Post by saxamo on 2008-02-06
Bump...Why would  you suggest faulty hardware?

---

### Post by accatagon on 2008-02-06
From the randomness and arbitrariness of your errors, he has deduced that it might be a hardware issue. Regardless, it can't hurt to check. You can read the instructions on the page he linked you to to run a memory test. If it's constantly restarting every time you get to the login screen, you can try booting into single-user mode or booting off of a live CD. If you can boot just fine off of the live CD, then that indicates a problem with the software, which may or may not be caused by a problem with the hardware. Just out of curiosity, which packages were you installing? If it's consistently rebooting just before the login screen, that seems indicative of some kind of problem with XServer. Were you installing restricted drivers for your video card? If so, we might need to revert you back to the open-source drivers to get you back to basic GUI functionality. 

So, what would really help me right now is:
what were you installing?
If graphics drivers, what model graphics card do you have?
Does it work normally off a live CD?
Does it boot properly into single user (recovery) mode?
If you get into single mode, use "shutdown -hP now" (must be a capital P) to turn the computer back off.

Feel free to run the hardware tests too. They can't hurt. 
Anyway. . . I'm subscribed to this thread, so just holler back with the info I asked for, and we'll run from there.

---

### Post by adiron on 2008-02-09
forget exactly what was being downloaded. There was something about an "Important security update". I forget what else. I have a NVIDIA GeForce 6150 SE video card. It actually does not work when I use a live CD. I've been running a memory test for the past couple days and no errors have shown up. It does boot into recovery mode, but when I try to type it just makes a noise. However ctrl alt del does restart the computer. 

Hope this helps.

---

### Post by accatagon on 2008-02-10
Ok, so at this point we can be sure that it's a hardware problem, since the live-cd didn't work, but worked before (I am correct in that assumption, yes?), and live-cds aren't dependent at all on the software installed.

We can assume it's not a catastrophic BIOS failure because you get to GRUB and that's all well and good. Of course, at this point i have to ask the question of whether the bios managed to successfully load the CD or whether it crashed before it even got anywhere (did it get to a menu, or a message that looked as if the CD were successfully detected?)

We can rule out being solely a hard drive failure, since the live-cd should work regardless of the hard drive.

We can rule out the memory, probably, since the memtest came back negative (in the medical sense, it came out positive in the how good it is sense). We can also rule out memory because the errors are consistent (right?). 

We can rule out temperature being a factor in the errors currently since it behaves consistently and doesn't simply crash (turn itself off). Again, correct me if I'm wrong.

It sounds like we can rule out the keyboard. If you want to double check, try getting to the terminal in GRUB (instructions should be at the bottom, I think it's e or c or something). If you can type there normally, then the system is getting keyboard interrupts just fine.

That leaves the graphics card, PCI cards, CD drive, and motherboard as the most likely suspects. 

The problem is that your system is clearly [POSTing]("http://en.wikipedia.org/wiki/Power-on_self-test"), so it's not a catastrophic hardware failure. 

I'm sorry I can't be more helpful. Your problem is really very bizarre. At this point my main goal is to confirm 100% that it's a hardware problem, and not software, and then try to figure out what hardware failure(s) would cause the symptoms you have. The problem is that hardware problems don't often just start with installing updates. Let's see if we can figure this out.

Can you answer the following for me:

How exactly does the live-CD fail and what live-cd is it? Is it in the same manner as the hard disk version?
Does the keyboard work normally in the Grub command line ("reboot" should reboot your computer)?
Just to make sure: You do know that nothing is supposed to appear when you are typing the password, yes? Text should appear when you type the username though, so that doesn't seem like the issue. 
Is Ubuntu the only operating system on the computer? 

You might consider trying a real light live-cd like Damn Small Linux just to make absolutely sure it's a hardware issue.

---

