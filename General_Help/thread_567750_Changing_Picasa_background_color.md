---
title: "Changing Picasa background color?"
date: 2007-10-04
forum: General Help
---

### Post by Tom B on 2007-10-04
I recently installed Picasa2 using the .deb file from Google. I really like it, except the background color for the menubar and menus is a dark maroon (see attached screenshot). It really sticks out and makes the text in the menus hard to read. I'm guessing this is configurable somewhere, but I can't figure out where. I can't find anything in the Picasa menus or System>Preferences. Any one know how to fix this?

---

### Post by santiagoward2000 on 2007-10-05
Wow! That's strange!! Have you installed any theme? I've never had that problem. Perhaps you could change it by editing your .gtkrc-2.0 file, but I'm just guessing, I don't know if it works on applications run under wine.

---

### Post by Tom B on 2007-10-05
Not to be dumb, but where is the .gtkrc file? I know it's hidden, so I've made those visible, but i still can't find it (by searching or browsing). And once I do find it, what would I be looking to edit?

---

### Post by santiagoward2000 on 2007-10-05
> **Tom B said:**
> Not to be dumb, but where is the .gtkrc file? I know it's hidden, so I've made those visible, but i still can't find it (by searching or browsing). And once I do find it, what would I be looking to edit?

Actually, if you haven't used it before, you probably hace to create it. But I have no idea on which code you have to add. I'm quite a newbie...

---

### Post by Tom B on 2007-10-07
I found the solution on the Picasa for Linux google group. Picasa tries to pick up your theme when it is started to make the background match. There is apparently a bug in some themes that makes this not work very well. To get around it, you first have to edit the file /opt/picasa/bin/picasa. Comment out the line that tries to "scrape" your theme. This line is towards the bottom and looks like this 
# First, scrape the theme from the environment, if we can
 "$PIC_BINDIR"/wrapper wdi SCRAPETHEME 

Just put a # in front of the second line and save the file (you will probably have to do this as root). Try running picasa now. If it is still messed up, quit picasa, and now you have to delete your ~/.picasa folder (in your home directory, go to View>Show Hidden Files). This will wipe your picasa settings, so you will have to re-set-up and tell it which directories to scan and everything- if you want to be safe, you can just rename the folder to something like "picasabackup" in case things went wrong. Now restart picasa, and the background will be grey.

---

