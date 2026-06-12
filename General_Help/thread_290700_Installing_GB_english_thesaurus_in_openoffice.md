---
title: "Installing GB english thesaurus in openoffice"
date: 2006-11-01
forum: General Help
---

### Post by spd106 on 2006-11-01
I was annoyed by the use of a us english thesaurus in open office, so I installed the british english thesaurus available from sourceforge [http://brit-thesaurus.sourceforge.net/](http://brit-thesaurus.sourceforge.net/)

You can follow the instructions (with slight modification) that are found in the install file included in the zip download. 

Note that since Ubuntu is Debian based the .dat and .idx files go in the /usr/share/myspell/dicts folder. You also need to edit the /usr/share/myspell/dicts/dictionary.lst file by changing the line 
THES en GB th_en_US_v2 
to 
THES en GB th_en_GB_final

Then start open office, go to the tools -> options dialogue. Select language settings -> writing aids, to the right of the lanuage modules section click on edit and make sure the box next to openoffice.org new thesaurus is ticked.

That's it, now you can select alternate words with an s rather than a z.

If you want to do some more hacking or add custom words, have a read through this article for an introduction [http://software.newsforge.com/software/06/01/27/2022227.shtml?tid=93](http://software.newsforge.com/software/06/01/27/2022227.shtml?tid=93).

---

