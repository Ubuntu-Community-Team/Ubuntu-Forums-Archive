---
title: "editing a spell check dictionary beyond adding new words?"
date: 2013-02-05
forum: General Help
---

### Post by L a r r y on 2013-02-05
There are many words that I use in a day that are not in the dictionaries used by spell checkers, but they are either in the dictionary or are found by Google to be correct on a dictionary web site.

I also have a sloppy "fist" when it comes to typing.  If I add my word to the dictionary and later misspell the word, there are no spell-check suggestions to choose from to get me correctly to my newly-added word.

I don't know why it is too, but many times I get numbers added  to or inserted in words, and these are not marked as misspelled. For those who deal with serial numbers like acve4235t and the like, that would be an issue, unless all alphanumeric strings are in all-caps.

Radio station call signs like WXYZ. XETRA and CKLW are all capitals, as are usually aircraft markings and amateur radio calls formatted like "W7XYZ" so a spell checker could ignore all-capitals containing numbers.

Unless serial numbers contain both upper and lower case letters, they could use all caps to avoid the spell checker's red line.

Are such options available in the spell checkers we use on computers in the Linux world?

Also, how many spell checkers might there be in my Ubuntu 12.04 computer?  Perhaps one for Firefox, another for Thunderbird mail, certainly a third in LibreOffice, and a fourth in general use by Gedit and other apps?

---

### Post by Impavidus on 2013-02-05
As an answer to your last question: there is the classic ispell, the more advanced aspell and finally hunspell, designed to give better results for languages with more complex morphology than english (based on myspell, the project originated in Hungary). All spell checkers can be used as plug-in in other programs or as a stand-alone command line tool.

Both firefox and libreoffice use hunspell. I don't know about other programs. Developers don't want to invent the wheel twice, especially since spell checkers are very complicated tools once you realise they have to work with a large variety of languages with totally different morphologies, so they use a plug-in.

---

