---
title: "OpenOffice.org Font problem"
date: 2008-02-12
forum: General Help
---

### Post by blastfm on 2008-02-12
I need help with OOo and fonts.
The ARIAL font on OOo is linked(?) to a different font. What I mean is if I use the Arial font or open a document that uses Arial, the characters are displayed using a different font.

I looked for eveything named "arial" and replaced them with a copy of the .ttf file from Windows but still no change.

Anyone knows what is happening here?

I hope the attached screen shot would make it clearer.

Thank you in advance.

---

### Post by apetresc on 2008-02-12
Try refreshing the font cache: ```
sudo fc-cache -f -v
```
You may or may not need to restart X after you do this. I'm not sure.

---

### Post by Hagar Delest on 2008-02-12
Have you installed the msttcorefont package ?

---

### Post by blastfm on 2008-02-13
Thanks for the replies but neither worked. 

I refreshed the font cache and re-started the PC still the same. 
I  already have the msttcorefont installed but marked it for re-installation in synaptic, re-started the PC, still got the same.

I hope this could be fixed since I have a lot of documents that use Arial (work documents that have specific font requirements) and substituting it with a different font won't do :confused:

---

### Post by Hagar Delest on 2008-02-13
Any font replacement set in OOo? Tools>Options>OOo>Fonts.

---

### Post by blastfm on 2008-02-14
> **Hagar de l'Est said:**
> Any font replacement set in OOo? Tools>Options>OOo>Fonts.

None. 

BTW, I tried this before, trying to replace the "not-Arial" into something like "Arial Unicode MS" font, but nothing happened.

---

### Post by Hagar Delest on 2008-02-14
Does it happen only in OOo or also in other applications?
You can try to rename your OOo user profile (~/.openoffice.org2).

---

### Post by blastfm on 2008-02-14
> **Hagar de l'Est said:**
> Does it happen only in OOo or also in other applications?
You can try to rename your OOo user profile (~/.openoffice.org2).

As far as I know,only in OOo. I've never noticed anything wrong with using Arial in other applications.

I renamed .openoffice.org2 to .openoffice_org2.bak but got the same result after starting OOo.

Thanks.

---

### Post by blastfm on 2008-04-28
UPDATE: 

I did a clean install of Hardy hoping it would fix this issue. NOT
I reinstalled OOo again hoping this would fix the issue. NOT

Finally, after booting up my PC on XP, I figured out the name of the font that replaced Arial.. it's called PlanetX (planet5.ttf).
Booting back to Hardy, I searched for all instance of this file all over my PC and found some copies in various .fXXXXX folder (NOTE: XXXXX = Hexadecimal characters). If I remember correctly, these folders were in my home folder. I moved them out to another partition to see what will happen when I re-start OOo, and yes, I have Arial.

Now if only I can open .xlsx :-k

---

