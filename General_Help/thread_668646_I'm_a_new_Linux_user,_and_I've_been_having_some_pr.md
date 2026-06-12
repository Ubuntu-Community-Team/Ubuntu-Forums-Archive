---
title: "I'm a new Linux user, and I've been having some problems."
date: 2008-01-15
forum: General Help
---

### Post by Stario on 2008-01-15
Hi Ubuntu forums =D
Ubuntu so far has been great. Everything is free and open source, and it's not windows. I've been having a few problems, recently though..

First, If I want to download something. I'll usually get > E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

So, I open terminal.
I paste dpkg --configure -a and I hit enter.

I get > requested operation requires superuser privilege


So, I don't know. Anyway. I normally have desktop effects. Now, I don't for some reason. I went to go back to enable them (they were set to off) to custom, and it would simply say 'Desktop effects could not be enabled'

I've used Envy for my graphics card (was told to from my friend), it installed the Nvidia drivers. I made sure they are in use and enabled in the 'Restricted Drivers Manager'. They are enabled, and working. I have a Geforce 8500 GT.

If you need any more information let me know. But know that I'm COMPLETELY new with Linux, so I won't know how to do much!

---

### Post by PinkFloyd102489 on 2008-01-15
type "sudo" before the command and enter your password when it prompts.

---

### Post by navd on 2008-01-15
ok you want to try to log into root first.

type 

su -

and insert your root password. Then try the dpkg.....

---

### Post by luisromangz on 2008-01-15
When superuser privileges are required in a terminal, you have to prefix the command with sudo, for example:

sudo dpkg --configure -a

---

### Post by Stario on 2008-01-15
Thanks mates, that worked, I can install some things.
What about my desktop effects issue? Thanks.

---

### Post by navd on 2008-01-15
all I could say about your desktop effects is that it could be a driver issue. Lucky you though. At least you get desktop effects. All we have in debian is a transparent terminal :lolflag:

---

### Post by Stario on 2008-01-15
:P Well I have desktop effects I just can't use them? xD

---

### Post by navd on 2008-01-15
Well the only thing I could possibly see as the problem is the card or driver. Search The Web to see any 8500 gt Ubuntu Issues lying around.

If not. Try reinstalling in the driver the old fashioned way( though that might not help at all ) just a thought.

---

### Post by Stario on 2008-01-15
How would I reinstall the driver the old-fashioned way?

---

### Post by voteforpedro36 on 2008-01-15
To use Custom, I think you have to have the Compiz Settings Manager installed. It's ccsm, I believe. 

So:

sudo apt-get install ccsm

Then you should be able to use Custom.

---

### Post by Stario on 2008-01-15
I have Compiz

---

### Post by voteforpedro36 on 2008-01-15
Yes, but the Settings Manager doesn't come installed with Ubuntu.

---

### Post by Stario on 2008-01-15
Should I reinstall Compiz?

---

### Post by voteforpedro36 on 2008-01-15
No, but in the terminal, type:

sudo apt-get install ccsm

Then you should be able to use Custom.

But I do think that you can already use the other options (Normal and Extra?). Maybe I'm the confused one.

---

### Post by Stario on 2008-01-15
I can't even have it on normal while Compiz is completley removed.

---

### Post by navd on 2008-01-15
Well try out pedro's way first......

[http://www.pendrivelinux.com/2007/02/22/installing-nvidia-drivers-in-ubuntu-edgy/](http://www.pendrivelinux.com/2007/02/22/installing-nvidia-drivers-in-ubuntu-edgy/)

I found that neat little site. It works in edgy so it should be similar if not the same in feisty.

Sorry if it doesnt fix the problem. Just a suggestion. Maybe all you have is an unsupported videocard.

---

### Post by Stario on 2008-01-15
Thanks mate, doing that now.

---

### Post by navd on 2008-01-15
yup anytime.. Give an update if anything happens.

---

### Post by Stario on 2008-01-15
Well, now I'm very confused. My res is set to 800x600, and I tried doing everything to get the thing back working for my graphics card.
I'm just going to reformat, I didn't have much. How would be the best way to do this, I have the CD with Ubuntu on it.

---

### Post by r-mo on 2008-01-15
Before you go the whole hog and reinstall just try running this command in the terminal

```
sudo dpkg-reconfigure xserver-xorg -phigh
```

It will reconfigure your graphics settings

---

### Post by Stario on 2008-01-15
Nope, no worky.
How can I reinstall it completely?

---

### Post by r-mo on 2008-01-15
Backup everything you need! 

Boot from the install cd and do a normal install but in the partitioning bit choose manual.  Then tick the box that says format next to the partition ubuntu is on atm, click the edit partition button and set the mount point to /

that's about it i think.

---

### Post by Stario on 2008-01-15
It won't let me check/tick that. Should I just right click>delete partition?
Edit: Played around with it, got it now. Didn't work at first, but then I set the mount point to / and now it's reformatting fine.
Thanks a ton, mate!
I should be good for now.

---

