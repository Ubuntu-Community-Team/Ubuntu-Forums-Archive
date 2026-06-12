---
title: "Gedit Syntax Highlighting"
date: 2008-05-06
forum: General Help
---

### Post by pmaconi on 2008-05-06
The user manual for Gedit suggests that the syntax highlighting scheme is customizable though a Syntax Highlighting tab under preferences. However, I don't have that tab. Has this feature been removed?

---

### Post by zaussome on 2008-05-06
z

---

### Post by ghost_ryder35 on 2008-05-06
do you mean the 
"highlight matching bracket" ?

---

### Post by pmaconi on 2008-05-06
No, I mean the syntax highlighting for certain file extensions. For example, all #include statements in c++ appear as a lavendar color. I want to change that to something less obnoxious to look at.

---

### Post by Daniel15 on 2008-05-06
I know that the Colour Scheme (on the "Fonts & Colours" tab) changes the highlighing colours (I'm using the "Oblivion" theme; it's a dark one), but I'm not sure if you can edit the colours manually.

---

### Post by fragos on 2008-05-07
After 7.04 Gedit changed how it handles these kinds of changes. Now they provide 4 themes. You can add a new theme but you get no help in building it. Look in /usr/share/gtksourceview-2.0/styles/ and you will find XML files for the 4 styles. You can accomplish what you want creating a copy the the style closest to what you want and renaming it. You can then edit that XML. I asked about this a year ago and the plan was to provide GUI editing of these themes but it hasn't happened yet.

---

