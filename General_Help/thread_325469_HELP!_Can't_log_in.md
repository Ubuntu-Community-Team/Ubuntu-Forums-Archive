---
title: "HELP! Can't log in"
date: 2006-12-25
forum: General Help
---

### Post by theaverageidiot on 2006-12-25
When I log in the screen goes black for a few seconds then takes me back to the login screen and I'm 100% sure my login details are correct! My comp was working fine all day and I turned it on just now and it does that. Restart won't fix it :(. I'm in dualboot windows now.

---

### Post by kidders on 2006-12-25
Sounds like you have a problem with your X server ... you should check its logs for anything new and strange.

---

### Post by theaverageidiot on 2006-12-25
I have NO idea what any of that meant/how to do it :/. Or what I would do if I found anything in the logs anyways, if I could find them. Help? o_O

---

### Post by kidders on 2006-12-25
Hey again,

You need to check out **/var/log/Xorg.0.log** for information about your problem. It's probable that you've changed something that is causing your graphical environment to fail to start. Your system logs might also tell you something useful ... **/var/log/messages**. You should be able to Google almost any error message with good success. :-)

Unfortunately, without something to go on, it's impossible to guess what your problem might be, I'm afraid. Have you any idea what might have caused it?

---

### Post by theaverageidiot on 2006-12-25
> **kidders said:**
> Hey again,

You need to check out **/var/log/Xorg.0.log** for information about your problem. It's probable that you've changed something that is causing your graphical environment to fail to start. Your system logs might also tell you something useful ... **/var/log/messages**. You should be able to Google almost any error message with good success. :-)

Unfortunately, without something to go on, it's impossible to guess what your problem might be, I'm afraid. Have you any idea what might have caused it?
I really don't know what I did :(. I was messing with Bluetooth/cell phone drivers all day but I don't see what that would do.

How do I get to those files if I can't boot into Ubuntu??!

---

### Post by kidders on 2006-12-25
Eep... you can't boot Ubuntu any more? That's not encouraging :-( What error messages do you get? (ie Are you having a problem with your bootloader, or with Ubuntu itself?)

Since whatever's going on seems to be getting worse, I wonder if there's a hardware-related explanation. :-k

---

### Post by mordox on 2006-12-25
use the ubuntu live cd from which you installed . the ubuntu 6.06LTS version has a live cd installer. or u can also use knoppix to boot and then mount the ubuntu partition and see the logs.

---

### Post by theaverageidiot on 2006-12-25
> **kidders said:**
> Eep... you can't boot Ubuntu any more? That's not encouraging :-( What error messages do you get? (ie Are you having a problem with your bootloader, or with Ubuntu itself?)

Since whatever's going on seems to be getting worse, I wonder if there's a hardware-related explanation. :-k
I can boot, I meant it still just goes to a black screen when I try to login. So I can't do anything.

---

### Post by kidders on 2006-12-25
You should be able to hit CTRL+ALT+F1 for a console. It works about the same as a terminal window in your graphical environment. Hopefully, your system messages log will have something useful in it, that will help identify your problem.

**Edit:** One thing you *could* try would be to temporarily remove your user profile, and see if that corrects the problem. If you're using KDE, for instance, you would do **mv ~/.kde ~/old_kde**. Of course, you won't want to leave your system like that, so we'll still need to identify the issue sooner or later.

---

### Post by riven0 on 2006-12-25
When you get to the terminal it doesn't hurt to do a **sudo dpkg-reconfigure xserver-xorg**. That's the first step I take if the problem is graphically related.

---

### Post by theaverageidiot on 2006-12-26
I did the Ctrl Alt F1 thing, then logged in, then CD'd in that terminal thing to /var/logs, but how do I view Xorg.0.log? "sudo gedit Xorg.0.log" doesn't work :(.

I did this: sudo dpkg-reconfigure xserver-xorg
And went through it all and all it did is fix my screen resolution :/.

---

### Post by kidders on 2006-12-26
> **theaverageidiot said:**
> I did the Ctrl Alt F1 thing, then logged in, then CD'd in that terminal thing to /var/logs, but how do I view Xorg.0.log? "sudo gedit Xorg.0.log" doesn't work :(.You can't use graphical apps in a text-only environment. You'll need to use a text-based editor (nano, pico, vi, etc.), or just tail/cat.

> **theaverageidiot said:**
> I did this: sudo dpkg-reconfigure xserver-xorg
And went through it all and all it did is fix my screen resolution :/.Doing that will usually only address server-wide issues, most of which would have stopped X from starting at all. Like riven0 said though, there's no harm in trying.

---

### Post by cmspaz on 2006-12-26
I'm actually having this problem myself as well.

It happened after I installed a secondary hard drive and added it to my /etc/fstab, then proceeded to attempt to log in as root from the main window, which of course doesn't work, then, when I tried to log back in, well, I couldn't.

But of course, removing said line from my fstab did no good.

I can get in through ssh, but not through vnc, it refuses the connection.

I clicked on the "Remote Login via XDMCP" in the F10 menu because I wondered what kind of settings were in there, since VNC wasn't working before this, either, when a week or so ago it was. Turns out it was most likely the fact that I had no idea what IP address this box got after I plugged the ethernet cable back in (This box doesn't have a dedicated monitor atm). I don't know if this'll make a difference or not, but I'm posting it just in case.

Hope any of this is of help.

EDIT

Oh, and none of the above worked for me, either >_<

/EDIT

EDITEDIT

And what types of "weird" things should we be looking for in Xorg.0.log, and anything with a [ww] next to it is an error, correct? Would missing font directories cause this?

/EDITEDIT

---

### Post by artinla on 2006-12-26
I would try these things:

From the terminal, type:
sudo adduser test

Fill in the information and try logging on with that user.  If your login screen is appearing, X is probably working.  I would suspect an ICEauthority type error is causing your problem.  Try renaming the file by typing:  sudo mv ~/.ICEauthority ~/.XICEauthority   If that doesn't work, type: sudo mv ~/.XICEauthority ~/.ICEauthority to put the file back the way it was.  You can try searching this forum for ICEauthority errors.

In case X is indeed causing you problems.. In your /etc/X11/ folder, you will probably have several xorg files that have a long number after them (date in yyyymmddxxxxx format)  You can copy one of the backup files in a manner such as the following:

ctrl-alt-f1 will give you a default terminal window

dir /etc/X11/  will give you a list of potential xorg backups

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.mybackup
sudo cp /etc/X11/xorg.conf.(whatever the backup is called) /etc/X11/xorg.conf

then hit ctrl-alt-f7 to return to your normal tty and then hit ctrl-alt-bksp to restart X.

If that doesn't help, you probably have issues beyond just an "X" misconfiguration.

Hope that helps.

Art

---

### Post by cmspaz on 2006-12-26
Heh, I think I've got this one, at least for me... There's a reason I got a new drive.

My primary drive is full. ](*,) EPIC FAIL

I'm in and it's working. Running startx from the terminal showed drivespace errors. I'll stick around and see if I can help any with the other guy. See what comes up running startx (other than an already running error. It should be above that).

---

### Post by theaverageidiot on 2006-12-26
> **cmspaz said:**
> Heh, I think I've got this one, at least for me... There's a reason I got a new drive.

My primary drive is full. ](*,) EPIC FAIL

I'm in and it's working. Running startx from the terminal showed drivespace errors. I'll stick around and see if I can help any with the other guy. See what comes up running startx (other than an already running error. It should be above that).
Come to think of it, I just downloaded a couple large files before shutting down. I had like 50MB left or something really tiny :/. I'm gonna give my XP less space and Ubuntu more space and see if it fixes it...

---

### Post by kidders on 2006-12-26
This might be a dumb thing to say, but don't forget to check how much free space you actually have before you go to all that trouble! If you're having storage-related problems, there would almost certainly be an error message in one of your logs anyhow.

If it does turn out that you're short on space, try deleting some stuff first. Imo you shouldn't resize partitions unless you really have to.

---

### Post by theaverageidiot on 2006-12-26
> **kidders said:**
> This might be a dumb thing to say, but don't forget to check how much free space you actually have before you go to all that trouble! If you're having storage-related problems, there would almost certainly be an error message in one of your logs anyhow.

If it does turn out that you're short on space, try deleting some stuff first. Imo you shouldn't resize partitions unless you really have to.
I did it before I saw this, but it's okay. It worked :). However, since I did that Xorg reconfigure thing, I used to have a TON of resolution options. Now I only have 3, all not right for my monitor (1024x768, 800x600, and 640x480). Also, it used to say 60 Hz but now it says 61 Hz. And when I scroll down a page now it jumps and glitches and stuff. o_O What do I do to fix it? Any way to restore my old setting or set them default like I did when I installed?

---

### Post by kidders on 2006-12-26
Hmm...

It's possible that the configuration thingy might have left behind a backup of your xorg.conf. If so, you can switch the configuration files around while X is still running without any problems. Then, log out of your graphical environment and hit CTRL+ALT+Backspace to reboot X.

If your screen goes black and *stays* black, you've picked the wrong xorg.conf backup.

---

### Post by theaverageidiot on 2006-12-26
> **kidders said:**
> Hmm...

It's possible that the configuration thingy might have left behind a backup of your xorg.conf. If so, you can switch the configuration files around while X is still running without any problems. Then, log out of your graphical environment and hit CTRL+ALT+Backspace to reboot X.

If your screen goes black and *stays* black, you've picked the wrong xorg.conf backup.
I officially deem this community the most helpful place. Ever.
Worked like a charm, thank you!! :)

This thread is **[SIZE="7"][FONT="Franklin Gothic Medium"]_[COLOR="Red"][SOLVED][/COLOR]_[/FONT][/SIZE]**

---

