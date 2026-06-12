---
title: "Capture data from web page ?"
date: 2013-09-10
forum: General Help
---

### Post by dlw1145 on 2013-09-10
There is a web page I need to extract streaming data from.
It is not video or music but numerical values.

I can do it with LibreCalc but only stagnant data, not live data.
The labels load but not the numerical data I need.
Example: Total...9999999, all I get is Total: no numerical data.
I would like to capture this data every half hour.

How can this be solved?

Thanks,
dlw

---

### Post by SeijiSensei on 2013-09-10
I would write a script in bash or PHP and run it from cron every half hour.

Unless the page contains only the data you need, you'll have to write some code to strip off any HTML cruft and just grab the data.  Are they in an HTML table?  Then you'd have to parse the <tr><td> structures as well.

---

### Post by mörgæs on 2013-09-10
Also worth trying wget.

---

### Post by tgalati4 on 2013-09-10
Or *curl*, but if the data is from a javascript calculator, you might have a difficult time scraping it because that process is jailed to prevent grabing of data for security purposes.  If you print-to-file, then you have a PDF that you can scrape.  So now  you need to figure out how to send a print every half hour to /tmp and use your script to scrape the latest PDF file.

If this is a public website, then there may be API's that you can use to get the same data.  If it is bank account data (where you have to log in through a secure process) then you will have some difficulty.

---

