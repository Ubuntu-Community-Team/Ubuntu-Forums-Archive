---
title: "Can't Reboot Without Live CD"
date: 2007-12-30
forum: General Help
---

### Post by drjasonmd on 2007-12-30
Hello Everyone,

I'm brand new to Linux, brand new to Ubuntu and only recently acquainted with using a command prompt (hadn't seen one of those since the early 90s).  

I've had Ubuntu running smoothly since yesterday.  I managed to get the drivers installed for my ATI Radeon Mobility graphics card today (from ATI), so I've been enjoying the nice 3D desktop effects.  However, now when I try to boot, it takes a very long time, the screen is blank, and ultimately it ends up at a command prompt with the screen resolution whacked up so high I can only see the upper left hand corner of the screen, just enough to see that it's asking for my login.  I put in my login, and then my password, but then nothing happens.  It never logs in to a GUI.  There appears to be a message telling me when my last login was, but the command prompt is off the bottom of the screen.

I've tried booting in recovery mode, but it does the same thing.  

So, now that I had everything running so smoothly, and a whole lot of software installed, I'd hate to just reinstall everything again.  The only thing I had left to do was to put in my email settings and then I'd be ready to work in Linux on Monday.  Is there a way to back out of the most recent changes from the Live CD or the command prompt prior to booting?  I'm sure it's either the ATI drivers or the Tux G2 login package that I installed.  Is there a way to set the screen resolution before it boots? 

Any help is appreciated.

---

### Post by LaRoza on 2007-12-30
Try recover mode:

```

dpkg-reconfigure -phigh xserver-xorg

```

This will reconfigure xserver (your display)

(might have to use sudo)

---

### Post by drjasonmd on 2007-12-30
do I do that from the command prompt when I start the machine? Is there a way to do this from here (I'm booted from the Live CD right now).  

What's sudo?

Thanks

---

### Post by LaRoza on 2007-12-30
> **drjasonmd said:**
> do I do that from the command prompt when I start the machine? Is there a way to do this from here (I'm booted from the Live CD right now).  

What's sudo?

Thanks

Reboot the computer (remove the CD) and enter Recovery Mode.

Run that command.

If it doesn't let you, put "sudo" before it.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by unix4linux on 2007-12-30
Ok, why don't you try going to a virtual terminal instead of the GUI and revert to a working xorg.conf file?  Whenever you make a change to the xorg file through the gui or gui setup, it saves a copy of the previous xorg.conf file in /etc/X11.  Look for the previous one and copy it over to the original file.

Another thing is you can open the xorg.conf file that you currently have and put in the vesa driver to load your video card.  Either one of these steps should suffice so that you are able to get back into gui and figure out your settings.

From you being brand new to linux and Ubuntu, I am assuming you don't know how to go to VT or make the adjustments I just explained.  If so, here it is...if you do know, no offense ;-)

to go to a VT do:
ctrl+alt+F1 or F2 or 3, etc. F6 being the last VT because F7 is reserved for GUI.

Once there, login.  After you are logged in go to "cd /etc/X11"
then
"sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak" (this is to backup your current xorg file)
then
"sudo cp /etc/X11/xorg.conf/previous_backup_system_made_not_the_one_u_just_made /etc/X11/xorg.conf"
then
"startx" to start your gui up again.  If it works, good...if not then try another backup the system may have created.  If all backups fail, then go into the xorg.conf file directly and change the field that has "driver"  "your_current_driver" to "vesa" (vesa is a generic driver"

You can edit the file with "vi /etc/X11/xorg.conf" which is what I use or you can use nano which is more user friendly "nano /etc/X11/xorg.conf"

Save the file, exit and "startx" again

If all still fails...you might have more issues...at that point, I suggest pasting your /etc/X11/xorg.conf file here and also the output of "lspci" so we know what kind of video card you have.

Hope this helps a bit

---

### Post by drjasonmd on 2007-12-30
Thank you both so much for your help.  I'm back in the GUI now, and I've got it all running like it was 6 hours ago.  I've now managed to get all my IMAP accounts set up and running, so I think I'm good to go.  It's going to feel real nice to finally be free of that Word/Outlook/Messenger nightmare for work on Monday.  

I learned a lot going through all of your suggestions above.  This really is a great community.  I'd still be on hold to a call center on my old OS.  

How refreshing this all is!

---

### Post by unix4linux on 2007-12-30
Glad we could help.  This is indeed a nice community.  There are some people that are ignorant but hopefully you won't let those people steer you away....best of luck with your new system and welcome to the community.

By the way, if you find yourself needing to use MS products like office, try Cross Over.  I use it for work email (outlook) simply because I need to have the calendar working correctly and evolution-exchange plugin sometimes craps out on me.

Cross Over is not free though...but it is nice

See you around

---

