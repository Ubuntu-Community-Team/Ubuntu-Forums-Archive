---
title: "Importing adresses in Evolution from Gmail"
date: 2007-11-03
forum: General Help
---

### Post by Hagar55 on 2007-11-03
When I tell my Gmail to export the contacts it does so in a .cvs file that is "comma separated".
Evolution only imports "tab" separated files.
So after the import I'm stuck with almost 200 contacts in which all the e-mail addresses are stuck in the wrong field and are therefor unusable.

Does anyone know a solution to this ?

---

### Post by ajgreeny on 2007-11-03
Just a thought; can you open the cvs file in a word processor and do a find and replace of the commas with tabs in some way.  I've never tried or needed to do it but I wouldn't mind betting it's possible somehow or other!

---

### Post by haldean on 2007-11-03
You can use Sed:
```

sed -i 's/,/\t/g' gmail-to-outlook.csv

```
replace gmail-to-outlook.csv with whatever the filename of the CSV file is, and that script will change all of the commas in the file into tabs. I'm almost sure that that should work :)

---

### Post by Hagar55 on 2007-11-03
If I get Ubuntu working again I'll try it...

---

