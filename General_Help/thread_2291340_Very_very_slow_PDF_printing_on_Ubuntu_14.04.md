---
title: "Very very slow PDF printing on Ubuntu 14.04"
date: 2015-08-19
forum: General Help
---

### Post by mrbou on 2015-08-19
Hi,

I try to use Ubuntu 14.04.3 (Trusty Tahr) in a company environment. (i personally use linux from more than 15 years).
 I have a big  problem when i try to **print PDF files (text / images)** **or direct from presentation program** like Libreoffice Impress. **It is very very slow...** 
It is on a network printer (Kyocera, Brother, ...), and the network is not the problem. Drivers are PPD Postscript.


  For a file less than 5 Mb.. it take **more than five minutes to print eight pages**. It is unusable!
It can take until 15 minutes to print some documents with 20 pages. :-(

Text documents is fast and have not problem.


  I tried Adobe Reader, Evince, qpdfview, and Okular. Now i choosed qpdfview.


  I googled many things, but I didn't find the solution. Apparently this problem **exist from many years** and i'm surprise that is not resolved!
I found also this old thread on this forum that is similar to my problem.

Any suggestion ? Test ?


Thanks for your help!
Michael

---

### Post by HermanAB on 2015-08-19
Well, a PDF is already formatted for printing so you can just send it straight to the printer with lpr.

[http://www.aeronetworks.ca/search?q=lpr](http://www.aeronetworks.ca/search?q=lpr)

---

### Post by mrbou on 2015-08-20
Thanks for your answer.

You mean with command line?? 

No way.. It is used by common people in a company that are not computer specialist (Open a pdf with Evince, qpdfview, Okular,... or a presentation with Libreoffice... and just select the printer and print). 
Must work without command line.

PDF is converted to postscript (pdftops) each time by CUPS and after sent to the printer.

Printer have many options, mailbox, hole, stapling, booklet, .. but is the same with a normal printer. 
Some PDF is too slow to print and unusable (we can't wait 10 min for 15 pages).
With Windows have no delay and printed directly.

I read in many forum that many people have the same problem. And i still not found i working solution..


What can i do?

---

### Post by mrbou on 2015-08-22
UP.. Another idea? Suggestion?

---

