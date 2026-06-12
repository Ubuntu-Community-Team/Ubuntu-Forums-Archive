---
title: "XFCE Appearance Editor - Missing Styles/GTK Themes"
date: 2016-10-29
forum: General Help
---

### Post by zyzzima on 2016-10-29
Hello. So I had a bunch of GTK themes in my usr/share/themes folder and I decided to get rid of them. I went in as root and deleted them. 

After doing this, when I try to install new GTK themes and put them in ~/.local/share/themes or in ~/.themes and open up my Appearance Editor, none of them show up in the 'Styles' tab. Is there any way to fix this? I tried doing a sudo chown -r to regain permission or something, but my terminal gave me an error about the '-r' part and nothing happened.[ATTACH=CONFIG]271859[/ATTACH]

---

### Post by Dennis N on 2016-10-29
Themes should show in the Appearance settings if the theme folders are in any of those locations. If you downloaded themes, did you extract the theme folders from the tar.gz file or zip file? Only the folders inside are placed in those locations.

---

