---
title: "aspell Personal Dictionary - misspelled word"
date: 2013-01-19
forum: General Help
---

### Post by nuk28 on 2013-01-19
I just got Bluefish working with enchant, which is using aspell. I accidentally added a misspelled word (Activites) to the dictionary and want to remove it. I've checked my home directory according to [http://www.mail-archive.com/aspell-user@gnu.org/msg01944.html](http://www.mail-archive.com/aspell-user@gnu.org/msg01944.html), but there are no files called .aspell.en.pws or .aspell.en_US.pws (given by "aspell config personal-path" in a terminal). I installed AbiWord, which also uses enchant, and it is not showing "Activites" as misspelled. Nor do I see any options in AbiWord for editing the dictionaries.

Where is this word getting stored, and how do I delete it!?

---

### Post by Impavidus on 2013-01-19
The correct file name should indeed be ".aspell.<language code>.pws", located in your home directory (/home/username/). Note that this is a hidden file, so in a file manager (nautilus) you'll have to hit ctrl-h to show it, or use ls -a on the command line. You can simply open the file in your favorite text editor (like gedit), delete the offending line and save the file.

---

### Post by nuk28 on 2013-01-19
Yes, but that file does not exist. I can see plenty of hidden files, but .aspell* does not exist. Neither Nautilus nor ls show it. Where else might this information be stored?

This is really annoying me because I use that word a *lot* on [my website]("http://ukanuk.heliohost.org/"), and I seem to forget that last 'i' rather frequently.

---

### Post by Impavidus on 2013-01-19
Are you sure enchant uses aspell? According to the website ([http://www.abisource.com/projects/enchant/](http://www.abisource.com/projects/enchant/)) it has eight different back ends, so it might be using a different one.

---

### Post by nuk28 on 2013-01-21
I actually don't know what backend enchant uses. The enchant.ordering file shows that myspell has priority over aspell. I was getting frustrated looking for things about myspell, however, and it seemed like Thunderbird might use myspell, and Thunderbird was seeing "Activites" as misspelled. I ended up just searching for "Activites" with this command:
```
find . -maxdepth 5 -print0 -type f | xargs -0 grep "Activites"
```
It found ~/.config/enchant/en_US.dic, which contains a short list of the words in my personal dictionary. I deleted "Activites", and now both Bluefish and Abiword show it as misspelled.

---

