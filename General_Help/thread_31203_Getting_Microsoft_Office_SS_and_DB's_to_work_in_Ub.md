---
title: "Getting Microsoft Office SS and DB's to work in Ubuntu"
date: 2005-05-02
forum: General Help
---

### Post by derrick1985 on 2005-05-02
Hey

I don't know if this has been discussed or not, but here goes:

I have quite a few Microsoft Office Databases/SpreadSheets that I would like to be able to just edit in Linux without having to dual boot back over to XP (I am REALLY trying to get out of it) but, when I open up the database, it opens up for some reason in Writer. So, I went into BASE and tried that, no go apparently.

Also, some of the spreadsheets have Macros, but they don't work. It seems to be complaining about wanting another file for where the macros would be stored?

So, basically, is there anyway to get these to work in Ubuntu (preferably without going to Crossover Office)

---

### Post by shakin on 2005-05-02
I don't think macros are supported because Office macros are written in Visual Basic for Applications, which is a proprietary MS product. It would take a lot of reverse engineering to duplicate that work.

You should be able to run MS Office using Wine, so you won't have to pay for Crossover. Check out my [how-to for DVD Decrypter](http://ubuntuforums.org/showthread.php?t=27369) and follow the steps in section 2 for configuring Wine.

---

