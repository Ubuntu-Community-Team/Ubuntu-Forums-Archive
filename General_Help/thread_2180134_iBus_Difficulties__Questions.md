---
title: "iBus Difficulties / Questions"
date: 2013-10-11
forum: General Help
---

### Post by foberle on 2013-10-11
I am running 64 bit Ubuntu 12.04 LTS. Having a need to type both classical Greek and modern Thai text in addition to standard English, I loaded iBus using the Ubuntu Software Center.

I quickly discovered that, because the base iBus package doesn't include support for either of those languages, I also needed to load the ibus-m17n_1.3.3-1.debian package in order to have access to the character sets for each of the aforementioned languages.

Things seem to work well enough for base characters, but no accents or those sorts of characters work, which essentially renders the iBus capability useless for actual work. When using Thai for example, none of the supported vowels or accents (i.e. supported characters is the unfortunate term for those characters that appear over or below the character they modify) seem to be available. Sometimes when I type the appropriate key, I think I can see the correct character flash momentarily, but then it and the character I've attached it to both disappear. I've attempted to adjust the leading and line spacing in those apps that have that capability (e.g. LibreOffice), but this makes no difference (which I don't believe it should, since there is plenty of vertical spacing built in to the fonts). Vowels that are independent characters work just fine.

I don't believe the issue is related to any of the fonts I am using, since all the other characters (consonants and unsupported vowels) appear as expected. So my questions are:

#1) What am I missing? I searched around on the web for some sort of iBus user guide and, although there are lots of technical discussions, I was unable to locate anything that discusses the basics of using it. Indeed, the very few short blurbs I've come across seem to be incorrect - for example, to rotate through multiple foreign keyboards, the Alt+Shift+L command is called for, but I've found that Alt+Shift works just fine and doesn't add whatever character is assigned to the 'L' key.

#2) Is there some way short of looking at an entire font in a font editor to determine if any particular font contains sections for a specific character set (e.g. Greek or Thai)?

#3) What is it that determines which font is used for a particular alphabet when using iBus? For instance, if my base font is set to Garamond and I switch to Greek, the font used is still Garamond, which makes sense, since that font contains Greek characters. But if I switch to Thai, the font that is used is 'Lohit Hindi,' which seems strange to me for two reasons.

The first reason is that 'Lohit Hindi' is primarily a Hindi font - and a sans serif to boot (clashes with the serif Garamond) - and I have several more appropriate Thai fonts available. I can't find anything in the Preferences dialog to alter this.

The second reason is that when I pull up the character map (in LibreOffice, [Insert-Special Character]), the 'Lohit Hindi' font doesn't seem to have any mappings for the Thai character set. So, where are the characters coming from??

Any pointers, guidance, or assistance would be quite helpful ...

---

### Post by grahammechanical on 2013-10-11
Can you confirm the obvious so that we do not get distracted? Have you installed Thai language support and the Thai keyboard layout?

Getting classical Greek is slightly different. I have yet to achieve it but then I cannot type anyway. I get by, some how. There are 4 Greek keyboard layouts, Greek; Greek (eliminate dead keys); Greek (polytonic) and Greek (simple). One of those layouts may give a keyboard layout that might give you key combinations for typing Greek characters with accents.

Fonts are important. The standard fonts installed in Ubuntu are Unicode fonts. These fonts have a very large area for recording characters. A much greater area than the old truetype fonts. So, we have fonts that have characters for many languages and this means that by simply switching keyboard layouts we can type in the characters of other languages. Accented characters may be part of the font set but the trick is to get a keyboard layout that can type those characters.

For example, open a new Libreoffice document and select freeserif as the font and go to Insert>Special Character. A panel will open up showing all the characters in the font set. You will see Basic Greek and Greek Extended as well as Thai. Now try it with Liberation Serif. Do you see the same? I see basic Greek but not extended or Thai. So, fonts do matter. This panel will also give you the Unicode number for each character which we can use to put in the document using a combination of key presses.

Regards.

---

### Post by foberle on 2013-10-12
Graham:

I'm not sure what you mean by "Thai Language Support," but if that is going to System-Language-Install Languages and checking off Thai, then I have done that. English is of course also checked off and so is Chinese (although I don't know how that happened). I have also selected ibus as the keyboard input method system on the same screen.

Using the ibus preferences section, I have installed the Thai TIS-820 keyboard that's part of the m17n package I mentioned. For all of the keys that work (again, as discussed in my post), I use the keyboard exactly as if it was my old Thai Typewriter, so the key mapping seems correct. Again, though, I'm not sure if that's what you are referring to.

If I highlight the Thai text that I have entered, and then change the font to Free Serif (the one you mentioned), the vowels and accents do indeed show up, but I would hate to have to do that with every section of text that I type. I could just use Free Serif as my base font, but I would prefer using something else. So I guess my question boils down to just one of my originals: how can I get ibus to substitute one of my unicode fonts as a source for Thai characters rather than the Lohit Hindi that it now uses? I can't believe it just picks that font out at random, since it doesn't contain the Thai characters itself and evidently gets them from yet another font.

Thanks, by the way, for the quick response. I wasn't really expecting much, since finding someone who types Thai outside of Thailand didn't seem like a sure bet.

Frank

---

