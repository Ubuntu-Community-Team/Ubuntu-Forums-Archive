---
title: "kmymoney"
date: 2007-03-12
forum: General Help
---

### Post by captgadget on 2007-03-12
I exported my Money account to a QIF file. Then when I went to import into kmymoney it couldn't interept the date because Microsoft put in an apostrophe instead of a slash. Is this typical or did I do something wrong?

---

### Post by ajgreeny on 2007-03-12
No, I suspect not.  I think the import filters from qif to kmymoney are a bit suspect.  My bank will allow downloads as Quicken files (qif) but I have never got them to load into kmymoney, even after trying all the different date formats that are suggested, etc etc.  I have tried everything I can think of but so far no luck.  In fact it makes very little difference to me as I was just trying the system out to see if I could download backdated statements in arrears to save entering it manually - I didn't really need the information but was simply interested.

Apart from that I think kmymoney is terrific.  It lets me keep up to date with my bank accounts and tracks all my direct debits and standing orders automatically, so I can make sure that I don't get caught short without cash in the bank.

---

### Post by captgadget on 2007-03-12
Thanks, I will be using it for many of the same reasons you are. Thanks again.

---

### Post by Marsolin on 2007-03-12
I've never actually tried to look at a QIF file. Is it just a text file when you try to read it? If so you could always see if a find and replace for the apostrophe fixes the problem.

---

### Post by jcconnor on 2007-03-18
This comes from the kMyMoney web site:

> The QIF specification does not specify a definite format for dates. Several different formats are used and the format is selected by the source of your QIF file (e.g. your bank). In order to cope with many different date formats, KMyMoney provides 'QIF profiles'. Each profile allows to customize KMyMoney to accept the input data format chosen by the originator of the QIF file.

With respect to dates, KMyMoney supports m/d/y as well as d/m/y formats. 2 digit year info as well as 4 digit year info is also supported. For 2 digit year info some institutions use an apostrophe to identify a certain range of years. Within the date tab of the QIF profile editor you can also select the behaviour of KMyMoney in case of such an apostrophe.
Date Format 	Meaning
%yy 	identifies two digit year info
%yyyy 	identifies four digit year info
%m 	identifies a numeric month (1-12)
%mmm 	identifies a short month name (e.g. Jan, Feb)
%d 	identifies a numeric day (1-31)

Example: If you see a date of 21/3'03 in your records, select the '%d/%m/%yy' setting. It does not matter if you have a / or an ' preceeding the years. Therfore, '%d/%m%yy' would be the wrong format. If your bank sends you this file for the year 2003 then you probably want to set the apostrophe handling to '2000-2099'. Then the above record would be interpreted to carry the '21st of March 2003' as it's date.

If you picked the wrong date format in the QIF profile, KMyMoney cannot correctly interpret the data and shows error messages. The default in this case is to use today's date.

Hope that helps.

---

