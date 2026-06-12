---
title: "d-color Olivetti MF22 Printer Drivers"
date: 2008-07-09
forum: General Help
---

### Post by tomehb on 2008-07-09
At work we have a d-color Olivetti MF22 Printer/PhotoCopier etc. However i cant seem to find any drivers for it? Only windows, anyone have any ideas? or shall i just give up?

Thanks

Tom

---

### Post by tomehb on 2008-10-29
We now have replaced it with a Olivetti d-Color MF250 .... Anyone found any drivers for this so you can print Colour?

Thanks

Tom..

---

### Post by Ekerim on 2008-12-03
Better late then never ? ;)

If you use CUPS then you can use the PPD-file included in the Windows driver. We had problems getting hold of even the Windows driver since it is not available from Olivetti's site so we contacted the support at the company who sold us the printer and they were able to get the drivers from Olivetti.

[COLOR="Red"]**There are however a problem with this driver, _it ONLY prints using duplex_ printing (ie. double-sided)**[/COLOR], at least we have been unable to solve this.

Once you have the Windows driver it is easy to get the PPD-file from it.

* Install mscompress (You will need msexpand) from source or from package if Ubuntu has one.
* Unpack driver .zip
* Look for a file named <filename>.pp_ in the driver directory
* Unpack <filename>.pp_ file using msexpand (It will end up being named <filename>.pp)
* Rename .pp file to d-Color_MF250.ppd
* Gzip the .ppd
* Copy the .ppd to /usr/share/cups/model/Olivetti (...or wherever Ubuntu keeps PPDs)

The resulting PPD will not pass *cupstestppd* but it will work anyway. If you are not comfortable with that, it is quite easy to fix all the problems.

---

### Post by Ekerim on 2008-12-04
Hi again

I'v had success rewriting a Konica Minolta Bizhub 350 PPD to support color and duplex printing on a Olivetti d-Color MF250. The reason for choosing this approach is that the d-Color MF250 basically IS a Konica Minolta printer, the PPD that came with the Windows driver confirms this and that the Bizhub PPD actually worked (mostly).

I have been in contact with their Swedish tech support team to try to find out under what license (if any) the PPD is distributed because there are no license references or texts in any of the files. I'm hoping it is Public Domain. My hopes are that they will agree with me so that I can maybe post the PPD and filter here or possibly later on get it approved for inclusion at openprinting.org if there are interest.

As it is now, the PPD is a hack...but at least everything I need to work is working correctly.
[LIST]
[*]Color printing.
[*]Duplex (both DuplexNoTumble and DuplexTumble) and Simplex printing.
[*]Multiple pages on each side.
[/LIST]

The PPD passes *cupstestppd* with a few warnings.

If I get permission, would an upload here be of interest or is there a better forum for this ?

---

### Post by rossouwap on 2010-02-08
Hi,

I'm finding myself hassling with an Olivetti d-Colour MF201, and would be VERY interested in you posting your working ppd file ;)

---

### Post by tomehb on 2010-02-08
I would also be interested in this :) but guessing you hit a dead end ? :)

---

### Post by rossouwap on 2010-02-08
I'm going to be testing functionality with some of the other linux Olivetti drivers I downloaded today in the morning. Maybe I can get one to work.

I'll let you know if I have any joy.

---

### Post by emyr42 on 2010-06-25
I have an Olivetti d-Copia 300MF which appears to be identical to the Kyocera KM-5050 except for the colour of some plastic panels.

I've installed their PPD, but no new paper sizes appear in the application print dialogs. A3 is definitely mentioned in the PPD, but doesn't show in the list.

Get the PPD using the resources finder on the KM-5050 product page: [http://usa.kyoceramita.com/americas/jsp/Kyocera/productdetails.jsp?pid=16088&cid=10568](http://usa.kyoceramita.com/americas/jsp/Kyocera/productdetails.jsp?pid=16088&cid=10568)

Edit: rebooted, and the sizes now appear in applications, but when I tried to print an A3 diagram, the copier printed half of it onto A4 then stopped.

I've also attached the PPD I got from Kyocera.

---

### Post by rossouwap on 2010-06-26
Brilliant - worked a treat.

Thanks

---

