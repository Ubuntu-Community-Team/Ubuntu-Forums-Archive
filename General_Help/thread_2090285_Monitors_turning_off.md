---
title: "Monitors turning off"
date: 2012-12-01
forum: General Help
---

### Post by kerryhall on 2012-12-01
I have an issue where my monitors turn off after approx 10-15 minutes, despite the "Turn screen off when inactive for:" set to "Never".

Sounds like a bug to me. Running gnome-panel rather than Unity. 

Any ideas? Thanks!

---

### Post by ohnonot on 2012-12-03
one thing about the last ubuntu flavor i used is that it runs a screensaver AND a power manager. so to be sure, you have to adjust settings in both.
personally i disabled both and use only xset anymore which runs a basic X-built-in screensaver.

---

### Post by kerryhall on 2012-12-03
Thanks for the help! How did you disable both?

---

### Post by emptybox on 2012-12-04
I have a similar issue running 12.10 Unity.

My monitor switches off after approx 15 mins even though I've been into 'Power' and set it never suspend, and I've been into 'Brightness and lock' and set it to never.
Is there another setting?

I can't see any settings for screensaver? Does Unity even *have* a screensaver?

I should add, it just requires a tap on the keyboard to bring it back. It doesn't ask for the password.

---

### Post by emptybox on 2012-12-04
There's something about this in the 12.10 bug thread, so might not apply to the OP's problem, but try putting "xset s off" into the terminal (minus the inverted commas).
That seemingly turns the xscreen saver off.

If that cures the problem for that session, then the advice is to add that line to etc/X11/xinit/xinitrc to make it permanent.

The first step seems to cure **my** problem anyway.

ETA: Editing xinitrc didn't seem to work for me, but adding the command to 'Startup Applications' *seems* to have done the trick.

---

### Post by ohnonot on 2012-12-04
> **kerryhall said:**
> Thanks for the help! How did you disable both?
i don't really know.
i'm using openbox which has a very simple autostart script.
i have been using plain ubuntu without unity for a while, i remember there's an autostart folder somewhere under the home folder and, iirc, another autostart folder somewhwere in the "root area"...
both contain .desktop files which can either be disabled (by editing a line in them, please don't ask me which) or just deleted.
but it's been a while, i could be wrong.

anyhow, just disabling both means you have no screen saver or turn off backlight at all.
not a desirable situation, i would say.

so, either careful tweaking of both (and others have better information on that than me) or replacing with xset.
for the latter, i can help.

---

### Post by kerryhall on 2012-12-06
I have heard that adding a line to rc.local is supposed to run something on boot, but of course I found out later that it does this in no particular order. (ie, it could try and execute xset s off before x even starts.)

So it sounds like I need to write an upstart configuration for this bash one liner, lol. 

I will certainly try "xset s off" and see if that fixes things for my session. I will report back.

Thanks!

---

### Post by ohnonot on 2012-12-10
> **kerryhall said:**
> I have heard that adding a line to rc.local is supposed to run something on boot, but of course I found out later that it does this in no particular order. (ie, it could try and execute xset s off before x even starts.)

So it sounds like I need to write an upstart configuration for this bash one liner, lol. 

I will certainly try "xset s off" and see if that fixes things for my session. I will report back.

Thanks!well, upstart is definitely far out for me.
why not add it to autostart?
anyway, where did you get in the last 4 days?

---

### Post by kerryhall on 2012-12-24
"xset s off" seems to have done the trick. Let me try throwing that into .xinitrc and see if it sticks that way

---

### Post by kerryhall on 2012-12-24
Spoke too soon. "xset s off" seems to have had no effect :( Let me keep digging here.

---

