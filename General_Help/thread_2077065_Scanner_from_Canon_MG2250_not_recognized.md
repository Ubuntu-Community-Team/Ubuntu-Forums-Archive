---
title: "Scanner from Canon MG2250 not recognized"
date: 2012-10-27
forum: General Help
---

### Post by Paul15071992 on 2012-10-27
Hei there guys,

I've got a litle problem with my multifunctional Canon MG2250. The problem is that the scanner isn't recognized. Printing works fine.
What do you think that i should do?

thank you!

---

### Post by pdc on 2012-10-27
yes, Canon have released this new MG series; so it is 2250 as opposed to the visually identical 2150 series; and no linux drivers yet;

..I just wonder if ScanGear for 2150 would work for your 2250?

[http://www.canon.co.uk/Support/Consumer_Products/products/Fax__Multifunctionals/InkJet/PIXMA_MG_series/PIXMA_MG2150.aspx?DLtcmuri=tcm:14-875791&page=1&type=download](http://www.canon.co.uk/Support/Consumer_Products/products/Fax__Multifunctionals/InkJet/PIXMA_MG_series/PIXMA_MG2150.aspx?DLtcmuri=tcm:14-875791&page=1&type=download)

it comes down as a debian package

MG2100 series ScanGear MP Ver. 1.80 for Linux (debian Packagearchive)

I emailed Canon Asia a week ago asking if they would release linux drivers; no answer so far

---

### Post by Paul15071992 on 2012-11-02
Thanks for the advice. I tried, but without results. 
I wrote a email to Canon Austria to ask them about the driver and they mailed me back and toled me I should ask the Ubuntu Support.

---

### Post by zanox on 2013-05-12
Hi! Did you resolve the issue?

---

### Post by zanox on 2013-05-12
ok I found that it is recognised by sane, and that I have not to use xsane but its proprietary application scangearmp that is not shown in the main application menu

---

### Post by pdc on 2013-05-12
If you want to use the scanner function, you can get scangear from here

[http://support-asia.canon-asia.com/contents/ASIA/EN/0100469701.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100469701.html)

it comes in as the [COLOR="#008000"]scangearmp-mg2200series-2.00-1-deb.tar.gz[/COLOR]

the commands; that you can paste into a terminal; to install; should be

> [COLOR="#FF0000"]cd Downloads[/COLOR]

> [COLOR="#FF0000"]tar -zxvf scangearmp-mg2200series-2.00-1-deb.tar.gz[/COLOR]

> [COLOR="#FF0000"]cd scangearmp-mg2200series-2.00-1-deb[/COLOR]

> [COLOR="#FF0000"]sudo ./install.sh[/COLOR]

then to run it 

> [COLOR="#FF0000"]scangearmp[/COLOR]

and for simplicity, best to create a launcher ........google on how to do that

---

### Post by josef-klotzner on 2014-02-23
the download contains 2 debian packages, which simply can also be installed by double click (but running the install.sh script is much faster and you don't need to know if select 32 or 64 bit  :D  :
[http://www.canon.co.uk/Support/Consumer_Products/products/Fax__Multifunctionals/InkJet/PIXMA_MG_series/PIXMA_MG2250.aspx?type=download&page=1](http://www.canon.co.uk/Support/Consumer_Products/products/Fax__Multifunctionals/InkJet/PIXMA_MG_series/PIXMA_MG2250.aspx?type=download&page=1)

---

### Post by Topsiho on 2014-02-23
Paul15071992 wrote: "I wrote a email to Canon Austria to ask them about the driver and they mailed me back and toled me I should ask the Ubuntu Support."

Thanks for this information. A shameless answer this. No Canon for me :)

Topsiho

---

