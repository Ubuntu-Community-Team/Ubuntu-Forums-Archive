---
title: "compiz effects"
date: 2008-05-04
forum: General Help
---

### Post by Trance56k on 2008-05-04
I just installed ubuntu and have compiz working. I'm looking to enable the effect when I close windows they go up in flames. Does anyone know where that option is?

---

### Post by kevinatkins on 2008-05-04
Hi,

You need to install compizconfig-settings-manager, then go into System -> Preferences -> Advanced Desktop Effects Settings.

From there, you can customise everything to your liking.

---

### Post by Trance56k on 2008-05-04
Woot thanks for the quick reply!

---

### Post by 565Customz on 2008-05-04
im in ccsm and i see all the settings but i dont see the setting for that...sorry im a newb

---

### Post by Zorael on 2008-05-04
> **565Customz said:**
> im in ccsm and i see all the settings but i dont see the setting for that...sorry im a newb
Animations under Effects. Go to the tab of the event you want to apply effects to (say, Close Animation) and configure which effects you want it to trigger.

---

### Post by 565Customz on 2008-05-04
sorry should have been more specific...basically when i pull up that tab, fire isnt listed under options...it looks like all the rest are though..

do i need to check the box beside paint fire on screen b4 i go into the close screen settings

---

### Post by caro on 2008-05-04
Under Animations, you should see some tabs.  Click on Close Animations.  At the bottom you will see a list of animations.  The one you want is called Burn.  Go back to the top, click on one of the animations listed by default like Glide, select Edit and then choose Burn in the dialog box.

The Paint Fire On Screen option lets you draw fire with your mouse.

---

### Post by 565Customz on 2008-05-04
ahh...i was looking for fire...lol

---

### Post by caro on 2008-05-04
> **565Customz said:**
> ahh...i was looking for fire...lol

I just started playing with compiz myself.  I spent several hours trying different things before I found some help on the forums and some other websites.  It's actually pretty easy once you figure out what everything does.  Enjoy!

FYI - You may want to create a new profile under Preferences just in case you do something to really hose your system.  That way you can revert back to the default settings easily by using the old profile.

---

### Post by 565Customz on 2008-05-04
ok..i set the duration and all that but it isnt doing anything...what do i select under window types and all that to make it do it...i want it on all windows

---

### Post by caro on 2008-05-04
What do you have in the Window Match box?  Does it look something like:

(type=Normal | Dialog | ModalDialog | Unknown)  or
(type=Normal | Unknown) | name=sun-awt-X11-XFramePeer | name=sun-awt-X11-XDialogPeer) & !(role=toolTipTip | role=qtooltip_label) & !(type=Normal & override_redirect=1) & !(name=gnome-screensaver)

If you originally went to Close Animation and all you changed was Glide 2 to Burn, then all apps (Firefox, terminal, etc) would close with flames.  If you want to make EVERYTHING (even popdown menus, etc), then you need to change those settings too.  The easy way would be to change the other lines in Close Animation to Burn also.  You can also move Burn up in the list to make it take priority.

---

### Post by 565Customz on 2008-05-04
> **caro said:**
> What do you have in the Window Match box?  Does it look something like:

(type=Normal | Dialog | ModalDialog | Unknown)  or
(type=Normal | Unknown) | name=sun-awt-X11-XFramePeer | name=sun-awt-X11-XDialogPeer) & !(role=toolTipTip | role=qtooltip_label) & !(type=Normal & override_redirect=1) & !(name=gnome-screensaver)


um no...nothing close...i set windows match to class=

that makes it do it for EVERYTHING including all your drop down menus and bubbles that pop up when you hold the mouse over something for  a second...now i need to pick the ones i DOnT want lol

---

