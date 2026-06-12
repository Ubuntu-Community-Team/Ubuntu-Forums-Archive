---
title: "High CPU use and screen freeze"
date: 2016-10-23
forum: General Help
---

### Post by aviator1 on 2016-10-23
I just upgraded to 16.04, but this problem occasionally happened with 14.04

I have an 8 core CPU and 16 GB RAM with no swap. I have a SSD and generally RAM use is less than 3% even when the system locks up.

I seem to only be having the problem on a large spreadsheet. Same spreadsheet that I used on 14.04.

When using, but especially when saving the spreadsheet, the screen will go grey and the system will lock. 

I can open the system monitor and see that 1 of the cores is maxed out at 100% and the other 7 are very low. It will stay like this for a minute or so, then clear itself. Once in awhile, another core will take up the 100% and the first will drop to nothing. 

It seems to be a different core that maxes out each time.

Any ideas or suggestions?

---

### Post by aviator1 on 2016-10-24
This appears to only be happening with a LibreOffice spreadsheet.

Especially when I execute SAVE after changes.

It is a large spreadsheet, but I have used the same on in 12.04 with no problems and 14.04 with few problems.

I note also that under Settings-Displays that I get an error. "Could not get screen information" and that I have 2 printer icons in that area.

Could this be a graphics issue?

Thanks for any response.

---

### Post by aviator1 on 2016-10-30
A  little more info. The spread sheet is about 437 KB

Here are 3 screen shots from the system monitor over a 3 minute period of a lock up.


[ATTACH=CONFIG]271890[/ATTACH][ATTACH=CONFIG]271891[/ATTACH][ATTACH=CONFIG]271892[/ATTACH]

---

### Post by aviator1 on 2016-10-31
Update.

Another poster suggested to set the number of "undo" commands to a lesser amount.

However, in LibreOffice 5, the place to set hat is not located at Tools/Otions/LibreOffice/Memory

Does anyone know where this can be set?

Thanks

EDIT. Found the location....the changes did not help.

---

### Post by aviator1 on 2016-11-07
UPDATE:

I saved the spreadsheet to a thumb drive and tried it on  my wife's computer. Identical CPU and processors and RAM, but with  14.04.

The spreadsheet opened, closed, and saved after changes to both the desktop and thumb drive without hesitation.

I  did not that upon initiating save on her machine, that one of the cores  did go yo about 90%, but the save session was not hampered.

Any ideas as to why I get he lock up with 16.04?

Thanks for any help.

---

