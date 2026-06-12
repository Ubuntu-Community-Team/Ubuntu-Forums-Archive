---
title: "How to graphically compare directories - in outline"
date: 2007-09-12
forum: General Help
---

### Post by vjones777 on 2007-09-12
I'm looking for a linux equivalent to windoze's windiff or beyond compare - something that can compare two directories (and subdirectories) and just list the differences.  I don't need (nor want) a character by character comparison of each file - I just need to know which files (and subdirectories) exist in one but not the other.


I thought this would be a commonly required thing, but after much googling I've not found anything suitable.  I've tried "diff -r -b DIR1 DIR2".  It's close, but that does a binary comparison of each file.  Since there are a lot of multimedia files (7Gb+) - doing a bit for bit comparison brings my system to its knees.  It's also not a GUI application, but that's fast becoming a secondary consideration.

xxdiff is GUI, but it also does a binary comparison. :sad:   It also doesn't seem to be able to provide a list of directories with differences - I have to open each directory (& sub-sub dir) to see if there are any differences in each of them.

I suspect this (comparing directory structure and filenames) could be done by writing a script or somesuch, but that seems to be overkill and I'd have thought this was a common thing to need to do.

Does anyone have any suggestions?  ](*,)

---

### Post by Nesman on 2007-09-12
If quick and dirty are options, you might try something like this:

```
ls dir1 | sort > dir1.txt
ls dir2 | sort > dir2.txt
diff dir1.txt dir2.txt

```

---

### Post by s26c.sayan on 2007-09-13
> **vjones777 said:**
> I'm looking for a linux equivalent to windoze's windiff or beyond compare - something that can compare two directories (and subdirectories) and just list the differences.  I don't need (nor want) a character by character comparison of each file - I just need to know which files (and subdirectories) exist in one but not the other.


I thought this would be a commonly required thing, but after much googling I've not found anything suitable.  I've tried "diff -r -b DIR1 DIR2".  It's close, but that does a binary comparison of each file.  Since there are a lot of multimedia files (7Gb+) - doing a bit for bit comparison brings my system to its knees.  It's also not a GUI application, but that's fast becoming a secondary consideration.

xxdiff is GUI, but it also does a binary comparison. :sad:   It also doesn't seem to be able to provide a list of directories with differences - I have to open each directory (& sub-sub dir) to see if there are any differences in each of them.

I suspect this (comparing directory structure and filenames) could be done by writing a script or somesuch, but that seems to be overkill and I'd have thought this was a common thing to need to do.

Does anyone have any suggestions?  ](*,)

Maybe [Meld]("http://meld.sourceforge.net/") does what you are looking for?

---

### Post by julian67 on 2007-09-13
> **vjones777 said:**
> I'm looking for a linux equivalent to windoze's windiff or beyond compare - something that can compare two directories (and subdirectories) and just list the differences.  I don't need (nor want) a character by character comparison of each file - I just need to know which files (and subdirectories) exist in one but not the other.


I thought this would be a commonly required thing, but after much googling I've not found anything suitable.  I've tried "diff -r -b DIR1 DIR2".  It's close, but that does a binary comparison of each file.  Since there are a lot of multimedia files (7Gb+) - doing a bit for bit comparison brings my system to its knees.  It's also not a GUI application, but that's fast becoming a secondary consideration.

xxdiff is GUI, but it also does a binary comparison. :sad:   It also doesn't seem to be able to provide a list of directories with differences - I have to open each directory (& sub-sub dir) to see if there are any differences in each of them.

I suspect this (comparing directory structure and filenames) could be done by writing a script or somesuch, but that seems to be overkill and I'd have thought this was a common thing to need to do.

Does anyone have any suggestions?  ](*,)

There is an easy way :)

I use [emelFM2]("http://emelfm2.net/") it's a dual pane file manager,  incredibly useful in all sorts of ways and it has a compare plug-in which you can enable by going to the settings>commands>plugins> and checking the boxes for compare. It will then be able to show your 2 chosen directories and highlight the files or folders which are present in both.

---

### Post by vjones777 on 2007-09-20
I tried emel2.  It seems interesting - it has a lot of options.  But the compare, when I finally figured out I  had to select the directory in the left pane then RIGHT CLICK, still seems to do a binary comparison, which takes way too long on large files.

Incidently, the terminal window I launch emelfm2 from keeps giving warning messages whenever I run the compare... "(emelfm2:11710): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate  widget with width -9 and height 63".  I don't think thats affecting the compare though.

Nesman.  Thanks very much for that.  That's just what I want.  Now I'll just have to work out how to put that in a script and be able to run it from a menu item, or some primitive GUI.  Scripting's a bit beyond my ability at the moment though.

Thanks
:)

Incidently, the author of xxdiff kindly replied - xxdiff also supports -r at the comand line.  Unfortunatly it won't do an outline comparison (it uses diff, so it compares the content of each file).

---

### Post by julian67 on 2007-09-21
> **vjones777 said:**
> I tried emel2.  It seems interesting - it has a lot of options.  But the compare, when I finally figured out I  had to select the directory in the left pane then RIGHT CLICK, still seems to do a binary comparison, which takes way too long on large files.

I

you're right, sorry. I had only used it on numerous small files and it had been so fast I assumed it was simply using filename, size and so on. I just tried it with very large files and yes it's a binary comparison.  :icon_frown:

---

### Post by vjones777 on 2007-09-22
**dirdiff**  - Its in the repositories.

Under options, make sure that 'literal comparison' isn't selected - it isn't selected when dirdiff is installed.
One thing to note is that by default, dirdiff excludes some type of files e.g. .old, .orig, .save etc.  but these can be changed under options-excluded files.

\\:D/

---

### Post by julian67 on 2007-09-22
> **vjones777 said:**
> **dirdiff**  - Its in the repositories.

Under options, make sure that 'literal comparison' isn't selected - it isn't selected when dirdiff is installed.
One thing to note is that by default, dirdiff excludes some type of files e.g. .old, .orig, .save etc.  but these can be changed under options-excluded files.

\\:D/

That's excellent :) It's now part of my 
emelFM2 context menus, thanks for the tip.

---

### Post by Maverickprowls on 2007-10-02
Thanks for pointing me in the direction of Meld, it's exactly what I was looking for.  I recently managed to delete every one of my personal photos from my system and have been trying to recover from the half-dozen backups I made between systems.  Meld let me compare the ancient back-up folders with ease.

Ta!

---

### Post by kbrill on 2008-01-20
Meld is almost perfect.  It will take a bit of getting used to it's differences with windiff after using that program for so long, but I finished what I needed to do with it without referring to the docs at all.  And that was the strong point of windiff, it's ease of use.  I am looking forward to getting used to meld as I did with windiff.

---

### Post by Mlehliw on 2008-01-26
Beyond Compare 3 will support Linux. It's in private beta right now so you could try emailing the company to try and get in, otherwise the public beta should hopefully be released soon.

---

