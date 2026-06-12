---
title: "OpenOffice and Synonyms"
date: 2006-11-11
forum: General Help
---

### Post by hellmet on 2006-11-11
My mom uses Word processing a lot, and recently I made
here switch to Ubuntu.. The first thing she pointed out was..
Where is the thesaurus??
and why the hell doesn't the spell check work??
I don't know if I'm missing something..
but the thesaurus is definitely absent, and the spell check
is awful.. both on the edgy and dapper systems I've worked on...

If someone could point out if I'm gng wrong somewhere...
or suggest some solution.. or a better word processor..
I'd be glad..

thanks

---

### Post by tuxcantfly on 2006-11-11
the thesaurus is there, it's the package openoffice.org-thesaurus-en-us

---

### Post by tuxcantfly on 2006-11-11
install it by doing sudo apt-get install openoffice.org-thesaurus-en-us

---

### Post by tuxcantfly on 2006-11-11
as for the spellcheck, it's myspell-en-us, install using sudo apt-get install myspell-en-us

---

### Post by tuxcantfly on 2006-11-11
if unsatisfied, you could always try abiword, install using sudo apt-get install abiword-gnome

---

### Post by tuxcantfly on 2006-11-11
kword is also good, especially on kubuntu, install using sudo apt-get install kword

---

### Post by tuxcantfly on 2006-11-11
I think the thesaurus for kword has to be installed seperately, install using sudo apt-get install kthesaurus

---

### Post by hellmet on 2006-11-11
both thesaurus and myspell are installed ..but the damn OOo works as if it was never installed.. I just don't seem to see the thesaurus
option .. I mean the right click thing.. 

and no matter what stupid words I type.. it seems to accept it..

---

### Post by hellmet on 2006-11-11
abiword works fine with spellcheck.. but I guess it doesn't have
a thesaurus...??

---

### Post by tuxcantfly on 2006-11-11
might be an issue with your openoffice configuration. rm -r .openoffice* to reset settings, then restart openoffice.org; it should detect the thesaurus and spellcheck on a fresh config.

---

### Post by tuxcantfly on 2006-11-11
how did you install the spellcheck and thesaurus? through apt-get or openoffice's wizard? if one failed, you might want to try out the other

---

### Post by hellmet on 2006-11-11
things installed by themselves .. I mean by default..
both on my mom's edgy and on my dapper ...

---

### Post by homy06 on 2006-11-11
I dunno, is their something better?

I mean, OO has no grammar checker

abiword or OO, which is better for simple school papers and stuff?

---

### Post by Rui Pais on 2006-11-11
Note that in some cases there are thesaurus available for languages that didn't exist in Ubuntu packages.

Using the wizard is the best way (although on a per-user basis).
On Menu go on File->Wizard->Install new dictionaries (or the equivalent on your language). 
With wizard you can install spell checkers, hyphenation checkers and thesaurus.

---

### Post by komputes on 2008-07-11
> **hellmet said:**
> I just don't seem to see the thesaurus
option .. I mean the right click thing..

I can officially say that the "right click thesaurus" is a feature that I miss from word.

This is how I got it working
-Open OpenOffice (redundant)
-File > Wizard > Dictionaries
-Select all three dictionaries for your languages
-Open document
-Tools > Options
-Tools>Options>Language Settings>Languages>Writing Aids, and tick "Check in all languages" in Option section

Note that OOo thesaurus work for me if I use "English(USA)" but not "English(Canada)", this may be the same for your language. This is on a computer using Ubuntu 7.10. On 8.04 I'm not even able to access the DicOOo interface because the window is not sizable and is presented in a square window about 128px x 128px. I'm thinking of filing a bug on both these issues.

---

