---
title: "How to change the bottom menu bar to left?"
date: 2023-01-06
forum: General Help
---

### Post by satimis on 2023-01-06
Ubuntu 22.04 desktop

How to change the bottom menu bar to left?

Now the bottom menu bar can ONLY be displayed by clicking "Activites".  It is concealed.

Settings -> Dock (disappears)

Please advise.  Thanks

Regards

---

### Post by MAFoElffen on 2023-01-06
See attached attachment for a screenshot of the setting menu > Appearance > Dock...

Those settings, but change position of dock to right from the appropriate setting there...

---

### Post by satimis on 2023-01-06
> **MAFoElffen said:**
> See attached attachment for a screenshot of the setting menu > Appearance > Dock...

Those settings, but change position of dock to right from the appropriate setting there...
Hi,

Thanks for your advice.

I found it but couldn't solve my problem there.

After login it displays the complete screen without menu bar shown up.  Clicking "Activities" it shows the menu bar at the bottom.  Pls refer the photos attached here.

I couldn't take screenshot.  I have to take photos on mobile phone.

[B][COLOR="#FF0000"]Edit
===[/COLOR][/B]
It was installed on Ubuntu 22.04 boot USB

Regards

---

### Post by MAFoElffen on 2023-01-07
That looks more Like Gnome sessions...

Where in 'dconf editor', if you navigate to org.gnome.shell.extensions.dash-to-dock dock-position... Default is Bottom. So turn off "Use defualt value" then choose Left. Then apply.

---

### Post by satimis on 2023-01-07
> **MAFoElffen said:**
> That looks more Like Gnome sessions...

Where in 'dconf editor', if you navigate to org.gnome.shell.extensions.dash-to-dock dock-position... Default is Bottom. So turn off "Use defualt value" then choose Left. Then apply.

Hi,

Thanks for your advice. 

On Terminal
Performed following steps;
$ sudo apt update
$ sudo apt install dconf-editor

Activities -> dconf-editor

org.gnome.shell.extensions.dash-to-dock

dock-postion        'LEFT'  (Already selected)

Pls see photo attached

Regards

---

### Post by satimis on 2023-01-07
Hi all,

Problem solved as follow;

Activities -> Extension

Start the Extension Manager
Find "Ubuntu Dock" and enable it

Now the "Left Menu" comes back with icons.

But there is a problem on the minimize icon at the right top corner of all windows.  It is missing.
(see attached screenshot)

Any help?  Shall I start a new posting?

Regards

---

### Post by satimis on 2023-01-08
Hi all,

Again, I solved the problem by running following command on Terminal
```

$ gsettings set org.gnome.desktop.wm.preferences button-layout ":minimize,maximize,close"

```

Now the minimize icon displayed on all windows.  Pls refer to attached screenshot.

**[COLOR="#FF0000"]But still I don't know why Ubuntu 22.04 desktop comes to that situation ???[/COLOR]**

Regards

---

### Post by MAFoElffen on 2023-01-08
Or Use "Gnome Tweaks"... Windows Titlebar > Buttons > Minimize > Enabled

---

### Post by satimis on 2023-01-09
> **MAFoElffen said:**
> Or Use "Gnome Tweaks"... Windows Titlebar > Buttons > Minimize > Enabled
Hi,

Thanks for your advice.

"Minimize" already enabled

Regards

---

