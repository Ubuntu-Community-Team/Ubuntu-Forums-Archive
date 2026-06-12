---
title: "Scanner problems"
date: 2014-09-20
forum: General Help
---

### Post by moon2 on 2014-09-20
Good evening :KS

I have a Epson 3490 photo scanner, I had been using XSane to enable me to use the scanner, it stopped working and I found the disc that came with the scanner, so installed that but nothing seems to work.

a) How do I uninstall what I installed with the disk
b) what can I do to make the scanner work.

I am new to Ubuntu and not techy, so really basic instructions would be most helpful

Thanks
Moon

---

### Post by sammiev on 2014-09-20
Epson drivers [here]("http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX").

Just add 3490 to the search and choose your drivers.

---

### Post by Paulgirardin on 2014-09-20
There is also Vuescan.I have not used it but it is worth a try.

[http://www.hamrick.com/vuescan/brother_mfc_3220c.html](http://www.hamrick.com/vuescan/brother_mfc_3220c.html)

---

### Post by sammiev on 2014-09-20
> **Paulgirardin said:**
> There is also Vuescan.I have not used it but it is worth a try.

[http://www.hamrick.com/vuescan/brother_mfc_3220c.html](http://www.hamrick.com/vuescan/brother_mfc_3220c.html)

That is for a brother printer. :confused:

For the OP, do not try this method.

---

### Post by rbmorse on 2014-09-20
Here's a better link for VueScan:

[http://www.hamrick.com/vuescan/epson_perfection_3490.html](http://www.hamrick.com/vuescan/epson_perfection_3490.html)

---

### Post by pqwoerituytrueiwoq on 2014-09-20
without knowing what is on that disk removing it will be hard
insert the cd and open it in folder view
then open a terminal
and run this
```
sudo apt-get install tree -y && tree /media
```
and post the output here and useing the 'code' feature (like i did above)

if just the UI for xsane is broke, try simple scan and/or the link in my signature

what does this give you?
```
scanimage -L
```
if it does not list your scanner in there
run ```
lsusb
``` if this does not show your scanner, you need to check your cables connected the scanner and the pc
if hte 1st command finds the scanner your UI is just broken and you cna use simple scan or the link in my signature

---

