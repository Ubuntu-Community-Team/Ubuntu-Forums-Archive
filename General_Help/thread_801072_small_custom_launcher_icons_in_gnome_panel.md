---
title: "small custom launcher icons in gnome panel"
date: 2008-05-20
forum: General Help
---

### Post by josh on 2008-05-20
hi guys!

ive been trying to customize my gnome de and cant find the answer to this. i want to have a tall panel say around 36px with a large main menu icon and 22x22 launcher icons. i tried checking gconf-editor and dont see any option to set this. when i resize the panel to 36 px, the launcher icons follow the size of the panel. i want them to stay at 22x22 even when the panel is resized to 36 px.

below is a screenshot of what im talking about.

[http://img2.freeimagehosting.net/uploads/9b1c77d2f9.png]("http://img2.freeimagehosting.net/uploads/9b1c77d2f9.png")

i tried creating this file ~/.gtkrc-2.0 (im using gnome 2.22) and pasting :

```
gtk-icon-sizes = "panel=16,16:gtk-large-toolbar=16,16:gtk-small-toolbar=16,16:gtk-button=16,16"
```

please let me know what you think! many thanks!

josh

---

### Post by bobjenkins on 2008-05-20
I have got no idea how to do any of the code, just installed linux a few weeks ago, I have been trying to figure this out also. Only I would like a large toolbar with two columns of small launcher icons. 

Its quite annoying because they will only scale up to a certain size, there has to be a setting somewhere where you can tell it how much to scale; then set that to 0
If I find a solution I will post back

thanks

EDIT
This guy claims to have gotten it to work [https://bugs.launchpad.net/ubuntu/+source/ubuntulooks/+bug/199109]("https://bugs.launchpad.net/ubuntu/+source/ubuntulooks/+bug/199109") the same way you are attempting it, but in Gutsy. He is suggesting that the upgrade to Hardy makes this not applicable anymore. I think we might be out of luck, I will keep persisting though; although its a small thing its bugging me

This worked before Hardy
```
#gtk-icon-sizes="gtk-menu=48,48:gtk-button=48,48:gtk-small-toolbar=48,48:
gtk-large-toolbar=48,48:gtk-dnd=48,48:gtk-dialog=48,48:panel-menu=48,48"

#gtk-icon-sizes="gtk-menu=48,48" #changes icon sizes in menus: file, edit, etc.

#gtk-icon-sizes="gtk-button=48,48" #changes icon sizes on yes, no, delete, cancel,
                                   #back, forward, etc. buttons

#gtk-icon-sizes="gtk-small-toolbar=48,48" #not sure about this

#gtk-icon-sizes="gtk-large-toolbar=48,48" #changes icon size in toolbars (don't know
                                          #why it's 'large'). also changed gaim icon
                                          #size in notification area (system tray)
                                          #default size on my setup was 24,24

#gtk-icon-sizes="gtk-dnd=48,48" #don't know

#gtk-icon-sizes="gtk-dialog=48,48" #don't know

#gtk-icon-sizes="panel-menu=72,72" #changes icon size in so called 'start' menu
                                   #(ussualy it sits in lower or upper left corner)
                                   #default size on my setup was 24,24

gtk-icon-sizes="panel-menu=16,16:gtk-large-toolbar=20,20"
```

---

### Post by josh on 2008-05-20
hey bobjenkins!

thank you for your reply!

yea... that kinda sux, i tried gnome support forums but their website seems to be down. i will update this post once i find something.

---

