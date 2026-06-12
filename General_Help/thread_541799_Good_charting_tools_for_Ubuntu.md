---
title: "Good charting tools for Ubuntu?"
date: 2007-09-03
forum: General Help
---

### Post by rawler on 2007-09-03
Today, I were looking for a decent tool to present some CSV data as a nice readable chart, and boy were I in for a surprise. I still haven't found a single tool that does what I need.

My current need are rather simple, I've got a generic CSV-file with raw data from a trouble-ticket system. I want to process the file using different transforms to produce some readable graphs. One of the things I need, is the ability to simply have the tool present the percentage of trouble-tickets related to different partners. (Identified by a simple integer id). In SQL this would be a simple
```
SELECT COUNT(*), netcode FROM issues GROUP BY netcode
```
I still haven't found a single charting tool that does this decently, but will now have to import my CSV through a relational database, and THEN to a charting tool just to get grouping functionality, which feel a bit overkill.

Other things I'd like to do in the future will be things like chart the average time to resolve tickets in various networks, and similar things.

Does someone know a more convenient way for me to achieve this than, say <SQL DATABASE> + <charting tool>

Regards
/ Ulrik

---

### Post by leonidas666 on 2007-11-02
I think the OpenOffice Calc DataPilot Function (known as PivotTable in Excel) should help you with this problem... that is, if you are still looking for a solution....

---

