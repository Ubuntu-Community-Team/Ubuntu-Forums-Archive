---
title: "Terminal problems with Japanese characters"
date: 2007-02-11
forum: General Help
---

### Post by SadaraX on 2007-02-11
EDIT: Solved the problem

I am having some trouble getting Japanese text to show up properly inside my terminal/console. I do not want to use Kterm because it does not have some necessary features. Basically, I just want to know how to get something like mrxvt or konsole or xterm to work with this particular text properly.

I am running Ubuntu 6.10, and I have the Japanese language packs installed. Here is the basic problem:

I have a dictionary file that I am going to parse text from, but normal consoles (xterm, KDE's konsole) do not see the Japanese properly text when I do 'head dictionary_file' (I'm using Jim Breen's edict file) or anything else to output to the console. My consoles do work if I write in Japanese into them (both hiragana, katakana and kanji). I just cannot seem to get the text from this file. 

Here is a small sample of the file:
[http://students.washington.edu/cdobrich/edict.head](http://students.washington.edu/cdobrich/edict.head)

Kterm interprets the information properly, and here is the output from within Kterm with 'head dictionary_file':
> 
&#65311;&#65311;&#65311;&#65311; /EDICT, EDICT_SUB(P), EDICT2 Japanese-English Electronic Dictionary Files/Copyright Electronic Dictionary Research & Development Group - 2006/Created: 2007-02-11/
&#12541; [&#12367;&#12426;&#12363;&#12360;&#12375;] /(n) repetition mark in katakana/
&#12542; [&#12367;&#12426;&#12363;&#12360;&#12375;] /(n) voiced repetition mark in katakana/
&#12445; [&#12367;&#12426;&#12363;&#12360;&#12375;] /(n) repetition mark in hiragana/
&#12446; [&#12367;&#12426;&#12363;&#12360;&#12375;] /(n) voiced repetition mark in hiragana/
&#12291; [&#12362;&#12394;&#12376;&#12367;] /(n) ditto mark/
&#20189; [&#12393;&#12358;&#12376;&#12423;&#12358;] /(n) "as above" mark/
&#12293; [&#12367;&#12426;&#12363;&#12360;&#12375;] /(n) repetition of kanji (sometimes voiced)/
&#12294; [&#12375;&#12417;] /(n) end or closure mark/
&#12294;&#20999; [&#12375;&#12417;&#12365;&#12426;] /(n) closing/cut-off/end/deadline/Closed/No Entrance/


This is what is shows up like on other consoles:
> 
&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533; /EDICT, EDICT_SUB(P), EDICT2 Japanese-English Electronic Dictionary Files/Copyright Electronic Dictionary Research & Development Group - 2006/Created: 2007-02-11/
&#65533;&#65533; [&#65533;&#65533;&#65533;&#43307;&#65533;&#65533;&#65533;&#65533;] /(n) repetition mark in katakana/
&#65533;&#65533; [&#65533;&#65533;&#65533;&#43307;&#65533;&#65533;&#65533;&#65533;] /(n) voiced repetition mark in katakana/
&#65533;&#65533; [&#65533;&#65533;&#65533;&#43307;&#65533;&#65533;&#65533;&#65533;] /(n) repetition mark in hiragana/
&#65533;&#65533; [&#65533;&#65533;&#65533;&#43307;&#65533;&#65533;&#65533;&#65533;] /(n) voiced repetition mark in hiragana/
&#65533;&#65533; [&#65533;&#65533;&#65533;&#676;&#65533;&#65533;&#65533;] /(n) ditto mark/
&#65533;&#65533; [&#65533;&#612;&#65533;&#65533;&#65533;&#65533;&#31014;] /(n) "as above" mark/
&#65533;&#65533; [&#65533;&#65533;&#65533;&#43307;&#65533;&#65533;&#65533;&#65533;] /(n) repetition of kanji (sometimes voiced)/
&#65533;&#65533; [&#65533;&#65533;&#65533;&#65533;] /(n) end or closure mark/
&#65533;&#65533;&#65533;&#65533; [&#65533;&#65533;&#65533;&#6445;&#65533;&#65533;] /(n) closing/cut-off/end/deadline/Closed/No Entrance/



If there is a problem with the dictionary_file itself, like perhaps it has been encoded strangely and needs to be altered, that is an option I would be happy to explore, but I really do not know if that is the root of the issue.

I tried custom compiling mrxvt from source with every variation of the options I could find the ./configure --help list, but nothing seems to work and they all give me garbage output. Again, I basically just want to know how to get something like mrxvt or konsole or xterm to work with the text properly.

---

### Post by ryukent on 2007-02-11
The Jim Breen edict file is encoded in EUC. Try converting it into unicode.

---

### Post by SadaraX on 2007-02-11
> **ryukent said:**
> The Jim Breen edict file is encoded in EUC. Try converting it into unicode.

EDIT: Thanks, that was the problem.

I used the program 'nkf' to convert the text. Now if I only I could get firefox to work with EUC, which I am sure is the reason some Japanese websites show up with broken text in my webbrowser and some pages show up good (because they are probably using UTF-8). Thanks.

---

### Post by ryukent on 2007-02-13
It does, go to View / Character Encoding / More Encodings / East Asian

---

