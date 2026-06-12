---
title: "Firefox icons not playing nice with GTK icon theme"
date: 2008-05-14
forum: General Help
---

### Post by BandD on 2008-05-14
Firefox 3.0b5 under Hardy is leaps and bounds better at interfacing with the GTK themes.  But I've found two icons that don't seem to want to play nice:

1)  The default favicon (the little icon specific to each site)--if a site doesn't have one, then if displays an ugly little page with bent corner and a greenish round blob in the middle that seems to be taken from the default gnome icon set.

2) The folder icons under "Smart Bookmarks"--this seems to be taking the "folder-saved-search" icon from the default gnome icon set as well.

Now the issue for me is that I can't figure out what the icons should be called within my current icon theme for Firefox to pick them up.  I have went through the gnome icon set (/usr/share/icons/gnome) and made matching fielnames in my current icon set.  So I don't know what else to do.   

Is anyone else having this problem with custom icon set enabled?  See the attached screenshot for a good look at what I mean.  It's pretty bad.  You can see what the "folder" icon should be next to "Smart Bookmarks" and how out of place the "folder" icons look for the folders under "Smart Bookmarks"

Am I the only that finds this utterly annoying!?!

---

### Post by rune0077 on 2008-05-14
> **BandD said:**
> 
Is anyone else having this problem with custom icon set enabled? 


Yep, mines giving me those icons as well. Also the "Open new tab" icon is not the same as in my theme.

---

### Post by BandD on 2008-05-14
What is your "New Tab" icon called in your current theme.  Mine seems to show up.  The file is simply "tab-new.png" found in the "actions" folder of each size folder (16x16, 22x22, 24x24, 32x32, 48x48, 64x64, and 124x124--i.e. /home/.icons/CURRENT_ICON_THEME/16x16/apps/new-tab.png)

---

### Post by rune0077 on 2008-05-14
I got both tab-new.png and tab_new.png in the actions folder. It shows up fine elsewhere, just not in Firefox.

---

