---
title: "LibreOffice Calc: 'Create' option on Pivot Tables unavailable"
date: 2016-04-19
forum: General Help
---

### Post by quiquednst on 2016-04-19
Months ago I installed LibreOffice 5 using [http://ppa.launchpad.net/libreoffice/ppa/ubuntu](http://ppa.launchpad.net/libreoffice/ppa/ubuntu) repo.
 Yesterday I realized that I couldn't create a new 'pivot' table on Calc. Neither on new spreadsheets nor old ones. But if the pivot table already exist I may refresh or delete it.
 The point is that clicking on Data &#8594; Pivot I only see two options: refresh and delete.
 I'm using xubuntu 14.04 up to date and LibreOffice 5.1.2.2.
 I have tested with LibreOffice 4 and LibreOffice 5.0 and it works fine.
Am I doing something wrong?
Any help?
Thanks in advance

---

### Post by vasa1 on 2016-04-19
Have you tried going to Insert > Pivot Table?

I see that in Version: 5.1.1.3.

At some point, quite a few menu items have been moved around. It takes some getting used to.

See the **Calc** section here: [https://design.blog.documentfoundation.org/2016/01/22/way-down-in-the-libreoffice-menus/](https://design.blog.documentfoundation.org/2016/01/22/way-down-in-the-libreoffice-menus/) for the thinking behind the rejig. From there:> In order to place related functions together in an appropriate position, **inserting a pivot table was moved from the Data menu to Insert, while pivot table management functions were left within the Data menu**. Splitting the functions of the pivot table over different places is controversial discussed in the design team. The advantage of an action based position at Insert is opposed by the drawback of not grouping related functions.

---

### Post by quiquednst on 2016-04-19
Touché!
Thanks a lot!

---

