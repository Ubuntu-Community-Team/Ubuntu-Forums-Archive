---
title: "Loading Unbuntu problem"
date: 2008-01-27
forum: General Help
---

### Post by wayneharrison on 2008-01-27
Version 7.1 downloaded from the Ubuntu web site.

I loaded this server and it just hangs up after:

running local boot scripts (/etc/rc.local)

I'm extremely new to Linux and it can be assumed that I'm probably below "novice level"

Is there a fix for this?  I'm considering just scrapping the whole project (which was just for my own education)

Also, just for added information.  The non-server version works just fine and I can go right into the gui screen.

---

### Post by lizadove on 2008-01-27
FIrst of all, don't give up!  There is a TON of information on this site, and many people who are very helpful.  Ubuntu is so cool!  I'm new to it, and juuuuuust barely getting my system running smoothly the way I want it to, but already I can see I'm going to really like it. 

For example, I've got a tri-boot system with XP on it too, and I COULD NOT get my printer to install correctly on XP- even with the factory installation disc!  With ubuntu I plugged it in, and a little note came up saying "Your HP 1400 series is ready to print" .  wow.  And it really did print - it wasn't lying.

If you're willing to invest a little time (and probably frustration, if you're like me) up front with ubuntu, you'll be rewarded in the end.  Ubuntu's not for everyone, but if you're not terrified of command-prompt, then you'll probably be okay.  Keep searching for your answer - on google too.  I don't know how to help you, but someone will.

Good luck!

---

### Post by GavinZac on 2008-01-27
can you post system specs and hardware info?

---

### Post by wayneharrison on 2008-01-27
466 Mhz processor
750 Mb ram
motherboard video 

It's just an extra PC I had laying around the house that I wanted to play with.

---

### Post by GavinZac on 2008-01-27
this is probably going to seem complicated but i hope to point you in the right direction at least to get more info to make finding the answer easier.

can you try booting without the "quiet splash" in the boot command, and with "break=top" in there instead? you can do this by pressing a button in the GRUB menu (i cant remember which button, but it tells you) and its simple a case of backspace'ing away the quiet splash bit and typing break=top, then hitting enter.

---

### Post by Casual Fan on 2008-01-27
The above poster's solution may work (with or without the break=top) if it's not really hanging--do you just get a black screen that sits there for a while?

---

### Post by wayneharrison on 2008-01-27
Mine just said "quiet".
I made the change and booted with the same results as before.

---

### Post by wayneharrison on 2008-01-27
I just get a flashing cursor in the bottom right of the screen after the script listed above says "ok"

If I press enter, it continues on, but I get a login line.

---

### Post by Casual Fan on 2008-01-27
Try pressing ctrl+alt+f7 when you get the login line...or login and type in sudo gdm.

---

### Post by GavinZac on 2008-01-28
> **wayneharrison said:**
> I just get a flashing cursor in the bottom right of the screen after the script listed above says "ok"

If I press enter, it continues on, but I get a login line.

The log in is Ubuntu Server. Server doesn't come with a desktop environment by default.

---

### Post by wayneharrison on 2008-01-28
Ok.  How do I go about getting the gui interface?  I don't want to work with it the way it is.

---

### Post by silviur on 2008-01-28
sudo apt-get install ubuntu-desktop

---

### Post by wayneharrison on 2008-01-28
That's it?  I've been wracking my brain over this and it can be solved by just a few words typed on the command line that I thought shouldn't be there?!?!?!?

I'm at work now, so I'll have to try it when I get home.  I hope this works!  

Thanks everyone for your help.

---

