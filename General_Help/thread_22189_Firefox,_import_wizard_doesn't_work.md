---
title: "Firefox, import wizard doesn't work"
date: 2005-03-26
forum: General Help
---

### Post by jeremy on 2005-03-26
since installing hoary, the import wizard looks like this. none of the buttons work, all I can do is close the dialogue.

Does anyone else have this problem?

---

### Post by neilius on 2005-04-09
Hi Jeremy,

I am having exactly the same issue after doing a clean install of Hoary yesterday, and here is a screenshot:

[IMG]http://neil.demolish.nu/firefox.png[/IMG] 

Any ideas folks?

Regards,

Neil.   :-)

---

### Post by jeremy on 2005-04-09
Yes, that is exactly the same problem as I have. Sorry (but relieved) to hear that I am not the only one.

---

### Post by sinbad782 on 2005-04-10
Yup - me too!

---

### Post by herting on 2005-04-10
Yeah, it behaved like this in the preview version as well, I assumed after the version switch everything would work in FF, alas I was wrong.

If someone knows how to fix, please enlighten us

<b>Update:</b> Everyone having this problem seems to be in England, perhaps it is the en-gb localization that is fudging it all up

---

### Post by kingojb on 2005-04-10
Good spot herting! I was having the same problem, I've removed the localisation and it works fine now.

---

### Post by herting on 2005-04-10
How does one go about removing firefox localization?

---

### Post by kingojb on 2005-04-10
Open up synaptic, find the package called mozilla-firefox-locale-en-gb and mark it for removal then apply.

---

### Post by herting on 2005-04-10
[QUOTE=kingojb]Open up synaptic, find the package called mozilla-firefox-locale-en-gb and mark it for removal then apply.[/QUOTE]

You are a sexy man, that fixed everything.  Thanks

---

### Post by neilius on 2005-04-10
Sweet stuff, removing the English locale stuff worked... but I'm wondering if i'll lose anything significant.

Regards,

Neil.   :-)

---

### Post by jeremy on 2005-04-10
I just tried removing the locale, and, while it changed, it didn't fix it.

---

### Post by wellmt on 2005-04-10
I've got this problem too, and yes I'm in the UK

---

### Post by sinbad782 on 2005-04-13
I received the firefox-locale-en-gb package too and the bookmark import function now works fine - plus I still have the BBC news RSS feed in the bookmarks toolbar, so not much has really changed!

I'd like to see Firefox's look properly integrated with KDE though - at the moment, the theme is GTK2 taken straight from Gnome. Perhaps if I do a clean install of Kubuntu it might fix this though.

---

### Post by neilius on 2005-04-13
Yeah it was just updated today, seems all is well and I can have that package installed with no problems! Oh to be British!

Regards,

Neil.   :smile:

---

### Post by kingojb on 2005-04-13
We get to have colour spelt properly in the preferences now and have the import work at the same time! Are there any other differences in spellings in firefox?

---

### Post by skoal on 2005-08-25
Hmm.  Sorry for the ~5 month old bump of this thread, but the import wizard still seems like it's "magic" is all smoke and mirrors.

I cannot get the "Import Wizard" to do anything.  I never had the *locale-en-gb package installed either.  I even tried installing it - to no effect.  I uninstalled it too - still no effect.

I have several old bookmarks which I'd like to re-import after a fresh Hoary install.  I'm really not too keen on manually editing an .html file if I don't have to either.  Suggestions? Anyone?

version: Firefox/1.0.6 (Ubuntu package 1.0.6)
.deb version: 1.0.6-0ubuntu0.1

\\//_

---

### Post by -DarkMind- on 2005-08-25
same problem here, i uninstall the *locale-en-gb package and not work :(

ubuntu hoary
mozilla firefox 1.0.6 (with the es-es locale installed )

---

### Post by -DarkMind- on 2005-08-27
the import wizard not work and the plugin's wizard not work too

both show bootons without text and not funcionals


this bug has a lot of time , please FIX IT  :-?

---

### Post by skoal on 2005-09-08
Well, this time my bump is only ~2 weeks, not 5 months as before.  Anyways, I have (by accident) discovered an alternative.  Yes! An alternative to the 3rd rate magician who calls himself the "Import Wizard"...

For bookmarks, just select Bookmarks > Manage Bookmarks > File > Import...and booyah!  Hocus pocus on dat Mr. "Import Wizard"!

\\//_

---

