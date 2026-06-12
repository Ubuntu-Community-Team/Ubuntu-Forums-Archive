---
title: "Are keyboard/regional settings carried over?"
date: 2007-03-30
forum: General Help
---

### Post by cowlip on 2007-03-30
The reason I'm asking "Are keyboard/regional settings carried over?", is because when I installed Feisty through Wubi I had to change the keyboard from Canada to US.  However, when I dropped out of X, I had trouble accessing keys because they seemed to still be using a French Canadian keymap, so there were accents and everything.  I guess X and Gnome and text console store their region settings in different places.

The default region in my "reigional and language" settings in XP was US, but Canada was set as a backup.

---

### Post by ago on 2007-03-30
They should, if they are not it's something we should be informed about so that it can be fixed.

---

### Post by cowlip on 2007-03-30
It's just it seems that it only carried over one of the two languages I had.  So I'll have to figure out a way to set it as "US" in a text console and not just Gnome.

I think I just figued out why, in the "Regional and Language Options" control panel applet in Windows XP:  under the tab, "Regional Options", I have "English (Canada)" set for the dropdown under "Select and item to match its preferences, or click Customize to choose your own formats:".

But under the "Languages tab"->Text services and input languages->Details, my default language is US, my keyboard has the two languages, with US as default.

So that explains why US didn't even exist in my Wubuntu install, I guess it just looks under the regional options tab, not the keyboard tab.

The only reason I have Canada anything set there is so that spellcheckers in Office and OpenOffice check Canadian spelling instead of US spelling, although the keyboard layout is the same as the US, not French as the Wubuntu install did.

I guess Wubi only looks at the "Standards and Formats" instead of the keyboard layout.  And I'm not sure which is the 'right way'.

---

### Post by ago on 2007-03-31
> **cowlip said:**
> It's just it seems that it only carried over one of the two languages I had.
Yep, we carry over the default language, I think that the keyboard layout at the moment is not really autodetected but it gets inferred from the language. Ecology2007 will be able to confirm that.

> So I'll have to figure out a way to set it as "US" in a text console and not just Gnome.
export LANG=en_US

You can put the command in your profile or use an alias to switch locale with a single letter. To change the console keyboard: sudo dpkg-reconfigure console-data

See also

[https://help.ubuntu.com/community/LocaleConf](https://help.ubuntu.com/community/LocaleConf)
[http://www.gentoo.org/doc/en/guide-localization.xml](http://www.gentoo.org/doc/en/guide-localization.xml)

---

### Post by cowlip on 2007-03-31
Thank you for your help, I really appreciate it :) I should have googled but I wasn't really sure where to start in terms of keywords.

I think Canada is just a very odd one out, because it's both Cdn English and Cdn French, and many countries are generally one language (..although maybe not in Europe)

---

### Post by ecology2007 on 2007-03-31
This particular keyboard / language configuration is hard to set without having a table of every common settings for every country.

Give me a clear overview of the differents setups that are in use in canada, and i will make it a special case with custom config.

---

### Post by tuahaa on 2009-08-16
definitely.

---

