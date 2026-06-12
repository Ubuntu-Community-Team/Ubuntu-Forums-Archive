---
title: "how to combine multiple CSVs into one xls workbook as separate tabs command line"
date: 2015-02-04
forum: General Help
---

### Post by N00b-un-2 on 2015-02-04
I figure I'll ask the question here, even though it's probably better suited for a site like superuser or VMUG.

Specifically here is what I'm doing.  I administer a few thousand virtual machines spread out over a total of 8 ESXi hosts (clusters).  I need to generate some reports weekly which is a very tedious process that I'm trying to automate.  I've got it now (with the assistance of some bash scripts I wrote using cygwin) to where it generates the reports for each server split up into 7 separate CSV files.
What I need to accomplish now is to somehow batch convert those separate csv files into one Excel workbook, each CSV being a separate tab within the excel workbook.  And I need it to be something I can automate, ie; via command line.

---

### Post by steeldriver on 2015-02-04
The ssconvert utility (part of the gnumeric package) appears to support that

```

ssconvert --merge-to=all.xls 1.csv 2.csv ...

```

```

DESCRIPTION
       ssconvert  is  a  command  line  utility  to  convert spreadsheet files
       between various spreadsheet file formats. It is a companion utility  to
       Gnumeric,  the  powerful  spreadsheet  program  created  by  the  GNOME
       project.

```

LibreOffice certainly has batch convert capability as well, but I don't know if that includes merging sheets

---

### Post by N00b-un-2 on 2015-02-05
thanks.  unfortunately for me, this is on cygwin.  I'm a Mac/Linux guy but my new position requires me to use Microsoft.  I think I already made some of my coworkers paranoid when I told them that I wrote a BASH script to do something on Windows, one of them even demanded that I convert it over to Powershell.  It looks like GNUmeric used to be developed for Windows but they took down all the builds.  But maybe I can find an old copy somewhere.  Thanks, I will do some digging and see what I come up with.

---

### Post by raptir on 2015-02-05
If you're on Windows, Excel has a *Consolidation Wizard* that would do this, but it's not from the command line.

---

### Post by steeldriver on 2015-02-05
Here perhaps?

[http://sourceforge.net/projects/gnumeric.mirror/](http://sourceforge.net/projects/gnumeric.mirror/)

It appears to include an ssconvert.exe binary. 

Although TBH if you're working in a Windows shop and that's what your colleagues are familiar with, then I'd probably be looking at writing some kind of VBA macro if I were in your position.

---

### Post by N00b-un-2 on 2015-02-05
YOU ARE A GENIUS!!!!  I had to dig a bit to find a Win32 build of Gnumeric but I found one and I'm happy to report that now with the help of one .bat file, 5 .sh scripts, a couple Linux binaries on Cygwin and of course ssconvert as part of gnumeric, everything works.  Now if only I could convince my boss to let me set up a linux VM for this, I could get rid of the Windows bits and set this whole thing to run as a cron job every week.  Oh well, I guess for now having to double click a script is going to have to suffice.

---

### Post by N00b-un-2 on 2015-02-05
you are probably right about needing to make a VBA macro at some point.  But as for right now, it gets the job done and it automates a process that used to take a technician a couple hours to do manually.  I have no experience with VB or powershell, so right now I'm just interested in getting the work done.  I'll worry about my Microsoft brainwashed colleagues being able to understand my scripting later.  They don't need to know HOW it works, they just need to know THAT it works.

---

