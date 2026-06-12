---
title: "Font not Accessible"
date: 2008-06-29
forum: General Help
---

### Post by andrecamp on 2008-06-29
Hi,

I am Running Photoshop 7.0 on Wine HQ. 

Everytime I try to type something in photoshop, this exact phrase comes up.

" Could not complete your request because a default system font could not be obtained. "

However on the font list, I see many fonts, but I just can't type with them. :S

Anyways, someone please help because I need photoshop.

---

### Post by tzulberti on 2008-06-29
MAYBE the problem is because you haven't installed the Microsoft Fonts (Times New Roman, etc...). You could install them using sudo apt-get install msttcorefonts

---

### Post by andrecamp on 2008-06-29
Thanks A Million! 
Problem Solved. :)

---

### Post by andrecamp on 2008-06-29
Actually, one last question.

Where can I find the fonts that I have just installed?

---

### Post by iaculallad on 2008-06-30
Try to browse your:

> /home/user_name/.font

EDIT: Other locations for your fonts are:

> /usr/share/fonts

/usr/local/share/fonts

---

