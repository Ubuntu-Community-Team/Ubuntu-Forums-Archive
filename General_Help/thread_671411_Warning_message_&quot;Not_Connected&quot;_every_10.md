---
title: "Warning message &quot;Not Connected?&quot; every 10 secs..."
date: 2008-01-18
forum: General Help
---

### Post by douglas_slac on 2008-01-18
Sorry - I'm sure this has come up before, but after trying many different searches I just can't find a thread on this already.

But I've updated to 7.10 (if I remember right), and I'm on a laptop here, and it is sometimes connected to a printer, and sometimes not.

I got the printer setup this morning, and working ok (gutneprint 5.1.3 needed, that another story), but now, I'm not connected to the printer, and every 10 secs I get this message in the corner of the desktop that says:

"Not connected?"
"Printer 'yadda-yadda' may not be connected."

I click on it, and 10 secs later, it pops up again.  I'm starting to go a bit crazy.

How do I turn this off, so it just doesn't happen?

---

### Post by danwood76 on 2008-01-18
what printer is it?
How is it connected to your PC?

regards,
Danny

---

### Post by douglas_slac on 2008-01-18
it is a usb printer, the dev. path is /dev/usblp0.

How does this matter to message control?  I kinda mostly want to understand how these pop-up yellow message boxes are controlled.

---

### Post by danwood76 on 2008-01-18
Well it sounds like its popping up because the printer isnt connected or isnt installed properly.
Does your printer work?

regards,
Danny

---

### Post by douglas_slac on 2008-01-18
The printer and printing is fine, this isn't a printer connection problem.  The computer is a laptop, and most of the time the printer won't be connected.

This is a pop-up message box control problem.  I want the pop-up box message to go away, it is continuing to drive me crazy.  How do I control the pop-up box messages?

---

### Post by danwood76 on 2008-01-18
it depends whats popping them up.
you could try right clicking the icon in the notification area and trying to disable the popups.

regards,
Danny

---

### Post by douglas_slac on 2008-01-18
Thats whats driving me crazy, I have no idea what is making this message pop up.  There isn't any icon, it is just there.  If I click on it at all, it just goes away.

These pop-up system messages didn't seem to be there in the previous Ubuntu, at least they weren't driving me crazy like this, such that I don't remember them.

But all morning (and now afternoon here), pop-up "Not connected?", click go away, pop-up "Not connected?", click go away, pop-up "Not connected?", what is causing these, right click, it goes away, arghh... search, search, pop-up "Not connected?", click go away, arghh... how do I control my machine..., pop-up "Not connected?"  AHhhh - forget it, if I can't find out soon, I'll have to trash Ubuntu... I'm loosing control of my machine - go get tea and repeat until hair is lost.

---

### Post by danwood76 on 2008-01-18
Well I havent gotmy printer plugged in now and Im not getting any messages likeyou are getting.

How have you got the printer setup, just through CUPS?
What drivers are you using and what printer do you have?

It might be that you can hide hesemesage through the CUPS setup.

regards,
Danny

---

### Post by danielhs on 2008-03-26
I'm seeing the exact same thing with a networked printer (using local CUPS server).

Message keeps popping up.  What's more, this is on my workstation, not a laptop, so it really shouldn't be going on and off the network.

---

### Post by danielhs on 2008-03-26
I'm seeing the exact same thing with a networked printer (using local CUPS server).

Message keeps popping up.  What's more, this is on my workstation, not a laptop, so it really shouldn't be going on and off the network.

I think it's worth filing a bug on this.

---

### Post by danielhs on 2008-03-26
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/207194](https://bugs.launchpad.net/ubuntu/+bug/207194) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Added a bug report for this in launchpad:
[https://bugs.launchpad.net/ubuntu/+bug/207194](https://bugs.launchpad.net/ubuntu/+bug/207194)

---

### Post by Daxman on 2008-05-03
Hey fellas, I found a solution to this problem, I was getting quite annoyed with it as well.
Check to see if you have any documents in que waiting to be printed. If you do and the printer is not attached, this warning message keeps popping up until the print job is completed or canceled. 
Go into System > Administration > Printing and see if your printer has anything waiting to be printed. If it does, Right click the priter icon and select Jobs.  Then, cancel it.
Hope this helps.

Dax

---

