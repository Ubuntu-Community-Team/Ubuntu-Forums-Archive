---
title: "[SOLVED] search like in WIN 98/XP"
date: 2007-08-22
forum: General Help
---

### Post by gobbles414 on 2007-08-22
Hi all,

I'm looking for a desktop search solution for Feisty that is similar to the file search tool in Windows 98/XP. I've already tried *Places --> Search for Files* as well as the search feature in the file browser. Additionally, I've tried *beagle, tracker, and catfish.* from the repositories. *Google Desktop* is not an option for me because of privacy concerns.

The purpose for this search is I need a quick way to delete several hundred hidden files that are scattered amongst several sub-directories of my music folder. Catfish detects these hidden files, but will not allow me to delete them. None of the other programs I have tried have detected the hidden files in question.

Thanks in advance!

---

### Post by Oceanic on 2007-08-22
Do you have permissions to write (and delete) these hidden files?

rightclick on one of these hidden files, etc etc...

I use Kat, very happy with it (just another Beagle port like Kerry Beagle)

---

### Post by gobbles414 on 2007-08-22
Oceanic,

Thanks for replying. Yes, I have read/write permissions to the hidden files in my music folder. The files appear to have been created by the Banshee audio player for DAP sharing. Regarding your suggestion of Kat... even after setting the preferences correctly, I was unable to execute a search. Maybe it is because I am using Ubuntu (Gnome) instead of KUbuntu?

I'd love to read any other suggestions you might have.

---

### Post by gobbles414 on 2007-08-24
Any other ideas...? I could really use some help with this issue. :confused:

---

### Post by stinger30au on 2007-08-24
easy. there is a search tool to add to your top taskbar. right click on it and click "add to panel"
in there is a search tool with a magnify glass on it.
install it. this is pretty much the same as the XP search tool

---

### Post by gobbles414 on 2007-08-24
Greetings stinger30au,

Thanks for replying. As I mentioned in my original post, I have tried both of the GUI search tools that are included in the default Feisty install. Both are fine with most file types. Unfortunately, neither of them is more than 75% accurate when searching for hidden files.

---

### Post by astralsin on 2007-08-24
```
updatedb
locate <whatever you're looking for>
```
 do this at the terminal, works fine on hidden files and directories for me

---

### Post by gobbles414 on 2007-08-24
Hey astralsin,

Would it then be possible to delete all of the detected hidden files with a terminal command?

---

### Post by gobbles414 on 2007-08-26
bump

---

### Post by marsmissionaries on 2007-08-26
Why don't you just open yoiur music folder in nautilus and tell it to display hidden files? and then select and delete them all.

CTRL+H while in the folder.

---

### Post by astralsin on 2007-08-26
gobbles ,yes.  

```
locate <your hidden files> | xargs rm -rf
```

WARNING this will delete anything locate returns.  it would be better to find a directory you want to delete and just rm -rf that directory
or you could do the nautilus thing.  this would be faster though.

---

### Post by gobbles414 on 2007-08-27
Hi all,

Thanks to you all for your replies. I'm going to use astralsin's method for now. The problem with the nautilus method is that I have many sub-directories within my music folder. Hopefully, Ubuntu Gusty will offer a better GUI-based desktop search.

---

