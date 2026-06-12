---
title: "read Windows Greek Unicode without converting it"
date: 2013-08-18
forum: General Help
---

### Post by jim8 on 2013-08-18
I want to know if its possible to read text documents (which has been created using the greek unicode under windows) with any ubuntu program (like  Text Editor) by DEFAULT. i mean just open the text and read it.
Is that possible? or do i have to convert it first?
I have googled a bit but i couldn't sovle this problem!

---

### Post by Vaphell on 2013-08-18
there is only 1 unicode (not exactly true but for all intents and purposes close enough) - it's a huge table of almost every existing character/symbol in almost every language and allows to freely mix languages. Windows uses code pages (which make mixing languages impossible) and the greek one is win1253.
in the open file dialog there is a combobox with encodings. Add windows1253 to the list and try opening the file with it selected.

---

### Post by grahammechanical on 2013-08-18
I do not think that text editors have formatted text. So, the particular font should not matter but whether it is unicode or not. This is what I get when I type the keys of my querty keyboard into Gedit (text editor) using a Greek keyboard layout and the standard system font.

;&#962;&#949;&#961;&#964;&#965;&#952;&#953;&#959;&#960;[]
&#945;&#963;&#948;&#966;&#947;&#951;&#958;&#954;&#955;\
«&#950;&#967;&#968;&#969;&#946;&#957;&#956;,./

This is what I get when I use the Greek keyboard layout in the forum reply box  with the font set to Times New Roman. I also have Microsoft core fonts installed.

[FONT=times new roman];&#962;&#949;&#961;&#964;&#965;&#952;&#953;&#959;&#960;[]
&#945;&#963;&#948;&#966;&#947;&#951;&#958;&#954;&#955;\
«&#950;&#967;&#968;&#969;&#946;&#957;&#956;,./[/FONT]

Regards.

---

### Post by jim8 on 2013-08-18
> **Vaphell said:**
> there is only 1 unicode (not exactly true but for all intents and purposes close enough) - it's a huge table of almost every existing character/symbol in almost every language and allows to freely mix languages. Windows uses code pages (which make mixing languages impossible) and the greek one is win1253.
in the open file dialog there is a combobox with encodings. Add windows1253 to the list and try opening the file with it selected.
You cannot imagine how much you helped me
Thanks.

---

