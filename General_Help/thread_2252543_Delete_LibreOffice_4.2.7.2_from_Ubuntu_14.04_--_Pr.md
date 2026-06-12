---
title: "Delete LibreOffice 4.2.7.2 from Ubuntu 14.04 -- Prevent Mangling Sorts"
date: 2014-11-12
forum: General Help
---

### Post by m-j-malone on 2014-11-12
Hello Community,

I am writing this in hopes that Canonical makes a change to all Ubuntu 14.04 installs (via updates) and any future versions that currently include LibreOffice 4.2.7.2.   I recommend they all be downgraded to a version of LibreOffice that does not irretrievably mangle years of work, for instance 4.1.6.2, possibly some later versions.   

The problem is with 4.2.7(.2?), LibreOffice changed the way SORT works, without warning the user in some way that is impossible to ignore, by for instance changing the name of the menu item from SORT to MANGLE.   I will try to explain the change made, but, without telling people, there are people right now (and me up until a few hours ago) mangling years-old spreadsheets when we thought we were sorting them.   When those people discover what has happened, the years of work that was lost, they will bail on LibreOffice and perhaps Ubuntu itself.  None of this will repair the years of work that has been mangled.  The change is so simple it is insidious and can go unnoticed for months, longer  than even some user's backup cycle.  It is possible by now, all  non-mangled versions of years-old spreadsheets have been over-written.  I emplore Canonical to do something to stop the process from continuing, and prevent new downloads of Ubuntu from starting to mangle spreadsheets by changing which version of LibreOffice is included by default with Ubuntu (14.04).   

What is happening?  It is in LibreOffice Calc 4.2.7.2 and possibly other versions.  It is the sorting of cells that contain references.  Here is the formula view and value (default) view of a spreadsheet:

          ...... A        ..... B                           ................A .........      B
1        ....10       ... =A1.......           1          ...10     ........ 10
2        ....9        .....=A2            ........2          ...9       .......... 9

In any proper spreadsheet, when one highlights A1 to B2 and asks for a sort by column B ascending, one gets:

          ...... A        ..... B                           .................A .........      B
1        ....9        ... =A1........ 1          ... 9     .......... 9
2        ....10 ...=A2            ....... 2          ... 10       ........ 10

That is exactly the result one would get if they cut and pasted entire rows to re-sort the sheet by hand.   What 4.2.7.2 is doing is this:

          ...... A        ..... B                           .................A .........      B
1        ....9        ... =A2........ 1          ... 9     .......... 10
2        ....10 ...=A1            ....... 2          ... 10       ......... 9

Which is quite obviously not keeping rows together (a founding premise of SORT IMHO) and the result is clearly not sorted with column B ascending which is what I asked for.   

There are a number of philosophical discussions going on:

[http://www.networkworld.com/article/2845000/opensource-subnet/libreoffice-defends-handling-of-spreadsheet-bug.html](http://www.networkworld.com/article/2845000/opensource-subnet/libreoffice-defends-handling-of-spreadsheet-bug.html)

[https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/1389858](https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/1389858)
[https://bugs.freedesktop.org/show_bug.cgi?id=81309](https://bugs.freedesktop.org/show_bug.cgi?id=81309)
[https://bugs.freedesktop.org/show_bug.cgi?id=81633](https://bugs.freedesktop.org/show_bug.cgi?id=81633)

The first clue that the current behaviour is incorrect and corrupting is that it was introduced as "Sorting should not always adjust references" -- Not always ?  Randomly maybe is better?  I want my spreadsheet to always do the same thing and I find a way to adapt.  The example given in the request to change the behaviour of references was a chronologically ordered bank statement with a running balance down the side.  They want the sort to work so that with poorly written formuli, and a poor choice of sort block, that the running balance remains proper down the side.  Do these people not know how to use a spreadsheet?    And to LibreOffice, I say, you do not change a behaviour that has existed for years in multiple programs without a huge warning about the potential to mangle historical spreadsheets.  

For users who like to stick to the long term releases, and have just stepped up from 12.04 to 14.04, or those just starting in Ubuntu or for those who Ubuntu is their first try at Linux if they discover a years-old spreadsheet has been irretrievably mangled, this is the type of bite that will drive them away from LibreOffice, Ubuntu, maybe even Linux.  This has to be fixed.  


This is how I ended the on-going damage to a years-old spreadsheets:

sudo apt-[COLOR=#0000ff]get[/COLOR] remove --purge libreoffice* libexttextcat-data* && sudo apt-[COLOR=#0000ff]get[/COLOR] autoremove

[FONT=arial]Then I found a link to LibreOffice 4.1.6.2 and downloaded it:[/FONT]

[http://downloadarchive.documentfoundation.org/libreoffice/old/4.1.6.2/deb/](http://downloadarchive.documentfoundation.org/libreoffice/old/4.1.6.2/deb/)

[FONT=arial]Went to my Downloads directory.
[/FONT]
tar -zxf LibreOffice_4.1.6.2_Linux_x86-64_deb.tar.gz
cd LibreOffice_4.1.6.2_Linux_x86-64_deb/DEBS
sudo dpkg -i *.deb

[FONT=arial]It will now take me weeks or months to undo the damage.   

It is my opinion that Canonical should do everything they can to avoid anything like this getting into
a long term support version of Ubuntu.  The people who install long-term support versions cannot
afford the time to be constantly upgrading versions.  They want something that simply works, not 
something broken at such a simple level.  [/FONT]  

[FONT=arial]Please Canonical, do something to prevent this from damaging someone else's work.  
Please do something to prevent those who are currently running 14.04 from mangling their 
work further.  Had I not noticed, it may have gone on for months longer.

Thank you for your time.[/FONT]

---

### Post by coffeecat on 2014-11-12
Although this is a valid subject for discussion here, this is a forum of mostly ordinary users, staff included. You will not catch Canonical's corporate ear here. The appropriate channels of communication are the bug reports - **not** philosophical discussions - that you have linked.

---

### Post by vasa1 on 2014-11-30
The Calc version (4.3.something) available to 14.10 users from the Software Center did not have this bug (or feature). The Calc version (4.2.7) available to 14.04 users from the Software Center still does. Pity.

---

### Post by vasa1 on 2014-12-01
> **m-j-malone said:**
> Hello Community,

I am writing this in hopes that Canonical makes a change to all Ubuntu 14.04 installs (via updates) and any future versions that currently include LibreOffice 4.2.7.2.   I recommend they all be downgraded to a version of LibreOffice that does not irretrievably mangle years of work, for instance 4.1.6.2, possibly some later versions.   

The problem is with 4.2.7(.2?), LibreOffice changed the way SORT works, without warning the user in some way that is impossible to ignore, by for instance changing the name of the menu item from SORT to MANGLE. ...
Those on 14.04 LTS may wish to download a more recent version of LibreOffice rather than an older version. I installed Version: 4.3.4.1 from libreoffice.org and now I don't have the sort problem. Of course, if you download the "direct" version, you'll be responsible for updating it as well. 

It's possible that 14.04 users may get an updated version of version 4.2 in the future but I need sorting to work *now*.

---

### Post by asorsher-m on 2014-12-12
About a week ago, I installed LibreOffice suite from repository and using Calc version 4.2.7, I noticed it was not sorting my selected cells correctly.  Upon closer inspection, the references to the selected cells were all scrambled.  In some cases the results were close, so the error was not immediately noticeable.  Apparently Libre office changed the way it handles referenced cells in a sorting process, but did not tell anyone!  This has been causing problems for almost 6 months.

  See attached bug:  
**Libreoffice calc 4.2.7-0ubuntu1 not updating references after sort**

[https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/1389858](https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/1389858)

They just put the fix in the repository today.  Using Synaptic I updated Libreoffice and now the spreadsheet sorts correctly.  Unfortunately, I wasted a few days trying to figure out what I was doing wrong, and had to manually re-do a lot of input now that the program is working [SIZE=3]([/SIZE][SIZE=3]4.2.7-0ubuntu2[/SIZE]).

---

### Post by bapoumba on 2014-12-13
Threads merged.

---

