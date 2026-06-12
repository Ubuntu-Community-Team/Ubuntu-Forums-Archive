---
title: "sort by date (reversed) when selecting files from inside an application like firefox"
date: 2012-12-11
forum: General Help
---

### Post by webdesigncompanyla on 2012-12-11
How do you sort by date (reversed) when selecting files from inside an application like Firefox?

Currently when I open the file manager it opens sorted by date, but when I go to select a file while inside an application like Firefox, for example to upload a picture, then it doesn't use the same sorting rules as I've assigned in the file manager.

How can I get a universal sort rule to sort by date reversed to show the most recently modified files first, even when selecting a file from inside an application like Firefox?

---

### Post by Vaphell on 2012-12-11
i set the file dialog (i used the one that uploads images in these forums in advanced mode) to be sorted by date by clicking the column header and my ff seems to remember the setting after the restart.

---

### Post by webdesigncompanyla on 2012-12-14
> **Vaphell said:**
> i set the file dialog (i used the one that uploads images in these forums in advanced mode) to be sorted by date by clicking the column header and my ff seems to remember the setting after the restart.


i have ubuntu 12.04 and i'm using gnome 3 and none of the applications remember the sorting rules, i have to click twice to get the file to sort to last used (sort by date/reversed) every time i get a file... it's a pain.

you didn't mention HOW you managed to do this, where did you click, which settings did you change and WHERE exactly?

---

### Post by Vaphell on 2012-12-14
i clicked the column header in the file selection window.

i did some tests in virtualbox (quantal) on gedit, geany, firefox and libreoffice calc - my main is 10.04 so it has not much in common with recent unity based ubuntus.

there apear to be 2 or 3 different file selection windows, most likely dependent on the gui framework used to write the program?
- libreoffice and geany seem to use the exact same window and settings stick
- gedit has its own, its settings seem to stick too
- firefox has its own, sticks

no idea if the settings are session based or are permanent. There is also difference when on the left panel you click recent files/directories. Recent files default to sorting by time.

---

