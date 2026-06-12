---
title: "Wine problem, please help"
date: 2007-01-17
forum: General Help
---

### Post by october1917 on 2007-01-17
When i try to run a CD which was autorun it doesn't start but Nautilus opens a window to view the contents. Then i double click AUTORUN.EXE and a small window notice me the above:
> Could not copy 'Z:\home\g1annis\AutoRun.exe' to 'C:\windows\temp\AutoRun.exe'

I click the OK which is the only i can do, and then another notification appears:
> There is no application associated with the given file name extention. This error will also be returned if you attempt to print a file that is not printable. And then again OK, and of course nothing happens.

What to do?

I run Ubuntu 6.10 i 've installed Wine via Automatix2 which makes automatic setup of Wine, and i run any compatible program (such as IsoBuster or others) with no problem.

Please help me.

---

### Post by hikaricore on 2007-01-17
I would suggest running the installer (?  i'm guessing you're trying to install something) from a terminal window for better error output results.  Also you should probably run the main program such as setup.exe rather than autorun.exe.

```
cd /media/cdrom
wine Setup.exe

```

This assumes your cdrom is mounted at /media/cdrom which may vary depending on your setup.

Also have you run the wine configuration tool yet?

```
winecfg
```

Should be run before attempting to use wine for the first time.  This will setup your ~/.wine directory and the fake drives & windows directory used by wine ~/.wine/drive_c/ & ~/.wine/drive_c/windows

good luck.

--Aaron

ps.  check to see if the software you're trying to run actually works before installing at the [wine application database]("http://appdb.winehq.org").

---

### Post by october1917 on 2007-01-17
Unfortunatelly, it seem not to be a wine problem:

I burned the iso to a CD and i tryied to run it on a laptop using WinXP. It does the same. But the strange is that i have tryied to install the PROGRAM with 2 different CDs downloaded from different sources, and both the CDs i burned do the same. After the autorun sreen i press Install and a very small window appears with one only button "OK".

So it seems not to be wine or linux problem or incompatibility. Could it be DirectX?
Do you have any idea?

---

