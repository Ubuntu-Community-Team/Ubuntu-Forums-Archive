---
title: "Rename all directories begining with &quot;video - &quot;"
date: 2018-09-24
forum: General Help
---

### Post by mainemojo on 2018-09-24
I have a directory with sub-directories.  Some of the sub-directories I want to rename begin with "video - ".  An example would be "video - Excel 2016 formulas".  I would like to remove and rename the example to "Excel 2016 formulas".  The 'v' in videos may or may not be upper case. I both instances, I want it removed.

What I have so far is:

```
find . -type d -iname "video - *"
```

I know I need a '-exec rm', but I don't know the specifics.  Or should I be using 'rename'?

---

### Post by steeldriver on 2018-09-24
You certainly do **not **need a '-exec rm' - that will [COLOR=#ff0000]**r**[/COLOR]e[COLOR=#ff0000]**m**[/COLOR]ove (delete) the files

---

### Post by mainemojo on 2018-09-24
So if I use a '-exec mv', then what?

Would the proper way be:
```
for f in *; do mv '$f" "${f#video - }";done
```

or

```
rename -v 'x/video - //' *
```

---

### Post by billrbilly on 2018-09-24
**gprename** is available for install thru package manager or in terminal [COLOR=#445263][FONT=Arimo]**sudo apt-get install gprename **
[/FONT][/COLOR]It should easily rename those folders from GUI
Can be run from terminal **gprename**
Takes a bit of getting used to, but not that hard at all from what I remember when I used it

navigate to folder containing subfolders
As eg...  [COLOR=#000000]video - Excel 2016 formulas, including the spaces you need the first 8 characters removed
Under insert/delete you can have it delete between 0 and 8.... 
Then click Rename, not sure if Preview always works
You may want to backup first just to be on safe side till you are use to the utility

Edit-- sorry, just realized you said you have other folders that start with different names in that directory
In that case the Replace/remove option might be better
Replace [B]video - 
[/B]with kept left blank then click on Preview, if everything looks good click Rename... It does have an undo feature[/COLOR]

---

