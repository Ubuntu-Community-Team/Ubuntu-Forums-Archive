---
title: "Screen blanking on lid close doesn't work"
date: 2007-09-03
forum: General Help
---

### Post by nkessler2000 on 2007-09-03
Hello. I'm having an issue with screen blanking. When I close the lid on my laptop or wait for the screen to blank, the screen dims but does not turn off. I've check the power management settings and it is indeed set to blank the screen when the lid is shut. 

I've read a few other threads regarding the subject but none of them seem to address my specific issue. One thread suggested using 
```
xset -display :0 dpms force off
```
to blank the screen, which works, but I can't figure out how to initiate that command when the lid closes. I've tried looking at the /etc/acpi/lid.sh file, but I can't decipher it. It seems to call another program called /usr/share/acpi-support/screenblank, and I've edited this file to include the above xset command, but that didn't do the trick. Additionally, if I run lid.sh manually, nothing happens, even if the lid is closed.

Anyone with more experience able to give me some guidance? 

Just so you know, I've got a Dell laptop with an ATI Radeon X1400 video card, and I'm using xgl and the restricted driver.

EDIT:
Also, if I manually run /etc/acpi/screenblank.sh the screen does go blank. So it seems it's just the lid closing that's not initiating it. Like I said though, the screen does go dim, so it's doing something.

---

### Post by nkessler2000 on 2007-09-03
Okay, a little more info. I've tried using acpi_listen to see if the system is seeing the lid close. Here's the output:
```

button/lid LID 00000080 00000015
button/lid LID 00000080 00000016

```

I checked out the /etc/acpi/events/lidbtn file. Here's what it looked like:
```

# /etc/acpi/events/lidbtn
# Called when the user closes or opens the lid

event=button[ /]lid
action=/etc/acpi/lid.sh
```

Because lid.sh, when executed manually, doesn't do anything, I tried changing it to screenblank.sh, which does blank the screen. However, none of this made any difference. The same dimming occurs when I close the lid. I'm stumped.

---

### Post by nkessler2000 on 2007-09-04
Okay, I got it to work. The fix I implemented last time did the trick. The reason it wasn't working before is because I needed to first restart acpid. It may not be the ideal fix, but it works, and that's what matters. 

However, screen blanking after after timeout still doesn't work. I set gnome-power-manager to blank the screen after 1 minute, but it doesn't do anything. I tried using acpi_listen to see if that detected any change, but nothing. Any ideas?

---

