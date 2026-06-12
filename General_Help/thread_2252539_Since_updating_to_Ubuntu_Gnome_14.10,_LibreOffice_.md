---
title: "Since updating to Ubuntu Gnome 14.10, LibreOffice Calc shows gibberish in spreadsheet"
date: 2014-11-12
forum: General Help
---

### Post by macsociety on 2014-11-12
Since updating from Ubuntu Gnome 14.04 to 14.10, my LibreOffice Calc app has issues opening perfectly good .csv spreadsheets.  These same spreadsheets open fine on other systems I own.  Shows an asian (maybe chinese or Japanese characters) in the fields instead of english.  Tried using Ubuntu Software Center to remove and re-install LibreOffice Calc but made no difference.

Any advise would be great!

Thanks

TJ

---

### Post by bapoumba on 2014-11-12
> Tools > Options > language Settings > Languages, what does it show ?

---

### Post by macsociety on 2014-11-12
All show english.

TJ

> **bapoumba said:**
> > Tools > Options > language Settings > Languages, what does it show ?

---

### Post by bapoumba on 2014-11-13
Do you have an asian language installed on your system ?
What caracter encoding do you use to open the csv ?

---

### Post by macsociety on 2014-11-13
Bapoumba, no asian language that I am aware of.  I did a stock install of 14.04 and stock update to 14.10 so unless that installs other languages, I don't believe I have such a thing.

Not sure how to check the Character Encoding you mention.  Where can I see that?

I am no spreadsheet or linux pro at any means.  grin.

Every app is set as factory when it was installed as I don't go into settings unless I am have issues like this.

For now I downloaded and installed Gnumeric which opens the same file fine.  Only LibreOffice Calc opens it funky.

TJ

> **bapoumba said:**
> Do you have an asian language installed on your system ?
What caracter encoding do you use to open the csv ?

---

### Post by bapoumba on 2014-11-14
When you open a csv, do you get to this dialog box ? Char encoding is at the top. Other than that, I have no real idea. Must be a local calc thing.

Have you played around with templates ? File > Templates > Manage > Spreadsheet > anything in there ?
Or Tools > Options, see if there is anything in the other menus.

---

### Post by macsociety on 2014-11-14
You did it!  Thanks.

Mine was on Unicode UTF-16

Changing back to 8 all is well!

Thanks

TJ

> **bapoumba said:**
> When you open a csv, do you get to this dialog box ? Char encoding is at the top. Other than that, I have no real idea. Must be a local calc thing.

Have you played around with templates ? File > Templates > Manage > Spreadsheet > anything in there ?
Or Tools > Options, see if there is anything in the other menus.

---

### Post by bapoumba on 2014-11-14
You are welcome, glad to see you got it to work :)
Please mark your thread as solved (under Thread tools), thanks.

---

