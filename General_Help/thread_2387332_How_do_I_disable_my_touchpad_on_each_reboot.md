---
title: "How do I disable my touchpad on each reboot?"
date: 2018-03-17
forum: General Help
---

### Post by AshleyQuick on 2018-03-17
The touchpad device is 12.

---

### Post by kerry_s on 2018-03-17
just turn it off in settings-> devices-> mouse & touchpad

---

### Post by AshleyQuick on 2018-03-17
I don't see that. (This is Lubuntu).

---

### Post by kerry_s on 2018-03-17
> **AshleyQuick said:**
> I don't see that. (This is Lubuntu).

then control center-> mouse

sorry my memory sucks. i think lubuntu has that multi-tier kind of menu thing where it just keeps expanding to the right.

it might be settings-> preferences-> mouse or hardware-> mouse or devices-> mouse

i'm sure it's your menu somewhere. :)

you might want to check out elementary os, just as lite, but dead simple.

---

### Post by AshleyQuick on 2018-03-17
There's a keyboard and mouse area but nothing there regarding the touchpad.

This particular touchpad is ridiculously sensitive and more importantly, I never use it.

---

### Post by AshleyQuick on 2018-03-17
Here's something I tried BUT the touchpad is re-enabled after a reboot. Can someone walk me though a way to make it permanent?

xinput set-prop 13 "Device Enabled" 0

---

### Post by Geoffrey_Arndt on 2018-03-18
So you don't have a F1, F7 or similar hot-key combo using function and one of your number keys?    These act as a toggle - do again to reverse the change.    I haven't seen many laptops without that function.

---

### Post by kerry_s on 2018-03-18
> **AshleyQuick said:**
> Here's something I tried BUT the touchpad is re-enabled after a reboot. Can someone walk me though a way to make it permanent?

xinput set-prop 13 "Device Enabled" 0

add it to your startup apps, it does have startup apps editor right?

sorry, i just installed elementary os, to show my nephew how it's done. so my mind is elsewhere. on the + he just gave me a great trade on 2x4gb of ram, so now i have my laptop maxed out.

---

### Post by AshleyQuick on 2018-03-18
I don't see a startup editor.

The following command works to disable the touchpad UNTIL I reboot: xinput set-prop 13 "Device Enabled" 0

So I have tried creating a crontab using @reboot xinput set-prop 13 "Device Enabled"...that didn't work. So I then created a startup.sh file and placed it in /etc/init.d and THAT didn't work. I've reached an impasse. :(

---

### Post by kerry_s on 2018-03-18
thats because those run as root. you need it to run as you the user.

run this command:
nano ~/.config/autostart/custom_command

copy & paste this:
```

[Desktop Entry]
Name[en_US]=Custom Command
Comment[en_US]=xinput set-prop 13 "Device Enabled" 0
Exec=xinput set-prop 13 "Device Enabled" 0
Icon=application-default-icon
X-GNOME-Autostart-enabled=true
Type=Application

```

press ctrl+x, them y & enter to save.

you should be good to go.

haha, almost screwed up. forgot to remove it from my startup, after i copied & pasted it for you.

---

### Post by AshleyQuick on 2018-03-18
Edit: I entered it incorrectly. Hang on..

---

### Post by kerry_s on 2018-03-18
no sudo, just open the terminal & start typing. my bag that was my fault.

---

### Post by AshleyQuick on 2018-03-18
Didn't work. I can assure you I entered everything correctly as well.  But once I rebooted, the touchpad is still working. :(

---

### Post by AshleyQuick on 2018-03-18
> **kerry_s said:**
> no sudo, just open the terminal & start typing. my bag that was my fault.

Not following you Kerry. I didn't see any mention of sudo in your post.

---

### Post by kerry_s on 2018-03-18
did you use sudo? 
i'm so sorry that was my fault, i installing stuff on my end & it was what i was typing.

do it again, first remove the file.
sudo rm ~/config/autostart/custom_command

now do it again as a normal user, i corrected the instructions.

it failed because you didn't own the file. again my fault, so sorry.

---

### Post by kerry_s on 2018-03-18
> **AshleyQuick said:**
> Not following you Kerry. I didn't see any mention of sudo in your post.

i went back & corrected it as soon as i realized the mistake.

---

### Post by AshleyQuick on 2018-03-18
I entered it exactly as you have it in that post and yet the touchpad is still enabled on reboot. I don't know what else to try.

---

### Post by kerry_s on 2018-03-18
what about preferences-> setup hot keys. click on programs, then the plus at the top, in the window that pops up, put your command in the command field, then click on hotkey 1(pick what ever you want to use), same with hotkey 2

let me get lubuntu installed in the vm & have a look around. i'm running live in baby mode right now.
[ATTACH=CONFIG]278980[/ATTACH]

---

### Post by kerry_s on 2018-03-18
i found it.

preferences-> default applications for lxsession-> autostart
put your command next to add, then click add

why lubuntu? guess it just needs getting use to.
[ATTACH=CONFIG]278981[/ATTACH]

---

