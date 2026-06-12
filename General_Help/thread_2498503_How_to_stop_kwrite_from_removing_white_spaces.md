---
title: "How to stop kwrite from removing white spaces?"
date: 2024-06-16
forum: General Help
---

### Post by alreve on 2024-06-16
Kwrite removes white spaces at the end of a line. This is very annoying for me because they are a marker I use in a script. 
Any line ending with ', ' (a comma and then a white space) needs something added to it. 

They stay until I save the file (.txt or .csv format). Then the comma stays but the white space vanishes. 
I've found a bug report : [https://www.mail-archive.com/kde-bugs-dist@kde.org/msg275137.html](https://www.mail-archive.com/kde-bugs-dist@kde.org/msg275137.html)
But they say it can be fixed in the settings, so it's been moved to "feature requests".

In my version - kwrite 21.12.3 - I have no such option in the settings. 

Current workaround : 
- find and replace all white spaces by &nbsp; before saving
- find and replace all &nbsp; by white spaces before editing the file
- back it up very often in case I forget to make the change before saving

I can't just find and replace all commas by "comma + white space" then remove double white spaces because on some lines I have only the comma at the end.
Only the comma has a different meaning for my script (it means adding something has to be done but is not urgent). 

All suggestions welcome

---

### Post by currentshaft on 2024-06-16
Use a different character for a marker other than a space? That seems like the easiest and most elegant solution. I mean, why a space? That is perhaps the worst possible character to use for delimination in Linux since it's used for IFS.

---

