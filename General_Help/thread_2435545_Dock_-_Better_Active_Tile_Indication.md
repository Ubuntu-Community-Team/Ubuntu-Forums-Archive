---
title: "Dock - Better Active Tile Indication?"
date: 2020-01-22
forum: General Help
---

### Post by 2CV67 on 2020-01-22
It is very useful to have an obvious indicator of which Tiles on the Dock are Active (Applications Open).
I seem to remember the Unity Dock having a clear system where the background color of the tiles changed significantly (or am I imagining that?)
Today, with 19.10, there is only a tiny dark red spot (or several spots) hiding at the edge of the screen.
This is anything but obvious & can be quite invisible in some lighting conditions.
The background color changes from black to dark gray for Focused tiles.

Is there any way I can improve this?
Like changing the tiny dark red spots on the left to big bright yellow spots on the right, for instance?
Or preferably by having completely different background colors for Active & Focused tiles?

I looked quite a lot on Internet & in Gnome-Tweaks etc without finding anything.

Thanks for any help!

Or thanks to any developer who pushes in this direction...

---

### Post by dragonfly41 on 2020-01-22
On 18.04 I use gnome-flashback with docky but it is still a tiny orange dot for active tiles.

[https://www.debugpoint.com/2018/05/how-to-install-classic-gnome-flashback-in-ubuntu-18-04-lts/](https://www.debugpoint.com/2018/05/how-to-install-classic-gnome-flashback-in-ubuntu-18-04-lts/)

I use this utility from time to time.

[https://www.giuspen.com/x-tile/](https://www.giuspen.com/x-tile/)

---

### Post by tea for one on 2020-01-22
The Gnome extension Dash To Panel has settings that allow you to change the indicator on open applications (whether active or inactive)

[https://extensions.gnome.org/extension/1160/dash-to-panel/](https://extensions.gnome.org/extension/1160/dash-to-panel/)

---

### Post by 2CV67 on 2020-01-22
Thanks for those replies!

I tried "Dash to Panel" extension & easily found satisfactory settings, with clear (but still red!) indication of Open apps & clear background difference for Focused app.

Just for information for anybody else following this, I found seeming incompatibility between the "Dash to Panel" extension & the existing "Datetime Format" extension I had been using.
I had to remove "Datetime Format" & Replace it with "Clock Override" extension to get the required result.

Consider this SOLVED.

Thanks again!

---

### Post by tea for one on 2020-01-22
> **2CV67 said:**
> Thanks for those replies!

I tried "Dash to Panel" extension & easily found satisfactory settings, with clear (but still red!) indication of Open apps & clear background difference for Focused app.

Consider this SOLVED.

Thanks again!

I'm sure that the red indicator is from your theme.

Perhaps change the theme to give you an alternative colour.

I quite like vimix with colour choices in both light and dark themes:-

[https://www.gnome-look.org/p/1013698/](https://www.gnome-look.org/p/1013698/)

Please use Thread Tools (top right) to mark as solved.

---

### Post by Dennis N on 2020-01-22
The Dash to Dock extension includes configuration options for the active window indicators - various colors and shapes.

---

### Post by 2CV67 on 2020-01-22
Thanks for those extra suggestions!

I liked the look of your thumbnails, Dennis N, and tried to find them in my extension.
But yours are from "Dash to Dock" & I am using "Dash to Panel" & the controls are different.
At first there didn't seem to be anything to reset the colors for unfocused apps, but after trying just about everything, I found I could get the colors I want by going:
```
Dash to Panel > Style > Running indicator style (Focused app) > Gearwheel > Running Indicator Options > Indicator color - Override Theme > 1 window open (or ungrouped) > Select color
```
Not exactly obvious, but finally the results of this extension are EXCELLENT!

Thanks again, everybody!

---

### Post by 2CV67 on 2020-01-23
Spoke too soon!

Dash to Panel isn't working at all today.
I am back to the old dock & old panel.
Looking at the Gnome Extensions website, D-to-P is INSTALLED but OFF.
If I turn it ON, nothing happens.
If I close & re-open the website page, it is again OFF.

I tried uninstalling & reinstalling, with no effect.
It keeps my old settings but they don't work.
Changing settings has no effect.

Hmmm...

---

### Post by tea for one on 2020-01-23
Open Gnome Tweaks - there is a radio button in the top right corner.

This activates or deactivates all the extensions.

---

### Post by 2CV67 on 2020-01-23
That works!

Why do I need to do that?
How often do I need to do that?

Many thanks anyway!

---

### Post by tea for one on 2020-01-23
> **2CV67 said:**
> 
Why do I need to do that?
How often do I need to do that?

I wish that I could give you a definitive answer but I really have no idea.

Best wishes

---

### Post by 2CV67 on 2020-01-24
I see I lost the "Unread Mail" indicator in the Thunderbird Tile.

Haven't yet found how to get that very useful feature back...

EDIT: Looks like it was already lost at my recent upgrade from 19.04 to 19.10 & I hadn't noticed, so I guess it is not part of this thread.

---

### Post by 2CV67 on 2020-02-17
Well - Gnome Tweaks continues to be OFF (occasionally) after starting a new session.
Not only the overall extensions button is OFF but some or all of the extensions are also OFF.
Minor nuisance once you know about it but still a nuisance.
No fix?

The "unread mail" feature has been fixed by the "New Mail Indicator" Gnome Extension, discussed here:
[https://ubuntuforums.org/showthread.php?t=2435759](https://ubuntuforums.org/showthread.php?t=2435759)

---

