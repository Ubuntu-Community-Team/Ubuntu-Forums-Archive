---
title: "MS Money compatible program"
date: 2008-01-26
forum: General Help
---

### Post by Macmania on 2008-01-26
Is there a program that anybody knows of that can import/open MS Money files? I am helping my friend migrate from Win XP and they have a lot of Money documents.

---

### Post by seventhc on 2008-01-26
I'm not sure how good it is as I don't use it but I think gnucash can read those docs.
```
$ sudo aptitude install gnucash
```there might be better programs but this is all I can think of for now, can't hurt to try it. :)

heres a link to their home page
[http://www.gnucash.org/](http://www.gnucash.org/)

---

### Post by Macmania on 2008-01-26
Cool, I'll give it a try

---

### Post by Alpinist on 2008-01-26
Havent tried them myself but have found 4 possible alternatives.

Gnucash - as mentioned
Grisbi
Kmymoney
Moneydance - commercial program

---

### Post by dbet on 2008-01-26
Gnucash is probably your best bet, as I have tried all of the others and keep coming back to gnucash.  And yes you can import your MS Money documents.  You must export your MS Money files as "Strict qif" files in order to import them into gnucash.

---

### Post by oygle on 2008-02-02
I have recently converted from M$ Money to [KMyMoney]("http://kmymoney2.sourceforge.net/index-home.html") , the importing of the QIF files was a breeze.

I did try the other programs mentioned, and found that KMyMoney was the one which could best replicate the M$ Money functionality.

---

### Post by jwillar on 2008-02-16
I found MoneyDance was the way to go for me.  All three will import msMoney files one way or another, but MD is the only one that will encrypt the data file, communicate directly w/ my Bank, credit card and BillPay.  GnuCash looks good and has good documentation but does not see the reason to encrypt it's data file.  jwillar

---

### Post by oygle on 2008-02-17
> **jwillar said:**
> MD is the only one that will encrypt the data file, communicate directly w/ my Bank, credit card and BillPay. 

1.  KMymoney [can encrypt the data fle]("http://kmymoney2.sourceforge.net/online-manual/details.settings.encryption.html")

2.  KMyMoney has an [OFX Importer plugin]("http://kmymoney2.sourceforge.net/online-manual/details.impexp.ofx.html") , which has "Web Connect" and "Direct Connect".

MD costs $$$, whilst KMyMoney is open source (free).  :)

---

