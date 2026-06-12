---
title: "Failsafe Gnome Login hangs, ctrl-alt-F1 fails"
date: 2007-08-27
forum: General Help
---

### Post by allwin on 2007-08-27
I put some updates on this afternoon, and when I rebooted, the Gnome desktop froze.  CTRL-ALT-F1 did not work, neither did CTRL-alt-backspace.  I tried logging in with the failsafe gnome session, and that session hung as well.

The desktop comes up, the panels show up, the CPU % graph in the panel starts up, and then it all freezes.

How do you go about fixing something like this?

I do have Compiz Fusion and Feisty and an ATI card, if that helps, but since the Failsafe is not supposed to load Compiz, what could it be?  

It was working PERFECTLY before the updates (to such things as jasper and compiz/fusion for example).

Where do I go from here as I have a useless system now!:confused:

The only way out is for me to push the power switch!

---

### Post by prince_niceguy on 2007-08-28
login into fail safe terminal and find out what is there in 

xsession-error file in your home directory.

That will give you some pointer on what could be the problem.

---

### Post by allwin on 2007-08-28
I eventually fixed this.  I was in a world of hurt, though.  The FAILSAFE terminal showed up for some reason in the lower right corner of the screen and was UNREADABLE with no scroll bars or any way of placing it where it was useful.

The failsafe GNOME session froze, and I couldn't use ctrl-alt-F1 to get a terminal.

Fortunately, I was able to ctrl-alt-F1 at the LOGIN screen!  That got me to a terminal, and I was able to log on in text mode and do a "startx" command.  Now I DON'T KNOW WHY...but at first it wouldn't start complaining about not being able to get a lock on some file in /TMP/.  So I "sudo rm" the file mentioned to get rid of it, then STARTX.

X came up looking kind of funny but eventually got me into a desktop.  I went into SESSIONS and took out GDESKLETS and COMPIZ FUSION (which I suspected of being the problem).

Then when I logged on again after rebooting, I got GNOME back just without any eyecandy.  I found some other threads that suggested going into Compiz Fusion Config Manager and doing a big RESET back to all defaults on all effects.

That allowed me to start COMPIZ from a terminal OK.

Then I put COMPIZ and EMERALD startup commands back into sessions and now it all seems to work.

Sad part is NOTHING IS WRITTEN anywhere about how to recover a HUNG DESKTOP if you can't get a TTY going.

I guess a followup question would be what you could do in a situation like that if you had NO IDEA what was causing the freeze!

---

### Post by prince_niceguy on 2007-08-28
Glad that it worked for you...

When there is gnly hang like this... I suspect something wrong with my .gnome or .gnome2 dir so I delete them ...

down side is I lose all my customization features but better than a hung system... ;-)

---

