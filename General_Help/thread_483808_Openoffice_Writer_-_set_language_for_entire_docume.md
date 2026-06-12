---
title: "Openoffice Writer - set language for entire document?"
date: 2007-06-25
forum: General Help
---

### Post by pickarooney on 2007-06-25
I have a 175-page document here, most of it written in (UK) English with some bits of Spanish and French. All my default language settings are set to UK English and in the main this works, in that the spell-checker defaults to this locale and picks out US spellings as errors as well as underlining the Spanish and French text in red. However, there are a couple of paragraphs where the spell-checker insists on ignoring errors, even rubbish like gaghaghl, and when I manually run the checker with F7 on these text segments the spell-checker language sets itself to US English.
There seems to be no equivalent of the MS Word Tools->Language option to (re-)set the language of a block of text to a particular locale, but is there some other workaround? Ideally, I'd like to be able to set the language of the bits written in Spanish and French to spell-check those separately.

---

### Post by Brucevdk on 2007-06-25
> **pickarooney said:**
> However, there are a couple of paragraphs where the spell-checker insists on ignoring errors, even rubbish like gaghaghl, and when I manually run the checker with F7 on these text segments the spell-checker language sets itself to US English.

Sometimes it helps to set the language using *Tools -> Options -> Language Settings -> Default languages for documents* with having "*For the current document only*" checked. I do remember myself the spellchecker getting confused quite a few times because for some reason it (sometimes) ignores this default setting on previously stored documents.

If this doesn't work and if possible, could you attach the relevant bits of the document? That way I could verify if something I'm recommending has any chance if working :)

> **pickarooney said:**
> There seems to be no equivalent of the MS Word Tools->Language option to (re-)set the language of a block of text to a particular locale, but is there some other workaround? Ideally, I'd like to be able to set the language of the bits written in Spanish and French to spell-check those separately.

As far as I know there is no way to set a language for an entire block of text, you can however use "*Paragraph is $language*" from the context menu (on a red underlined word) for the Spanish and French bits.

EDIT: actually there is, you can select a block of text then in the context menu select Character and on the Font tab there's a language setting.

---

### Post by Golyadkin on 2007-06-25
> Tools -> Options -> Language Settings -> Default languages for documents 
That works fine for me.

---

### Post by pickarooney on 2007-06-25
> you can however use "Paragraph is $language" from the context menu
I don't have this option in my context menu - is it from some plugin?

The default languages option doesn't work, unfortunately, some of the doc is still in USEng and some in UKEng. Hmm, does the fact that I'm using .DOC format rather than .ODT have an effect, I wonder? I've never edited and saved the .DOC on a Windows PC but I do occasionally open a copy of it in Windows to review it. 

I just tested by copying two pages into a fresh OOO file and already I can see that roughly the first page is in UKEng and the second in USEng. I could PM/mail the excerpt if you'd like to have a look at the issue, but am kind of reticent to attach it on the forum (not that anyone's likely to steal it!)

---

### Post by pickarooney on 2007-06-25
Actually, I've found the point where it goes wrong, and it's between the two sentences in the attached file (zipped because the file size limit for DOC is insanely small). If I misspell a word in the first line (just add xxx before it) and spell-check, it's UK, if I do the same in the second bit, it's US. 
I checked to see were there any hidden paragraph marks that might explain the formatting change, but all I see are millions of sigmas and other Greek letters.

---

### Post by Hagar Delest on 2007-06-26
For spell checking issues, see here : [Tutorial for Spell check and Language configuration](http://www.oooforum.org/forum/viewtopic.phtml?t=50862).

---

### Post by pickarooney on 2007-06-26
Excellent. The answer was in the first line of your post there. I would never have thought of looking under the font properties to change the language of a block of text, but you learn something new every day. Page bookmarked - thanks! :)

---

### Post by Golyadkin on 2007-06-27
Not really the most intuitive place to put language settings... Language is a property of text, not of a font.

---

