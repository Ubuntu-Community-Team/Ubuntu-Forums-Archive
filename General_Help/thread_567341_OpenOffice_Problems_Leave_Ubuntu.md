---
title: "OpenOffice Problems: Leave Ubuntu?"
date: 2007-10-04
forum: General Help
---

### Post by IronArjen on 2007-10-04
I keep on having problems with OpenOffice. Lets start with the main ones

1 Crash upon  copy paste. I work with fairly large files, like a calc with 10.000 rows and 12 columns.
2 The filter function in Calc does not work properly. I use this function a lot and  due to the large datasets I can not see exactly what I am doing but what I do know for sure is that filtering does result in the complete loss of certain data and in the duplication of certain other  data.
3 The custom filter does not sort properly: it combines ascending with the custom filter
(hence: I make a custom filter consisting of grouped data, groups indicated by a number, data indicated by a code.  Sorting by this custom filter results in a list with first the numbers, then the data. It should be 1, data from group 1, 2 , date from group 2 etc.

The OOo forum tells me that Ubuntu uses/has a slightly different setup as that is provided by OOo whihc means that sometimes it is better, sometimes it is worse. Apparently I also get the last part. Looking at the amount of threads about OpenOffice crash, and seeing that most have not been solved, I am getting a bit scared. Will OOo ever work properly in Ubuntu?

---

### Post by bigb_thedestroyer on 2007-10-04
I use Writer almost exclusively, not Calc, but have not had any problems.  You good try the Gnome office or KDE office as a short term solution, until OOo 2.3.

---

### Post by hardyn on 2007-10-04
I really really dislike calc... it is the weakest link in the OOo suite... i find i like Gnumeric alot better.

it DOES trendline w/ forumulas.
seems to play better with excel.
really light weight.
really quite intuative.

---

### Post by IronArjen on 2007-10-04
seems like a good idea

The first improvement is that gumeric eats tabbed txt files! Hail!

---

### Post by darknuala on 2007-10-04
You could test drive IBM's Symphony [http://symphony.lotus.com/software/lotus/symphony/home.jspa](http://symphony.lotus.com/software/lotus/symphony/home.jspa)

---

### Post by strabes on 2007-10-04
OO.o 2.3 comes with gutsy.

---

### Post by trippinnik on 2007-10-05
Since you are also worried about the modifications that Ubuntu team makes to openoffice you could try building from the official source.  Also the other options mentioned above look pretty good.  I think you could also help make them better by submitting a bug report to launchpad as well.

---

### Post by swisscow on 2007-10-05
I used these instructions to make debs for open office as I too found the Ubuntu version lacking. This was for openoffice2.2 but should work for 2.3

    * Cleaned out open office through Synaptic
    * Installed alien through synaptic
    * Download the tarball from the open office web site to the desktop and extracted it
    * Renamed the extracted folder to something easier, like office
    * Then in terminal:


```
cd Desktop
cd office (or whatever you called the extracted folder)
cd RPMS
sudo alien --scripts --keep-version *.rpm
sudo dpkg -i *.deb
cd desktop-integration
sudo dpkg -i *.deb
```

It takes a little time for Alien to convert the rpms to debs so be patient

---

### Post by kidcharles on 2007-10-06
There is a .deb package available for 2.3 from openoffice.org.

There is a thread about installing it and some other issues here:
[http://ubuntuforums.org/showthread.php?t=553410](http://ubuntuforums.org/showthread.php?t=553410)

---

### Post by swisscow on 2007-10-06
Didn't know that - great news.

---

### Post by IronArjen on 2007-10-09
I will wait for OOo2.3 for Gusty, meanwhile I am rather happy with gnumeric although it does not sort to a preformed set, It has problems deleting from a filtered set (it does not ignore the cells that are filtered) the same for copy paste of a filtered set and, and that actually induced a small curse: it crashed during autosave!! Luckily I had it set to ten minutes!

---

### Post by p_quarles on 2007-10-09
You might also give the Koffice suite a try. It's my personal favorite, but of course it doesn't suit everyone. "kspread" if you want just the spreadsheet, and "koffice" if you want to try the whole suite. 

It's a KDE app, but runs fine under other environments (and loads faster than OOo).

---

### Post by Phearicle on 2007-10-10
yea. Koffice is awesome.

---

