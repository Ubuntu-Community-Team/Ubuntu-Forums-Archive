---
title: "No Icons Visible and Chrome Only Program That Opens"
date: 2018-01-14
forum: General Help
---

### Post by lefrustrated on 2018-01-14
Hey so recently I upgraded to Ubuntu 17.10. Nothing was wrong with it. Today I tried to install custom icons, and was generally just messing around in gnome-tweak-tool. I reboot my computer only to be greeted with my background, an empty dock, and the top bar. I hover over the top bar to find that I can hover over the apps to see what app it is, there just isn't an icon. I click on a couple to see what happens. Chrome opens, but nothing else will. I try > ctrl-alt-t and terminal won't even open. I try deleting all my gnome config files, nothing changes. I reinstall gdm3. Nothing changes. I really don't know what's going on here. Not much on the internet about this.

---

### Post by wyliecoyoteuk on 2018-01-15
Probably your profile is trashed.
Try adding a new user and log in as that user.

---

### Post by lefrustrated on 2018-01-15
> **wyliecoyoteuk said:**
> Probably your profile is trashed.
Try adding a new user and log in as that user.
Yeah the secondary profile works. Is there any way I could fix this without switching profiles though? I have so much on this profile it would probably be way more work transferring all my configurations and programs than just simply fixing the problem in the first place.

---

### Post by wyliecoyoteuk on 2018-01-15
Sorry, not a Gnome user.
There is probably a damaged or missing hidden file. in the file manager set to show hidden files (they start with a dot e.g. .gnome), and compare the two profiles.
The most recently modified files in .gnome or .local might be a clue.

---

### Post by lefrustrated on 2018-01-15
> **wyliecoyoteuk said:**
> Sorry, not a Gnome user.
There is probably a damaged or missing hidden file. in the file manager set to show hidden files (they start with a dot e.g. .gnome), and compare the two profiles.
The most recently modified files in .gnome or .local might be a clue.
 You see that's the thing. I rid of all those hidden files so they could be regenerated. Same stuff kept happening.

---

