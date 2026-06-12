---
title: "Problems installing true type fonts"
date: 2007-05-25
forum: General Help
---

### Post by dezier on 2007-05-25
I am trying to install four true type files of the typeface Times (not Times New Roman). I have read that I could just copy them to fonts:///, but when i try this it doesn't work - it's not possible to copy. I have also tried to place the files in ~/.fonts/ and ran mkfdir and mkfontscale. I have restarted the system.

I just can't figure out why it wount work. (Since my department want me to use Times this bothers me.)

---

### Post by dezier on 2007-05-26
No one? Come on, help me! Should I have to confess to my supervisor that I even can't do such an easy thing as installning a new typeface. She's going to laugh at me and be convinced of never changing from Windows. ;-)

---

### Post by merlinus on 2007-05-26
I have done this by running Thunar as root.  Where are you copying the fonts from?  I copied them from my windows installation, and Type 1 fonts from my psfonts folder there as well.

-merlin

---

### Post by smyrman on 2007-05-27
> **dezier said:**
> I am trying to install four true type files of the typeface Times (not Times New Roman). I have read that I could just copy them to fonts:///, but when i try this it doesn't work - it's not possible to copy. I have also tried to place the files in ~/.fonts/ and ran mkfdir and mkfontscale. I have restarted the system.

I just can't figure out why it wount work. (Since my department want me to use Times this bothers me.)

well i don't know abouth the "fonts:///" protocol i didin't get that to work either..
what i did was that i copied the fonts to this folder:
/usr/share/fonts/
it doesn't seam to matter what subdirectory u install them in..

here is how i installed the "liberation fonts" from my desktop, (useing the gnome-terminal):
*sudo cp -R liberation-fonts-ttf-2 /usr/share/fonts/liberation-fonts-ttf-2*
in my case i just copied the hole folder into /usr/share/fonts, and it works nice..

---

