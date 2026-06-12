---
title: "Keyboard backlight turns off when typing passward at login"
date: 2021-02-26
forum: General Help
---

### Post by scoaste on 2021-02-26
I set the keyboard to be backlit using [FONT=courier new]xset led on[/FONT].  But  recently, at the lightdm login prompt when I start typing the password,  the light goes dark.  After I log in I can reissue the xset command at  the command line and the keyboard is backlit again for the duration of  the session.  I have the xset command in two places now (the 2nd is a  more recent attempt):
 
/etc/lightdm/lightdm.conf.d/50-kb-backlight.conf

[FONT=courier new] [Seat:*] greeter-setup-script=xset led on[/FONT]

 
/usr/share/lightdm/lightdm.conf.d/50-kb-backlight.conf

[FONT=courier new] [Seat:*] greeter-setup-script=xset led on[/FONT]

 
How can I get the keyboard to be lit continuously on boot?

---

