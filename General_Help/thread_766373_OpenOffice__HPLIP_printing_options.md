---
title: "OpenOffice / HPLIP printing options"
date: 2008-04-25
forum: General Help
---

### Post by kneewax on 2008-04-25
Since moving fully to Ubuntu I have tried very hard not to post 'I used to be able to do xxxx in Windoze...' threads, but this one I need to air as I am stumped on how do a fairly simple task.

I am using the HPLIP software to print to my HP Photosmart 2575 PSC device. When I used Windows I used to use the standard HP driver for this machine inorder to print vital info for my Filofax organiser.  Our quarterly rota for example as well as using it for addresses etc.  I had set up a custom paper size in the printer properties for my blank filofax inserts and any document I wanted I could print to that paper size with the option 'fit to papersize' checked so that OpenOffice would reduce the document automatically to my custom size.


I just can't figure out how to do this using the HPLIP properties, or even if it is possible at all. In HPLIP I cannot seem to set a custom papersize.  Also There seems to be no option to fit to page even if I could.

Simply Reducing the page size in OpenOffice has too many formatting issues.

Any help gratefully appreciated

Kneewax

---

### Post by bollix47 on 2008-04-25
Can you check under Applications > Accessories > HP Device Manager to see if the Printer Settings has the setting you need to change?

I can say on mine (OJ5610) it does have the "Fit to Page" option on that tab.

---

### Post by kneewax on 2008-04-25
Thanks for that - I don't have a HP Device manager there although I found a setting for fit to page in System > Preferences > HPLIP Toolbox, so am getting nearer being able to do this.  However I am still unable to set a custom template up for the page size I need.

---

### Post by kneewax on 2009-02-23
<bump>

Since posting this I have been using Virtualbox and XP to perform this task as I still cannot come up with a suitable way of doing this with OOo and HPLIP.  

Can anyone shed any light on the potential for custom paper sizes in HPLIP or even an alternative way of printing (I am not sold on HPLIP!)

---

### Post by Auric_Falc0n on 2009-03-13
Here's how I got my DeskJet D1420 to print to my classic-size Franklin Planner:

Open the folder /etc/cups/ppd/
Open the ppd file for your printer (mine was "Deskjet_D1400_series.ppd") as administrator
Add the two sets of green lines to the file (after the black lines):
```
*FoomaticRIPOptionSetting PageSize=Letter: " -dDEVICEWIDTHPOINTS=612 -&&
dDEVICEHEIGHTPOINTS=792"
*End
[COLOR="Green"]*FoomaticRIPOptionSetting PageSize=Franklin: " -dDEVICEWIDTHPOINTS=396 -&&
dDEVICEHEIGHTPOINTS=612"
*End[/COLOR]
```
and
```
*PageSize Letter/Letter: "%% FoomaticRIPOptionSetting: PageSize=Letter"
[COLOR="Green"]*PageSize Franklin/Franklin: "%% FoomaticRIPOptionSetting: PageSize=Franklin"[/COLOR]
```
The points are 72 per inch - my franklin pages are 8.5" x 5.5"
These two lines of code add the page size to the printer and an entry in the page size drop-downs.
In OOo I use a customer page size for anything I want to print to my pages.

This has worked great for me so far and I am going to try it on a DeskJet AIO 5100 at work I print to.

Hope this helps-

Joe

---

