---
title: "re-writing http://dl.google.com/linux/chrome"
date: 2016-03-05
forum: General Help
---

### Post by Bashing-om on 2016-03-05
So not OK,

Google has dropped support for 32 bit operating system requiring a change to the sources list file .
OK .. no problem to edit the source to:
> 
 deb [arch=amd64] [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable main

Adding the field " [arch=amd64] " . Update/upgrade goes through then fine good and dandy .
However, when I re-boot that source is reverted to the file as prior to the edit(s) !
The edited sources list:
```

03Mar2016 : /etc/apt/sources.list.d/google-chrome.list ;
deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main
##03Mar2016 field "[arch=amd64]" added as Google dropped 32bit support causing 
##W: Failed to fetch http://dl.google.com/linux/chrome/deb/dists/stable/Release

```

is once more as:
```

### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb http://dl.google.com/linux/chrome/deb/ stable main
sysop@1404mini:~$

```

Running the xfce4 DE in 14.04.4.

HUH ??
My question is what process is writing that old invalid source list back in place ?
Do I need to update google's singing key, and if so what is that process ?

[INDENT]one of those times
[INDENT][INDENT][INDENT]I just do not know
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Bashing-om on 2016-03-05
Hey, hey !!

I got it I got it !

In the file " /opt/google/chrome/cron/google-chrome " ;
the script also generates the .list file.

add that new field " [arch=amd64] "  in the 2 referenced places in the script ( search for http: ) .

[INDENT][INDENT]workie great now
[INDENT][INDENT]last long time
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by QIII on 2016-03-05
I just uninstalled it, removed it from sources and then went to Google.com to download and install the new version.  It added the clean repo, so no more problems.

---

### Post by Bashing-om on 2016-03-05
Hey QIII ;  :)

That too is good to know info ... Goggle is getting up to speed ( sure wish we had prior warning this was going to happen ).

[INDENT][INDENT]The more I know
[INDENT][INDENT][INDENT]the more I realize
[INDENT][INDENT][INDENT]how little I do know
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

