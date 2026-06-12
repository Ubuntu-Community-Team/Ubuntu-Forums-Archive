---
title: "Removing spellcheck languages in Firefox"
date: 2008-05-19
forum: General Help
---

### Post by Oreo Priest on 2008-05-19
I have several language packs installed on Ubuntu, but I have a particular problem with the Firefox spellcheck. When I right click, it brings up a long list (which I can't screenshot, sorry) including:

de_CH
de_DE
en_US
English / United States
en_ZA
English / United Kingdom
German / Germany
es_ES
German / Luxembourg
en_GB
Spanish / Spain


etc, though the list is about 20 items long. The repetitions (eg. en_US, 
English / United States) actually show up on the list.

I would like to delete all of them except for English / Canada, French, German / Germany, and Spanish / Spain. I have removed every Firefox language add-on, so I know it is not as simple as disabling them. Any help would be appreciated.

---

### Post by y-lee on 2008-05-19
Check and see if you have the **Quick Locale Switcher** Add on installed if so Click on **Preferences** for that add on and go to the Locales tab and uncheck the languages you do not wish. :)

Hope this helps.

---

### Post by Oreo Priest on 2008-06-05
> **y-lee said:**
> Check and see if you have the **Quick Locale Switcher** Add on installed if so Click on **Preferences** for that add on and go to the Locales tab and uncheck the languages you do not wish. :)

Hope this helps.

I don't have it installed. So far as I can tell, none of my add-ons are language related.

---

### Post by digitalhead on 2008-07-08
To correct the spellchecker language in Firefox, open about:config and search for spellchecker.dictionary and change it to whatever is correct. If you want US English, put "en-US". Make sure you have the right syntax though because if it's wrong, such as putting the obvious like "en_us" or "en_US", it will not take effect and reset to whatever the last usable setting was when you close Firefox.

Hope this helps.

---

### Post by Oreo Priest on 2008-07-08
Not really. My default language is just fine, it's only the long list that's annoying me.

---

### Post by garf83 on 2008-07-29
Somewhere I read suggested running Firefox as root and then seeing if you can remove them.  Probably not safe to browse this way though :)

---

### Post by Oreo Priest on 2008-07-29
I still wouldn't know where to go to delete them; it's certainly not in the plugin list.

---

### Post by bryncoles on 2008-07-29
try opening firefox as a normal user, and going to tools->add ons->languages and disable / uninstall from there - is that any help?

---

### Post by Oreo Priest on 2008-07-29
Still no, none of the languages are shown there. I'm fairly certain my Ubuntu language pack is the source.

---

### Post by garf83 on 2008-07-29
I've got installed:

myspell-en-au
myspell-gb-us
myspell-gb-gb
myspell-gb-za

Desciption:
This is the English_british dictionary for use with the myspell spellchecker
which is currently used within OpenOffice.org and the mozilla
spellchecker.

There's a whole lot more of these packages you might be able to uninstall.  Although it won't allow me to remove the us, gb and za ones.  Hope that helps.  Or just do a search for "spell" in Synaptic and see what you've got installed.

---

### Post by Lacos on 2008-11-07
Quite old post. But did you find a solution?

---

### Post by Oreo Priest on 2008-11-07
Still no. Any ideas would be great.

---

### Post by Lacos on 2008-11-12
Look in your */usr/share/myspell/dicts* folder. I deleted all files expect from the DicOOo.sxw file.

---

### Post by Oreo Priest on 2008-11-16
I tried that and it got rid of all of the xx_XX dictionaries. The problem remains that Spanish / Spain is just a symbolic link to es_ES, though both show up (and likewise with fr_CA) so I can't delete the second without losing the first. The list is now down to five things long, however, so I can cope. Thanks!

---

