---
title: "Canon printer using wrong black ink on glossy paper."
date: 2012-10-20
forum: General Help
---

### Post by 2CV67 on 2012-10-20
I have a Canon iP4300 printer with 2 black ink cartridges.
I believe there is a dye black for glossy media & a pigment black for plain paper?

Results using the Canon driver in XP have always been OK.

In Ubuntu 12.04 results are generally not so good, using either Gutenprint driver or Canon driver via Michael Gruz's download site (mentioned here:  [http://ubuntuforums.org/showpost.php?p=11704448&postcount=5](http://ubuntuforums.org/showpost.php?p=11704448&postcount=5)), but adequate for non-photo printing.

I just tried photo printing with M. Gruz's driver & it seems that the printer is using the pigment black ink even though glossy photo paper is specified.

Any ideas how to fix this?

Thanks!

---

### Post by 2CV67 on 2012-11-27
Bump...

Anybody at least confirm (or otherwise) my observation?

---

### Post by pdc on 2012-11-27
peut-etre, si vous nous donnez 

> [COLOR="Red"]sudo dpkg -l | grep cnijfilter[/COLOR]

...... we can see which printer drivers you have installed ......

if you copy and paste in and out .............

__________________________________________________________________________

from here

[http://support-asia.canon-asia.com/P/search?model=PIXMA+iP4300&menu=download&filter=0&tagname=g_os&g_os=Linux](http://support-asia.canon-asia.com/P/search?model=PIXMA+iP4300&menu=download&filter=0&tagname=g_os&g_os=Linux)

Canon supplied rpm packages when your printer was first released 5 yrs ago; 

so Michael must have used to alien to convert rpm and create a deb package

......if you are really keen to have excellent control over every aspect of your printer, can I recommend turboprint

[http://www.zedonet.com/en_p_turboprint_driver.phtml?printer=Canon_PIXMA_iP4300](http://www.zedonet.com/en_p_turboprint_driver.phtml?printer=Canon_PIXMA_iP4300)

download from here

[http://www.turboprint.info/download.html](http://www.turboprint.info/download.html)

these folks have been supporting printers since the 1980s: they started with drivers for the Commodore Amiga

---

### Post by 2CV67 on 2012-11-27
> **pdc said:**
> 

...... we can see which printer drivers you have installed ......

if you copy and paste in and out .............

```
ii  cnijfilter-common                      3.50-2ubuntu4                           IJ Printer Driver for Linux.
ii  cnijfilter-ip4300series                2.70-3ubuntu4                           IJ Printer Driver for Linux.

```
> 
Canon supplied rpm packages when your printer was first released 5 yrs ago; 

Yes, I have been using various Canon packages for years, with more or less difficulty. For example:
[http://ubuntuforums.org/showthread.php?t=1912988](http://ubuntuforums.org/showthread.php?t=1912988)
[http://ubuntuforums.org/showthread.php?t=1869131](http://ubuntuforums.org/showthread.php?t=1869131)
[http://ubuntuforums.org/showthread.php?t=892340](http://ubuntuforums.org/showthread.php?t=892340)

> ......if you are really keen to have excellent control over every aspect of your printer, can I recommend turboprint

Yes, I have tried TurboPrint but it seems un-Linux-like to pay for it!
If all else fails...

Thanks very much for your input!

---

### Post by pdc on 2012-11-27
>  it seems un-Linux-like to pay for it!

linux is said to be free ........... libre .......as in speech .....

NOT as in ........free beer...... ou peut-etre, en Alsace, ..vin libre ..!!

.....everyone has to be able to put food on the table .......

......liberty (freedom) in linux comes from the GNU ....... freedom to use and change ..............

vive la liberte !

---

### Post by 2CV67 on 2012-12-20
I can now confirm that TurboPrint does use the right black ink for photo printing.

So why not the Canon driver?

---

### Post by pdc on 2012-12-20
parce que ...........turboprint is like the French ....

........does everything better than others .........  ;)

---

