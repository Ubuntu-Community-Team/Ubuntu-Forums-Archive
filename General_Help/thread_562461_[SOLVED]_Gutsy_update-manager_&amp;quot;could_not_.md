---
title: "[SOLVED] Gutsy update-manager &amp;quot;could not calculate upgrade"
date: 2007-09-28
forum: General Help
---

### Post by n3tfury on 2007-09-28
hi folks.  new install from yesterday's release was going fine until there were supposedly 11 updates available (this was the second update today, the first one went just fine).  basically it asks if i want to run a partial upgrade and i click yes since the other option is to cancel.  then i get the screenshot below.  

here is the text from /var/log/dist-upgrade/apt.log:

```
Installing openoffice.org-core as dep of openoffice.org-gnome
Installing openoffice.org-common as dep of openoffice.org-core
Installing python-uno as dep of openoffice.org-writer
Installing openoffice.org-draw as dep of openoffice.org-impress
Installing libgtk2.0-0 as dep of gtk2-engines-pixbuf
Installing openoffice.org-core as dep of openoffice.org-calc
Starting
Starting 2
Investigating openoffice.org-l10n-en-gb
Package openoffice.org-l10n-en-gb has broken dep on openoffice.org-core
  Considering openoffice.org-core 21 as a solution to openoffice.org-l10n-en-gb 8
  Removing openoffice.org-l10n-en-gb rather than change openoffice.org-core
Investigating openoffice.org-l10n-en-za
Package openoffice.org-l10n-en-za has broken dep on openoffice.org-core
  Considering openoffice.org-core 21 as a solution to openoffice.org-l10n-en-za 8
  Removing openoffice.org-l10n-en-za rather than change openoffice.org-core
Investigating language-pack-en-base
Package language-pack-en-base has broken dep on language-pack-en
Investigating language-support-en
Package language-support-en has broken dep on openoffice.org-l10n-en-gb
  Considering openoffice.org-l10n-en-gb 8 as a solution to language-support-en 14
  Added openoffice.org-l10n-en-gb to the remove list
Package language-support-en has broken dep on openoffice.org-l10n-en-za
  Considering openoffice.org-l10n-en-za 8 as a solution to language-support-en 14
  Added openoffice.org-l10n-en-za to the remove list
  Fixing language-support-en via keep of openoffice.org-l10n-en-gb
  Fixing language-support-en via keep of openoffice.org-l10n-en-za
Investigating openoffice.org-l10n-en-gb
Package openoffice.org-l10n-en-gb has broken dep on openoffice.org-core
  Considering openoffice.org-core 21 as a solution to openoffice.org-l10n-en-gb 8
  Removing openoffice.org-l10n-en-gb rather than change openoffice.org-core
Investigating openoffice.org-l10n-en-za
Package openoffice.org-l10n-en-za has broken dep on openoffice.org-core
  Considering openoffice.org-core 21 as a solution to openoffice.org-l10n-en-za 8
  Removing openoffice.org-l10n-en-za rather than change openoffice.org-core
 Try to Re-Instate language-pack-en-base
Investigating language-support-en
Package language-support-en has broken dep on openoffice.org-l10n-en-gb
  Considering openoffice.org-l10n-en-gb 8 as a solution to language-support-en 14
  Added openoffice.org-l10n-en-gb to the remove list
Package language-support-en has broken dep on openoffice.org-l10n-en-za
  Considering openoffice.org-l10n-en-za 8 as a solution to language-support-en 14
  Added openoffice.org-l10n-en-za to the remove list
  Fixing language-support-en via keep of openoffice.org-l10n-en-gb
  Fixing language-support-en via keep of openoffice.org-l10n-en-za
Investigating openoffice.org-l10n-en-gb
Package openoffice.org-l10n-en-gb has broken dep on openoffice.org-core
  Considering openoffice.org-core 21 as a solution to openoffice.org-l10n-en-gb 14
  Removing openoffice.org-l10n-en-gb rather than change openoffice.org-core
Investigating openoffice.org-l10n-en-za
Package openoffice.org-l10n-en-za has broken dep on openoffice.org-core
  Considering openoffice.org-core 21 as a solution to openoffice.org-l10n-en-za 14
  Removing openoffice.org-l10n-en-za rather than change openoffice.org-core
Investigating language-support-en
Package language-support-en has broken dep on openoffice.org-l10n-en-gb
  Considering openoffice.org-l10n-en-gb 21 as a solution to language-support-en 14
  Removing language-support-en rather than change openoffice.org-l10n-en-gb
Investigating thunderbird-locale-en-gb
Package thunderbird-locale-en-gb has broken dep on thunderbird
  Considering thunderbird 1 as a solution to thunderbird-locale-en-gb 8
Package thunderbird-locale-en-gb has broken dep on language-support-en
  Considering language-support-en 21 as a solution to thunderbird-locale-en-gb 8
  Or group remove for thunderbird-locale-en-gb
Done
Starting
Starting 2
Investigating language-support-en
Package language-support-en has broken dep on openoffice.org-l10n-en-gb
  Considering openoffice.org-l10n-en-gb 1 as a solution to language-support-en 10004
  Added openoffice.org-l10n-en-gb to the remove list
Package language-support-en has broken dep on openoffice.org-l10n-en-za
  Considering openoffice.org-l10n-en-za 1 as a solution to language-support-en 10004
  Added openoffice.org-l10n-en-za to the remove list
Package language-support-en has broken dep on thunderbird-locale-en-gb
  Considering thunderbird-locale-en-gb 1 as a solution to language-support-en 10004
  Added thunderbird-locale-en-gb to the remove list
  Fixing language-support-en via keep of openoffice.org-l10n-en-gb
  Fixing language-support-en via keep of openoffice.org-l10n-en-za
  Fixing language-support-en via keep of thunderbird-locale-en-gb
Investigating openoffice.org-l10n-en-gb
Package openoffice.org-l10n-en-gb has broken dep on openoffice.org-core
  Considering openoffice.org-core 17 as a solution to openoffice.org-l10n-en-gb 1
  Removing openoffice.org-l10n-en-gb rather than change openoffice.org-core
Investigating openoffice.org-l10n-en-za
Package openoffice.org-l10n-en-za has broken dep on openoffice.org-core
  Considering openoffice.org-core 17 as a solution to openoffice.org-l10n-en-za 1
  Removing openoffice.org-l10n-en-za rather than change openoffice.org-core
Investigating language-support-en
Package language-support-en has broken dep on openoffice.org-l10n-en-gb
  Considering openoffice.org-l10n-en-gb 1 as a solution to language-support-en 10004
  Added openoffice.org-l10n-en-gb to the remove list
Package language-support-en has broken dep on openoffice.org-l10n-en-za
  Considering openoffice.org-l10n-en-za 1 as a solution to language-support-en 10004
  Added openoffice.org-l10n-en-za to the remove list
  Fixing language-support-en via keep of openoffice.org-l10n-en-gb
  Fixing language-support-en via keep of openoffice.org-l10n-en-za
Investigating openoffice.org-l10n-en-gb
Package openoffice.org-l10n-en-gb has broken dep on openoffice.org-core
  Considering openoffice.org-core 17 as a solution to openoffice.org-l10n-en-gb 1
  Removing openoffice.org-l10n-en-gb rather than change openoffice.org-core
Investigating openoffice.org-l10n-en-za
Package openoffice.org-l10n-en-za has broken dep on openoffice.org-core
  Considering openoffice.org-core 17 as a solution to openoffice.org-l10n-en-za 1
  Removing openoffice.org-l10n-en-za rather than change openoffice.org-core
Investigating language-support-en
Package language-support-en has broken dep on openoffice.org-l10n-en-gb
  Considering openoffice.org-l10n-en-gb 1 as a solution to language-support-en 10004
  Added openoffice.org-l10n-en-gb to the remove list
Package language-support-en has broken dep on openoffice.org-l10n-en-za
  Considering openoffice.org-l10n-en-za 1 as a solution to language-support-en 10004
  Added openoffice.org-l10n-en-za to the remove list
  Fixing language-support-en via keep of openoffice.org-l10n-en-gb
  Fixing language-support-en via keep of openoffice.org-l10n-en-za
Investigating openoffice.org-l10n-en-gb
Package openoffice.org-l10n-en-gb has broken dep on openoffice.org-core
  Considering openoffice.org-core 17 as a solution to openoffice.org-l10n-en-gb 10004
  Added openoffice.org-core to the remove list
  Fixing openoffice.org-l10n-en-gb via keep of openoffice.org-core
Investigating openoffice.org-gnome
Package openoffice.org-gnome has broken dep on openoffice.org-core
  Considering openoffice.org-core 10004 as a solution to openoffice.org-gnome 0
  Holding Back openoffice.org-gnome rather than change openoffice.org-core
Investigating openoffice.org-impress
Package openoffice.org-impress has broken dep on openoffice.org-core
  Considering openoffice.org-core 10004 as a solution to openoffice.org-impress 0
  Re-Instated openoffice.org-gnome
  Re-Instated openoffice.org-core
  Re-Instated openoffice.org-impress
Investigating openoffice.org-l10n-en-gb
Package openoffice.org-l10n-en-gb has broken dep on openoffice.org-core
  Considering openoffice.org-core 10004 as a solution to openoffice.org-l10n-en-gb 10004
  Removing openoffice.org-l10n-en-gb rather than change openoffice.org-core
Investigating openoffice.org-l10n-en-za
Package openoffice.org-l10n-en-za has broken dep on openoffice.org-core
  Considering openoffice.org-core 10004 as a solution to openoffice.org-l10n-en-za 10004
  Removing openoffice.org-l10n-en-za rather than change openoffice.org-core
Investigating language-support-en
Package language-support-en has broken dep on openoffice.org-l10n-en-gb
  Considering openoffice.org-l10n-en-gb 10004 as a solution to language-support-en 10004
Package language-support-en has broken dep on openoffice.org-l10n-en-za
  Considering openoffice.org-l10n-en-za 10004 as a solution to language-support-en 10004
Done
ERROR:root:Dist-upgrade failed: 'E:Unable to correct problems, you have held broken packages.'
Installing openoffice.org-core as dep of openoffice.org-gnome
Installing openoffice.org-common as dep of openoffice.org-core
Installing python-uno as dep of openoffice.org-writer
Installing openoffice.org-draw as dep of openoffice.org-impress
Installing libgtk2.0-0 as dep of gtk2-engines-pixbuf
Installing openoffice.org-core as dep of openoffice.org-calc
Starting
Starting 2
Investigating openoffice.org-l10n-en-gb
Package openoffice.org-l10n-en-gb has broken dep on openoffice.org-core
  Considering openoffice.org-core 21 as a solution to openoffice.org-l10n-en-gb 8
  Removing openoffice.org-l10n-en-gb rather than change openoffice.org-core
Investigating openoffice.org-l10n-en-za
Package openoffice.org-l10n-en-za has broken dep on openoffice.org-core
  Considering openoffice.org-core 21 as a solution to openoffice.org-l10n-en-za 8
  Removing openoffice.org-l10n-en-za rather than change openoffice.org-core
Investigating language-pack-en-base
Package language-pack-en-base has broken dep on language-pack-en
Investigating language-support-en
Package language-support-en has broken dep on openoffice.org-l10n-en-gb
  Considering openoffice.org-l10n-en-gb 8 as a solution to language-support-en 14
  Added openoffice.org-l10n-en-gb to the remove list
Package language-support-en has broken dep on openoffice.org-l10n-en-za
  Considering openoffice.org-l10n-en-za 8 as a solution to language-support-en 14
  Added openoffice.org-l10n-en-za to the remove list
  Fixing language-support-en via keep of openoffice.org-l10n-en-gb
  Fixing language-support-en via keep of openoffice.org-l10n-en-za
Investigating openoffice.org-l10n-en-gb
Package openoffice.org-l10n-en-gb has broken dep on openoffice.org-core
  Considering openoffice.org-core 21 as a solution to openoffice.org-l10n-en-gb 8
  Removing openoffice.org-l10n-en-gb rather than change openoffice.org-core
Investigating openoffice.org-l10n-en-za
Package openoffice.org-l10n-en-za has broken dep on openoffice.org-core
  Considering openoffice.org-core 21 as a solution to openoffice.org-l10n-en-za 8
  Removing openoffice.org-l10n-en-za rather than change openoffice.org-core
 Try to Re-Instate language-pack-en-base
Investigating language-support-en
Package language-support-en has broken dep on openoffice.org-l10n-en-gb
  Considering openoffice.org-l10n-en-gb 8 as a solution to language-support-en 14
  Added openoffice.org-l10n-en-gb to the remove list
Package language-support-en has broken dep on openoffice.org-l10n-en-za
  Considering openoffice.org-l10n-en-za 8 as a solution to language-support-en 14
  Added openoffice.org-l10n-en-za to the remove list
  Fixing language-support-en via keep of openoffice.org-l10n-en-gb
  Fixing language-support-en via keep of openoffice.org-l10n-en-za
Investigating openoffice.org-l10n-en-gb
Package openoffice.org-l10n-en-gb has broken dep on openoffice.org-core
  Considering openoffice.org-core 21 as a solution to openoffice.org-l10n-en-gb 14
  Removing openoffice.org-l10n-en-gb rather than change openoffice.org-core
Investigating openoffice.org-l10n-en-za
Package openoffice.org-l10n-en-za has broken dep on openoffice.org-core
  Considering openoffice.org-core 21 as a solution to openoffice.org-l10n-en-za 14
  Removing openoffice.org-l10n-en-za rather than change openoffice.org-core
Investigating language-support-en
Package language-support-en has broken dep on openoffice.org-l10n-en-gb
  Considering openoffice.org-l10n-en-gb 21 as a solution to language-support-en 14
  Removing language-support-en rather than change openoffice.org-l10n-en-gb
Investigating thunderbird-locale-en-gb
Package thunderbird-locale-en-gb has broken dep on thunderbird
  Considering thunderbird 1 as a solution to thunderbird-locale-en-gb 8
Package thunderbird-locale-en-gb has broken dep on language-support-en
  Considering language-support-en 21 as a solution to thunderbird-locale-en-gb 8
  Or group remove for thunderbird-locale-en-gb
Done
Starting
Starting 2
Investigating language-support-en
Package language-support-en has broken dep on openoffice.org-l10n-en-gb
  Considering openoffice.org-l10n-en-gb 1 as a solution to language-support-en 10004
  Added openoffice.org-l10n-en-gb to the remove list
Package language-support-en has broken dep on openoffice.org-l10n-en-za
  Considering openoffice.org-l10n-en-za 1 as a solution to language-support-en 10004
  Added openoffice.org-l10n-en-za to the remove list
Package language-support-en has broken dep on thunderbird-locale-en-gb
  Considering thunderbird-locale-en-gb 1 as a solution to language-support-en 10004
  Added thunderbird-locale-en-gb to the remove list
  Fixing language-support-en via keep of openoffice.org-l10n-en-gb
  Fixing language-support-en via keep of openoffice.org-l10n-en-za
  Fixing language-support-en via keep of thunderbird-locale-en-gb
Investigating openoffice.org-l10n-en-gb
Package openoffice.org-l10n-en-gb has broken dep on openoffice.org-core
  Considering openoffice.org-core 17 as a solution to openoffice.org-l10n-en-gb 1
  Removing openoffice.org-l10n-en-gb rather than change openoffice.org-core
Investigating openoffice.org-l10n-en-za
Package openoffice.org-l10n-en-za has broken dep on openoffice.org-core
  Considering openoffice.org-core 17 as a solution to openoffice.org-l10n-en-za 1
  Removing openoffice.org-l10n-en-za rather than change openoffice.org-core
Investigating language-support-en
Package language-support-en has broken dep on openoffice.org-l10n-en-gb
  Considering openoffice.org-l10n-en-gb 1 as a solution to language-support-en 10004
  Added openoffice.org-l10n-en-gb to the remove list
Package language-support-en has broken dep on openoffice.org-l10n-en-za
  Considering openoffice.org-l10n-en-za 1 as a solution to language-support-en 10004
  Added openoffice.org-l10n-en-za to the remove list
  Fixing language-support-en via keep of openoffice.org-l10n-en-gb
  Fixing language-support-en via keep of openoffice.org-l10n-en-za
Investigating openoffice.org-l10n-en-gb
Package openoffice.org-l10n-en-gb has broken dep on openoffice.org-core
  Considering openoffice.org-core 17 as a solution to openoffice.org-l10n-en-gb 1
  Removing openoffice.org-l10n-en-gb rather than change openoffice.org-core
Investigating openoffice.org-l10n-en-za
Package openoffice.org-l10n-en-za has broken dep on openoffice.org-core
  Considering openoffice.org-core 17 as a solution to openoffice.org-l10n-en-za 1
  Removing openoffice.org-l10n-en-za rather than change openoffice.org-core
Investigating language-support-en
Package language-support-en has broken dep on openoffice.org-l10n-en-gb
  Considering openoffice.org-l10n-en-gb 1 as a solution to language-support-en 10004
  Added openoffice.org-l10n-en-gb to the remove list
Package language-support-en has broken dep on openoffice.org-l10n-en-za
  Considering openoffice.org-l10n-en-za 1 as a solution to language-support-en 10004
  Added openoffice.org-l10n-en-za to the remove list
  Fixing language-support-en via keep of openoffice.org-l10n-en-gb
  Fixing language-support-en via keep of openoffice.org-l10n-en-za
Investigating openoffice.org-l10n-en-gb
Package openoffice.org-l10n-en-gb has broken dep on openoffice.org-core
  Considering openoffice.org-core 17 as a solution to openoffice.org-l10n-en-gb 10004
  Added openoffice.org-core to the remove list
  Fixing openoffice.org-l10n-en-gb via keep of openoffice.org-core
Investigating openoffice.org-gnome
Package openoffice.org-gnome has broken dep on openoffice.org-core
  Considering openoffice.org-core 10004 as a solution to openoffice.org-gnome 0
  Holding Back openoffice.org-gnome rather than change openoffice.org-core
Investigating openoffice.org-impress
Package openoffice.org-impress has broken dep on openoffice.org-core
  Considering openoffice.org-core 10004 as a solution to openoffice.org-impress 0
  Re-Instated openoffice.org-gnome
  Re-Instated openoffice.org-core
  Re-Instated openoffice.org-impress
Investigating openoffice.org-l10n-en-gb
Package openoffice.org-l10n-en-gb has broken dep on openoffice.org-core
  Considering openoffice.org-core 10004 as a solution to openoffice.org-l10n-en-gb 10004
  Removing openoffice.org-l10n-en-gb rather than change openoffice.org-core
Investigating openoffice.org-l10n-en-za
Package openoffice.org-l10n-en-za has broken dep on openoffice.org-core
  Considering openoffice.org-core 10004 as a solution to openoffice.org-l10n-en-za 10004
  Removing openoffice.org-l10n-en-za rather than change openoffice.org-core
Investigating language-support-en
Package language-support-en has broken dep on openoffice.org-l10n-en-gb
  Considering openoffice.org-l10n-en-gb 10004 as a solution to language-support-en 10004
Package language-support-en has broken dep on openoffice.org-l10n-en-za
  Considering openoffice.org-l10n-en-za 10004 as a solution to language-support-en 10004
Done
```

any help appreciated.

---

### Post by compubahn on 2007-09-28
I had a similar problem with that update / partial-upgrade today which made update-manager pretty unhappy.

I fixed it by going to synaptic package manager & searching for "openoffice.org" then choosing upgrade for the main package called "openoffice.org". This upgraded all of the dependent packages & all is well again.

GL

---

### Post by n3tfury on 2007-09-28
you, my friend, deserve huge props.  thank you so much, that worked perfectly!

---

