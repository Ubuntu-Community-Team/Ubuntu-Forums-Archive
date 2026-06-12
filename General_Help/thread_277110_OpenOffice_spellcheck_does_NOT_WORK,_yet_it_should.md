---
title: "OpenOffice spellcheck does NOT WORK, yet it should!"
date: 2006-10-14
forum: General Help
---

### Post by efrancolaporte on 2006-10-14
I need help, I am a newbie and completely clueless about this one.

Spellcheck in OpenOffice does not work at all.  It doesn't detect any mistake, yet I DID set up the language settings and enabled spellcheck in the Tools/options panel in the Writing Aids section.

I have no idea why it doesn't work on ANY document I create in OpenOffice, because if I open a .doc in OpenOffice that has been created from Microsoft Office, the spellcheck DOES work but only in that file.

Secondly, the spellcheck also works in newly created documents in AbiWord. But NEVER in any NEW OpenOffice document.

Why is that??? How do I fix it??? Please help me.  It's such a shame, I love linux if it wasn't for that stupid bug.

Thank you.

--
Emmanuel

---

### Post by mikeoh on 2006-10-14
I had the similar problem of OpenOffice not spellchecking.  It was caused by language being set to a language that didnt have the language spell checking package installed.

Check in the OpenOffice language settings that the set language has an icon next to it saying abc and a blue tick.  If it doesn't it means that you do not have the spell checking installed for that language.  To fix this install the myspell-<language> package,

---

### Post by efrancolaporte on 2006-10-14
Yeah I doublechecked, it DOES have this blue checkmark before the selected language. 
I also checked my installed packages in Synaptic Package Manager, I have the Aspell packages, the Myspell packages AND the language-pack-base packages.

Helllllllp!!!!

---

### Post by efrancolaporte on 2006-10-14
bump

---

### Post by efrancolaporte on 2006-10-14
bump

---

### Post by efrancolaporte on 2006-10-19
bump

---

### Post by Jonathan Starrett on 2006-10-22
I was having the same problem on Gentoo Linux up until today. I solved the problem my installing (emerging) the following packages:

aspell 
aspell-en 
hunspell 
myspell-en

Which are spell checking programs and their associated dictionaries. Now if only I could get the thesaurus to work...](*,)

---

### Post by mikepee on 2007-11-22
I got the same thing.

All packages are installed as should be.

All options are set as should be.

I click spell check or F7 I get the spell checker as I should.

exact text I used to test the spell checker "Speling iz imprtant"

result "Spellcheck Complete" AKA no errors

Ubuntu 7.10 
OOo 2.3

Everything is updated via Synaptic Package Manager.

I have removed and then reinstalled the packages.

If I figure this one out I'll post it.  I can't find anyone who has the problem and managed to solve it yet. WTF!

Mike

---

### Post by authun on 2007-12-03
[QUOTE=Jonathan Starrett;1647977]I was having the same problem on Gentoo Linux up until today. I solved the problem my installing (emerging) the following packages:

aspell 
aspell-en 
hunspell 
myspell-en


This worked for me on Gentoo as well (thanks Jonathan)...

---

### Post by suhasrp on 2007-12-03
I had similar problem with the default language in "Tools->Options->Language Settings->Languages->Default languages for Documents" to "English (India)"
When I changed it to "English (UK)" (which had the Spell Check Icon visible in the list)
I could do spell check. Hope this helps

Cheers
Suhas

> **mikepee said:**
> I got the same thing.

All packages are installed as should be.

All options are set as should be.

I click spell check or F7 I get the spell checker as I should.

exact text I used to test the spell checker "Speling iz imprtant"

result "Spellcheck Complete" AKA no errors

Ubuntu 7.10 
OOo 2.3

Everything is updated via Synaptic Package Manager.

I have removed and then reinstalled the packages.

If I figure this one out I'll post it.  I can't find anyone who has the problem and managed to solve it yet. WTF!

Mike

---

### Post by mikepee on 2007-12-04
I resolved my issue.  I  Had all the packages installed correctly.  Somehow the language setting was set on English Canadian which OOo did not like cause it thought I was in the US.   Truly a weird problem cause I've been to Canada and the English is pretty much the same.  So once I changed it to English US it worked great.  It's always the simple things.

Still can't get the damn search box to work in Nautalis.

Mike

---

### Post by ntu on 2007-12-04
I had a similar problem It was set to English New Zealand and no spell check in OO. Changed it to English UK and OO spell check now works ok.

---

### Post by m4cks on 2008-04-14
efrancolaporte, when you switch to English (USA) or another language that indicates you have spell checking, did that work? Not that you should keep it that way - but I'm wondering if we can isolate this problem to one language.

---

