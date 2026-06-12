---
title: "Mouse moves but clicks don't work occasionally"
date: 2013-05-10
forum: General Help
---

### Post by Shadowblink on 2013-05-10
Hi, let me start of by saying I'm new to Ubuntu and I don't know how to work well with it (yet).
Today I installed xubuntu because I was interested in ubuntu after using it on a live cd, however I liked the xfce interface more than the unity so I decided to go with xubuntu.
After using it for a while I noticed I was having problems with the mouse ( I have a Cyborg R.A.T. 7 ).
Sometimes it just 'freezes' I can move it around and interact with the current window but I can't click on anything else, I know it sounds weird so I'll try to explain it by using an example.
So if I open Firefox I can click on the adress bar, tabs, etc... but I cant click on anyting in the menu bar or on minimize, maximize or close. 
I neither can click on anything on the UI on top or use the docking station on the bottom.
I noticed that if I right click on the tabs or something which opens a menu if you right click it I can interact with everything again untill it bugs again. 
Now I know you might say 'Well problem solved' but if I close something I cant right-click anywhere so I can't interact with something else.

Edit: Some shortcuts do not works: Alt + Tab for one does not work, will edit if I find more.

Help would be apreciated ;)

Thanks in advance!

---

### Post by cortman on 2013-05-10
So it's not just your mouse but keyboard as well? Does this happen in any other program besides firefox?
Have you tried a different mouse/different USB port?

---

### Post by Shadowblink on 2013-05-10
Well I don't *think* that it's my keyboard as well because other shortcuts do work like bringing up the terminal or switching to another workspace, I think it's a problem with interacting with other windows, yeah it happens in every program/window.
No I haven't tried a different port, I have unplugged and replugged but that didn't work, I will try a different port now ;)

Edit: Pushing a button on my mouse to switch between profiles seems to fix it temporarily as well
Edit 2: Different port didn't work

---

### Post by Shadowblink on 2013-05-12
Am I allowed to bump this ?

---

### Post by theBishop on 2013-05-12
I'm having this exact same problem on regular Ubuntu 13.04.  It's hard to search for online because I just get results like "mouse doesn't work" or "touchpad not detected".  But the problem is subtle as the OP described.

My laptop has an synaptics touchpad which works correctly.  But when I plug in an external mouse, both the mouse and the pad have the problem described.  Clicks are recognized within the focused app, but I can't focus any other app.  I can't do any window-management tasks (maximize, minimize, move, etc).  

When I unplug the mouse, the touchpad goes back to working properly.

And I didn't notice before reading this thread, but alt-tab doesn't work either.  Unity seems to work, I can bring up the dash with <Super>, and <Super>+S works to bring up the workspace picker.

<Alt>+<Tab> and <Super>+W do not work with the mouse plugged in.

Sounds like a Compiz bug, right?  I'm not sure.

---

### Post by Shadowblink on 2013-05-12
It's exactly as you say, I've searched online but with no result.

However I think you can describe it more accurate because I'm really unexperienced with Ubuntu :)

---

### Post by theBishop on 2013-05-12
> **Shadowblink said:**
> It's exactly as you say, I've searched online but with no result.

However I think you can describe it more accurate because I'm really unexperienced with Ubuntu :)

Crappy Workaround:  I was able to get my mouse working by disabling the touchpad in system settings.  At least I can carry on with my work now (photo editing with a touchpad: miserable), but I know touchpad+mouse has worked in the past on Ubuntu.  Not sure what changed.

---

### Post by theBishop on 2013-05-12
OK, even weirder.  After enabling the touchpad with the mouse connected, everything works as it should with both inputs.

How about that!

EDIT: spoke a little too soon.  So the disable-touchpad thing isn't really a workaround.  Although I could get move/maximize on the usb mouse with the touchpad disabled, it was inconsistent.  Sometimes I could get the mouse to work.  But even when the mouse seemed to be working: the window I clicked didn't actually get focus.  

I could move windows using the mouse, and the window I clicked became the top-most window on screen.  But, that window can't receive keyboard input, and the window's title stays dim, suggesting it doesn't have focus.

---

### Post by Shadowblink on 2013-05-13
You're saying it might be a problem with touchpad + mouse but I'm a desktop user so that can't really be the core of the problem.

Also I'm not sure if this is just a problem with drivers or such but I'm having trouble to get sound working correctly, if I have sound in Skype I don' have sound in my browser or vice versa. It might be linked to the problem of interacting with different windows, not sure though because clementine seems to work all the time.

---

### Post by Shadowblink on 2013-05-15
Bump... Please help :s

---

### Post by timberjam on 2013-05-29
You're not the only one with this problem.  This has been happening to me more and more recently.  When I first turn on the computer (it's a desktop without a trackpad) and log in, all seems to be okay.  I open up an application, like Chrome or Terminator, and the mouse can't interact with the window that opens up.  For instance, Chrome opens up with all the quick launch app icons on the main screen, but I can't click any of them.  In Terminator I can't right click in the window to open the options menu.  I have to reboot the computer a couple times and then it eventually starts working.  I've also tried just logging out rather than fully rebooting, but I can't remember right now if that worked.  I'm not willing to reboot my computer right now to test it.

Other symptoms:
  1) I can interact with the Unity buttons.  For instance I can launch apps from the Launcher, and I can click on the little icons in the top bar (eg - to close or maximize an app, or to logout/reboot the computer)
  2) I can't use alt-tab to switch between windows
  3) Basic keyboard typing seems to work

Ubuntu: 13.04
OS Type:  64-bit
Processor:  AMD FX(tm)-4300 Quad-Core Processor × 4
Memory:  16GB
Graphics:  GeForce 8800 GT/PCI/SSE2

I'll add more if I think of anything else.

---

### Post by timberjam on 2013-05-31
Just a quick update that logging out and back in fixed it.

---

### Post by timberjam on 2013-05-31
<Grumble>  After logging back in, it worked for about 10 minutes.  Then the mouse/keyboard suddenly froze again.  I could interact with the window I was on, but couldn't switch to any others.  Luckily, Ctrl-Alt-Del still brings up the Logout option.  Logged out and back in and it is currently working again.

---

### Post by jacklk on 2013-05-31
I have had this problem before, but sometimes booting would make the touchpad and keyboard not work at all and I had to restart to be able to use my touchpad and keyboard. I also heard this is a very common problem with ASUS laptops. I did have a work around for it though, it may work or it may not.
In /etc/default/grub, try replacing the "GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"" line to...
> GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i8042.reset i8042.nomux nolapic"
... then run...
> sudo update-grub
... and afterwards reboot. This is only a suggestion from my previous expirences, please try this if you are experiencing this problem. I would be interested to know if it works.

---

### Post by Sqwirrelz on 2013-06-06
Finally! This is the first thread I have found in months of someone else having this problem. I have the exact same issues as OP. I'm running Xubuntu 12.04. I am using an old generic laptop with external mouse and external keyboard. (I have this setup as a desktop pretty much). Without the two devices connected, everything runs fine. 

When I only connect my mouse (also a Cyborg Rat 7, good taste OP) everything goes wrong. I have also tried other generic mice, and have the same results, so I don't think it's the device itself. When I connect the external keyboard, it doesn't cause any problem at all. 

I didn't encounter any problems earlier today with the mouse attached for a few hours, which was strange, but eventually the trouble came back. I did try your solution, Jacklk, with no success. I've also tried disabling my touchpad and using the mouse with no luck. Really hoping to find a solution to this, as it's infuriating beyond anything I can describe. 

edit: I've also been having the same problem on a desktop with Xub 12.04. Bloody mouse being hateful.

---

### Post by fouad al omare on 2013-06-06
> **jacklk said:**
> I have had this problem before, but sometimes booting would make the touchpad and keyboard not work at all and I had to restart to be able to use my touchpad and keyboard. I also heard this is a very common problem with ASUS laptops. I did have a work around for it though, it may work or it may not.
In /etc/default/grub, try replacing the "GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"" line to...

... then run...

... and afterwards reboot. This is only a suggestion from my previous expirences, please try this if you are experiencing this problem. I would be interested to know if it works.

this seems to have solved the issue, thank you very much, i had also the same problems, first installed mint, died twice ruining everything i have, now trying ubuntu.

---

