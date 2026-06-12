---
title: "gtk-redshift - wont run at startup"
date: 2012-10-20
forum: General Help
---

### Post by keithy on 2012-10-20
Hi there,

Have just upgraded form 12.04 to 12.10 and now gtk-redshift wont run at startup

It runs fine from terminal (no errors) and I have the following added in startup applications

gtk-redshift -t 6000:4800

This ran perfectly in 12.04

I have removed and reinstalled both redshift and gtk-redshift to no avail

running gnome3 for desktop

any clues welcome

thanks

---

### Post by keithy on 2012-10-20
fixed manually adding latt long coordinates

---

### Post by Tiler on 2013-01-06
> **keithy said:**
> fixed manually adding latt long coordinates

If you don't mind, could you show your work?  It'd really help a brother out.  :)

---

### Post by keithy on 2013-01-07
sure,

i use

gtk-redshift -t 6000:4800 -l 51.5:0.11

replace 51.5:0.11 with your own lat/lon

6000:4800 is my own tweaks to the default colour temperatures

HTH

---

### Post by Tiler on 2013-01-07
> **keithy said:**
> sure,

i use

gtk-redshift -t 6000:4800 -l 51.5:0.11

replace 51.5:0.11 with your own lat/lon

6000:4800 is my own tweaks to the default colour temperatures

HTH
You're a gentleman and a scholar!

---

