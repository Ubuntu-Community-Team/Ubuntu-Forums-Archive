---
title: "openoffice 2.3 on kubuntu 7.10"
date: 2007-11-27
forum: General Help
---

### Post by abrazafi on 2007-11-27
Hi All,

I just finished installing kubuntu 7.10 on my machine.
Everything seems ok execpt for the OpenOffice 2.3
dictionary installation. I went through the menu (file/wizard/dictionary)
and the system keeps saying that it needs to recover my working
file. At the end the dictionary is not installed.

Any suggestion is welcomed.

Thanks,
Abdon.

---

### Post by kle on 2007-11-29
Please describe the steps you took to install OpenOffice. 
I have switched from Ubuntu to Kubuntu, because the Gnome kept crashing on me. However, while OpenOffice worked beautifully on Ubuntu, all I get on the Kubuntu is the OO splash screen, as described here: [https://wiki.ubuntu.com/GutsyGibbon/Tribe5/Kubuntu#head-29f59dd33bcff20a2089978206587ea863d2a764](https://wiki.ubuntu.com/GutsyGibbon/Tribe5/Kubuntu#head-29f59dd33bcff20a2089978206587ea863d2a764)

Cannot find out how to install the Gnome Open Office. 

As for language support: On Gnome I had to 
1) install the languages I want in the submenu called Languages 
2) for one of my languages, I additionally had to run the dictionary wizzard from OO menu file -> wizzard -> install dictionaries

Hope this will solve your problem

---

### Post by abrazafi on 2007-12-10
Yes, I am trying to install the dictionary (through the Wizard) and getting the following message:

"OpenOffice.org Document Recovery

Due too an unexpected error, OpenOffice.org crashed. All files you
were working on will now be saved ... "


It's happening on my 2 sytem based on kubuntu 7.10

Many thanks.
Abdon.

---

### Post by abrazafi on 2007-12-11
Everything is working fine now ...

I just needed to update my softwares using the command:
         sudo apt-get update
which changed the whole package of my OpenOffice ( ~ 60 Mb).
I'm back to business ...

Thanks,
Abdon.

---

