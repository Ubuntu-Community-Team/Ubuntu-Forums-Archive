---
title: "Icons missing on the left vertical menu"
date: 2022-12-04
forum: General Help
---

### Post by satimis on 2022-12-04
Hi all,
[B]
Ubuntu 22.04, fresh install
====================
[/B]
The icons on the left vertical menu is missing after increasing the width of the Top Bar.

Please see my posting on another thread;
**How to increase the size of top menu bar**
[https://ubuntuforums.org/showthread.php?t=2481374&page=3&p=14121549#post14121549](https://ubuntuforums.org/showthread.php?t=2481374&page=3&p=14121549#post14121549)

To display the icons I have to click "Activities" at the left corner of the Top Bar.  Then the icons will popup at the bottom of the screen.

Please advise how to fix the problem?

Thanks

Regards

---

### Post by Dennis N on 2022-12-04
Reduce the font size until you see the icons again. Something seems to be going wrong when you make things too large.  

For a UHD display, Dash to Panel may be better. It has width settings up to 96px and font selectable up to 64px. It can be on any edge. Top or bottom is best.

Disable Ubuntu Dock if you use an alternate dock like Dash to Dock.

---

### Post by satimis on 2022-12-04
> **Dennis N said:**
> Reduce the font size until you see the icons again. Something seems to be going wrong when you make things too large.  

For a UHD display, Dash to Panel may be better. It has width settings up to 96px and font selectable up to 64px. It can be on any edge. Top or bottom is best.

No hope

Settings -> Accessibility
Large Text not selected

```

stage {
  font-size: 11pt;
  color: #F7F7F7; }

```

Change font-size back to 11pt

> 
Disable Ubuntu Dock if you use an alternate dock like Dash to Dock.
Could you please explain in more detal?

Thanks

Regards

---

### Post by satimis on 2022-12-04
- deleted -

---

### Post by Dennis N on 2022-12-05
> Could you please explain in more detal?

Look in Extension Manager to see if Dash to Panel is already installed. (see screenshot). 
If not, use the Browse button at the top to search for it and install it. 
Ubuntu Dock is in the System Extensions at the bottom of Extension Manager. Turn it OFF and Turn Dash to Panel ON.
Configure the Dash to Panel settings you want with configuration button (see screenshot).

---

