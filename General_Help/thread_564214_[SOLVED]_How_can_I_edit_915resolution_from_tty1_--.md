---
title: "[SOLVED] How can I edit 915resolution from tty1 -- HELP!!"
date: 2007-09-30
forum: General Help
---

### Post by drsmaw on 2007-09-30
Oh man, I did it again.
Ok, I edited 915resolution to accept 144x900 and then restarted x.  All i got was a little cursor at the top left, Obviously I went too fast and missed something while editing. Kubuntu started but never made it to the splash screen.
I can get into tty1 by ALT+f2.  But using 'sudo gedit /etc/default/915resolution' doesn't help, obviously no GUI.
How can I get to 915resolution to edit the mistake i entered in?
Using 'sudo resoluion -l' shows me all the modes, I just need to correct the default mode I set up and I think I'll be fine. 
PLease, Thanks!

---

### Post by ramjet_1953 on 2007-09-30
try this:

[COLOR="Red"]sudo 915resolution 30 1440 900 24[/COLOR]

Then [COLOR="Red"]gksu gedit /etc/default/915resolution[/COLOR]

Change the following:

MODE=auto to [COLOR="Red"]MODE=30[/COLOR]

XRESO= to [COLOR="Red"]XRESO=1440[/COLOR]

YRESO= to [COLOR="Red"]YRESO=900[/COLOR]

BIT= to [COLOR="Red"]BIT=24
[/COLOR]
Save and re-boot

Regards,
Roger :cool:

---

### Post by drsmaw on 2007-09-30
Thanks Roger,
Attempting it right after this post.  I think i entered 32 bit when i originally edited.  Gonna try it now. I'll be back.

---

### Post by drsmaw on 2007-09-30
ok, error.
won't let me gedit.  
"gksu:5639) GTK-Warning: cannot open display:"
what do you think?

---

### Post by bodhi.zazen on 2007-09-30
You can always use nano :

In a terminal:```
sudo nano -B /etc/default/915resolution
```

Crtl-X to exit nano, Y to save changes.

The -B flag saves a  backup of the original file (just in case ...)

---

### Post by ramjet_1953 on 2007-10-01
Sorry drsmaw!

Brain fade, I'm afraid.

You can't use gedit in recovery mode.

bodhi.zazen's suggestion is the way to go, when editing the file in terminal mode.

By the way, I belive that there is no advantage in using 32 bit with Linux, as it only includes an alpha channel and doesn't increase resolution.

It is really a Windows thing.

Regards,
Roger :cool:

---

### Post by drsmaw on 2007-10-01
Ok, got it.  Nano did it.
thanks for the help.
Got my 1440x900, but it's stretched I'll have to fool around with it.  looks like my refresh rate is stuck at 75 - I think i need it at 60.
Marking another SOLVED

---

