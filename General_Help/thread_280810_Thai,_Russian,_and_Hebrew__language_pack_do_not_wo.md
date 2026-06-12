---
title: "Thai, Russian, and Hebrew  language pack do not work."
date: 2006-10-20
forum: General Help
---

### Post by Ludwin on 2006-10-20
Hello!

I live in Thailand and, although I am not Thai, have a basic knowledge of the language. I installed the thai language pack, but it does not work well at all.

If I try to use the thai keybord configuration, and choose that configuration in System - Preferences - Keyboard, the system refuses to use it. I find no way to write in Thai.

To check whether this problem is specific to Thai, I installed language packs for two other languages using a non-latin alphabet: Russian and Hebrew. It did not seem to work either.

If I choose one of these langauges for one or more session, a part of the menu will appear in that languages. But it is impossible to write with these alphabets. Signs that should appear above another appear on its side instead...

Browsing Thai webpages with Firefox, I also noted that the Thai characters are displayed in a clumsy way.

Has anyone experience with non-latin alphabets?

---

### Post by teasum on 2006-10-20
> **Ludwin said:**
> 

If I try to use the thai keybord configuration, and choose that configuration in System - Preferences - Keyboard, the system refuses to use it. I find no way to write in Thai.

I don't know if this is what you have done, but you should add the correct Thai keyboard layout first in the System - Preferences - Keyboard dialog.  Mine is "Thailand TIS-820.2538."  Also, did you add the keyboard indicator applet to the Gnome panel?  That's what I use to switch layouts on the fly whien typing in English and Thai.

> 
To check whether this problem is specific to Thai, I installed language packs for two other languages using a non-latin alphabet: Russian and Hebrew. It did not seem to work either.

These are all CTL (complex text layout, I think..??) languages, so there are a couple issues that might make them not work.  First, I would check to see that you have the right fonts installed and selected, since some will simply not work.

> 
Browsing Thai webpages with Firefox, I also noted that the Thai characters are displayed in a clumsy way.

Try going to Edit - Preferences - Content - Fonts & Colors - Advanced.  In that dialog, you can choose the font sets for Western and other languages separately.  Try choosing Loma for Thai, and see if Thai webpages show up correctly after that.

Good luck!

---

### Post by Ludwin on 2006-10-21
Thanks for you advice, Teasum. I browsed the packet manager menus and saw that there are many more packages related to languages than language-package. There are gnome-specific language packs as well, language-support* packages,
and myspel* packages. I am installing all the packages with the *-th extension in it, and I hope it will eventually work.

---

### Post by Ludwin on 2006-10-23
> **teasum said:**
> 
Try going to Edit - Preferences - Content - Fonts & Colors - Advanced.  In that dialog, you can choose the font sets for Western and other languages separately.  Try choosing Loma for Thai, and see if Thai webpages show up correctly after that.
Good luck!

It worked. But I had to specify in the browser that I don want to use the webmaster specified encodings.

---

