---
title: "Alt+Shift in ubuntu?"
date: 2007-11-10
forum: General Help
---

### Post by idi0t on 2007-11-10
I have ubuntu 7.10 and I`ve installed a language for my country (Macedonia). Now how can I change the keyboard layer (so I can type in my language) while using some program. 

Like there is ALT+SHIFT in windows.. ?

---

### Post by zvacet on 2007-11-10
system>preferences>second tab(I don´t know exact name,cose I don´t use english version)>add your language>chek it and that is it.Of course you need locales.It is in language support.

---

### Post by mikewhatever on 2007-11-10
You can choose the key combination in System>Preferences>Keyboard, Layout Option tab>Group Shift/Lock Behavior. Find 'Alt+Shift chenges group' and tick it.
I think it is Alt+Alt by default.

---

### Post by idi0t on 2007-11-10
Thanks! a lot!

---

### Post by olebon on 2007-11-10
What about XUBUNTU (to be more precise, XFCE)? 
The way described above unfortunately does not work :(

---

### Post by mikewhatever on 2007-11-10
> **olebon said:**
> What about XUBUNTU (to be more precise, XFCE)? 
The way described above unfortunately does not work :(

Does not work, or you had no such gui options to follow? I am not all that familiar with XFCE.

---

### Post by olebon on 2007-11-11
No such GUI options at all. 

All we have is:
System->Language Support for adding new languages without any controls available (a list of 'Supportd Languages' with checkboxes).

Settings->Keyboard Setting for keyboard control. It even has a misguiding folder Shortcuts, but these are the the shortcats for quick launch of applications.

The only way to switch keyboard layouts is the panel of layout switcher, but it lets a switch with a mouse click only.

---

### Post by olebon on 2007-11-12
The problem turned out to be easily solvable: I've simply added 

Option "XkbOptions" "grp:alt_shift_toggle"

to the end of the keyboard section in xorg.conf.

Thanks everybody!

---

