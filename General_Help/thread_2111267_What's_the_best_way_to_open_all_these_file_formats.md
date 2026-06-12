---
title: "What's the best way to open all these file formats?"
date: 2013-02-01
forum: General Help
---

### Post by Maheriano on 2013-02-01
Here is a list of plugins I need to be able to run on a client setup running Ubuntu and they absolutely need to run and look exactly the same way they did when created on Windows. I can't have a single line out of place anywhere. And yes, it has to run Linux, I'll look at using Windows only if I run into a time constraint.

- mpg / mpeg - VLC
- pps / ppsx / ppt
- lnk - shortcut file, not necessary
- wmv - VLC
- raw - gimp-ufraw, Bibble, rawstudio
- jpg / jpeg - built in image viewer
- doc - Libre Office
- exe - These are simply executables to run Flash files, they can be changed over to Linux executables.
- cxt (Adobe Director file) - ???
- pxf - Adobe Acrobat
- dxr (Shockwave file) - ???
- vob (DVD rip) - VLC

I've already created individual threads here to discuss the possibility of Libre Office or WINE displaying the Powerpoint slides correctly, those can be located here:
[http://ubuntuforums.org/showthread.php?t=2111252](http://ubuntuforums.org/showthread.php?t=2111252)
and
[http://ubuntuforums.org/showthread.php?t=2111250](http://ubuntuforums.org/showthread.php?t=2111250)

So besides Libre Office and WINE, are there any other alternatives to displaying Powerpoint files with absolutely no issues in rendering? What about the rest, am I pretty safe in displaying those without any issues in rendering there? Thanks.

---

### Post by raja.genupula on 2013-02-01
These are the best , choose you want [http://office-suites.venturebeat.com/d/p/Linux](http://office-suites.venturebeat.com/d/p/Linux)

Regarding shockwave player : [https://answers.launchpad.net/ubuntu/+question/65572](https://answers.launchpad.net/ubuntu/+question/65572)

---

### Post by Mark Phelps on 2013-02-01
> pps / ppsx / ppt

PowerPoint does not work well at all using Wine in Linux -- gets Silver rating (which is quite poor) at best.

So, if you need to rely on using PowerPoint on a daily basis, you really have no choice other than to use MS Office in MS Windows.
> 
doc - Libre Office

If you end up getting ".docx" files (MS Word XML format) then LibreOffice is not going to suffice.  Lots of threads have been posted about folks having trouble reading docx files and rendering them properly, and with MS Word having problems with docx files LiberOffice generates.

Once again, for these files the only real solution is using MS Office in MS Windows.

Your insistence on Linux looking and working just like MS Windows is heading down a road to disaster!  Linux is a free ALTERNATIVE to MS Windows, not a free VERSION of MS Windows.  The more you need Linux to emulate Windows, the more unhappy your experience is going to be in the long run.

---

### Post by Maheriano on 2013-02-01
I should have mentioned they will only be viewing slides and not editing anything. But I guess if they won't even display 100% then it doesn't matter.

---

### Post by dvdhudson33 on 2013-05-25
My teachers at college love handing out their lectures in PPSX.

Apart from some font-size problems, which I can live with, the main issue is that LibreOffice Impress will only open PPSX in Slideshow view, and won't allow any editing.  As you say, that might not be a big issue for you.  But if it is, the only workaround I've found is to:
[LIST=1]
[*] rename the PPSX file as a PPT file
[*]open a blank presentation in Impress
[*]import (Insert/File) the PPT.
[/LIST]

It does the job, although the clunky fonts are still there.  But it's better than nothing - how can I possibly cheat my way to a pass without good source materials?

---

### Post by HiImTye on 2013-05-25
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]
docx isn't a portable format, so it will look different even between Windows computers

---

