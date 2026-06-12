---
title: "Turning off and completely uninstalling on-screen keyboard ubuntu 24"
date: 2024-10-25
forum: General Help
---

### Post by warnoplayer on 2024-10-25
Love ubuntu. I am using ubuntu 24.04. New to ubuntu. With llms I have managed to fix most ubuntu problems. But this one persists and I see no other solution than to turn to this forum and you guys.

I have searched and tried out other solutions and these do not work for my setup. So what do I have?

Asus Zenbook 13900h touchscreen, fantastic and works great with ubuntu up and until 1 month ago. After an update, I have no idea when and where, because i have so far trusted all updates, the on screen keyboard has been off and has not been bothering me.

Every time i click on a text field, this thing pops up. And i have no idea how to truly turn it off. I have tried all hte obvious stuff like clickcing on accessability settings, trying to toggle it on off etc but every time i start firefox, or start terminal, this darn on screen keyboard pops up. The worst part is, when i click minimise or settings button on the on screen keyboard, it will not start the settings and it will not go away. Like, it LIKES to just stay and help when help is not needed. I have to click somewhere else on the desktop  to make the on-screen keyboard go away and hope that it does not pop up when i refocus on firefox or select any other text field, terminal etc.

Can you guys help me uninstall this annoyance of a program completelyl and utterly until someone has had the time to give this program the attention it craves but cannot receive from me?

---

### Post by Norm24 on 2024-10-25
```
sudo apt remove onboard
```

or you can search it in Synaptic and remove it that way also.

---

### Post by grahammechanical on 2024-10-25
We can activate the on screen keyboard at the log in screen. I have done that because sometimes my OS loads to the log in screen without loading the keyboard driver. The mouse works but not the keyboard. In my case, activating the on screen keyboard for login does not cause it to appear once the desktop is loaded. So, System Settings>Accessibility and moving the slider does not de-activate the on screen keyboard?

Regards

---

### Post by warnoplayer on 2024-10-25
thanks so much for the replies

1) sudo apt remove onboard did not cut it. Still on after deinstalling onboard.

2) And moving the slider on system settings acceessibility to the left=deactivate does not cut it either. Still that bugger comes up and irritates. 

Moar suggestions, moar moar! Thanks so much so far![IMG]https://ubuntuforums.org/attachment.php?attachmentid=294415&stc=1[/IMG]

---

### Post by tea for one on 2024-10-25
Settings > Accessibility > Typing > Screen Keyboard
Toggle on/off

---

### Post by Norm24 on 2024-10-25
Maybe try:

```
sudo apt purge onboard
```

---

### Post by grahammechanical on 2024-10-25
> Still that bugger comes up and irritates

lol

ninja-ed by @Norm24

Is your device touch screen? If so, it is possible that the problem is not caused by Onboard but by Gnome On-Screen keyboard (GOK).

[https://help.gnome.org/users/gnome-help/stable/keyboard-osk.html.en](https://help.gnome.org/users/gnome-help/stable/keyboard-osk.html.en)

[https://www.omglinux.com/improved-gnome-on-screen-keyboard/](https://www.omglinux.com/improved-gnome-on-screen-keyboard/)

On my install of 24.04 an on-screen keyboard appears at login but the App Centre offers to Install Onboard. I conclude that there is more than one on-screen keyboard around to mess with your head.

Regards

---

