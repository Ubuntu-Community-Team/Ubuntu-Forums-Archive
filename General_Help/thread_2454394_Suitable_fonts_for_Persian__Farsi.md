---
title: "Suitable fonts for Persian / Farsi?"
date: 2020-11-28
forum: General Help
---

### Post by chrysanthemum2 on 2020-11-28
I installed a lot of fonts for the Arabic script, but almost all of them lack the letter p &#1662; which is not used in Arabic but in other languages which use the Arabic script such as Farsi/Persian, Kurdish, Pashto, Urdu and others. Can anyone recommend how to install a set of fonts which include this letter and others which are suitable for typing in Farsi/Persian? I can only find the standard Arabic ones. Thanks.

---

### Post by DuckHook on 2020-11-28
Being mindful that I know nothing about the languages in question, does this page help? [https://alefba.us/free-arabic-persian-farsi-urdu-kurdish-fonts/](https://alefba.us/free-arabic-persian-farsi-urdu-kurdish-fonts/)

The first link ultimately leads to these: [https://github.com/behnam/fonts-farsiweb](https://github.com/behnam/fonts-farsiweb)

They are technically "web" fonts, but this just means that they are designed/kerned for web display. I've never found this to be an impediment to general use.

Are you familiar with font maps and management? The letter you are looking for may already be installed in your current font libraries and you just need to be able to access it more easily. Please have a look at the link in my sig: *Remapping Keys*

---

### Post by chrysanthemum2 on 2020-11-28
> **DuckHook said:**
> Being mindful that I know nothing about the languages in question, does this page help? [https://alefba.us/free-arabic-persian-farsi-urdu-kurdish-fonts/](https://alefba.us/free-arabic-persian-farsi-urdu-kurdish-fonts/)

The first link ultimately leads to these: [https://github.com/behnam/fonts-farsiweb](https://github.com/behnam/fonts-farsiweb)

They are technically "web" fonts, but this just means that they are designed/kerned for web display. I've never found this to be an impediment to general use.

Are you familiar with font maps and management? The letter you are looking for may already be installed in your current font libraries and you just need to be able to access it more easily. Please have a look at the link in my sig: *Remapping Keys*

I tried one of the links in the first post, and it's not a Persian/Farsi font as such, but Persian/Farsi letters mapped to Latin layout. They should be in different You can't really type with it because the characters don't join up in the usual cursive style of Arabic letters. Hopefully that makes sense.

I'm not sure I understand why remapping keys should be necessary. I have the Farsi keyboard layout installed and I can switch between it and English and others I have installed no problem. The letters work no problem, it's just many fonts seem to miss that p &#1662; letter, so it defaults to the standard version which doesn't match with the rest of the font.

---

### Post by DuckHook on 2020-11-28
> **chrysanthemum2 said:**
> …Hopefully that makes sense.
Yes, it does make sense. My ignorance of the languages under discussion is obvious for all to see. I know that Arabic is cursive, but aside from the broadest generalities, I know little else.
> I'm not sure I understand why remapping keys should be necessary.
In the FOSS world (of which Linux is only a part), the matter of what is necessary is a rather academic exercise. It's a community project. People fill in the many holes that still exist when they feel compelled to "scratch that itch". No volunteers, no solution.

I don't know why the letter in question is non&#8209;standard. From your description, it is not actually "missing" so much as it is not already mapped onto the Farsi keyboard. If I understand you properly, it can be invoked using tools like the Unicode combo key, but even then, it is not **kerned** correctly so as to be appear cursive.

I can't help beyond this point. It would be a case of the ignorant trying to enlighten the knowledgeable.

---

### Post by chrysanthemum2 on 2020-11-28
> **DuckHook said:**
> Yes, it does make sense. My ignorance of the languages under discussion is obvious for all to see. I know that Arabic is cursive, but aside from the broadest generalities, I know little else.

In the FOSS world (of which Linux is only a part), the matter of what is necessary is a rather academic exercise. It's a community project. People fill in the many holes that still exist when they feel compelled to "scratch that itch". No volunteers, no solution.

I don't know why the letter in question is non&#8209;standard. From your description, it is not actually "missing" so much as it is not already mapped onto the Farsi keyboard. If I understand you properly, it can be invoked using tools like the Unicode combo key, but even then, it is not **kerned** correctly so as to be appear cursive.

I can't help beyond this point. It would be a case of the ignorant trying to enlighten the knowledgeable.

Thanks for your help. For anyone else reading this, sorry if my description of the problem was not clear. The letter is mapped correctly to the Farsi keyboard layout. The issue is that the letter is seemingly not included in many of the standard fonts available in the repos for Ubuntu for Arabic scripts. I was wondering if there are fonts specifically designed for Farsi, Kurdish, Urdu or any of the other languages which use the Perso-Arabic Abjad which I was unaware of, as these should include this letter, which is a standard letter in those languages.

---

### Post by CatKiller on 2020-11-28
I can't help with this glyph and its representation particularly - I understand that it's supposed to have different forms depending on where it falls in a word? - but Noto could be a place to look. Having glyphs for every language is their specific aim: the name comes from "no tofu."

---

### Post by chrysanthemum2 on 2020-11-29
> **CatKiller said:**
> I can't help with this glyph and its representation particularly - I understand that it's supposed to have different forms depending on where it falls in a word? - but Noto could be a place to look. Having glyphs for every language is their specific aim: the name comes from "no tofu."

Thanks! All of the noto fonts do indeed include this letter! Though there's not many of those fonts.

Yes you are correct, this letter (as with most Arabic letters) has a different form depending on whether it's at the start, middle or end of a word.

---

