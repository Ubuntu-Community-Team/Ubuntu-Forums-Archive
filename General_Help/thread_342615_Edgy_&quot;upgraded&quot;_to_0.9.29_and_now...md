---
title: "Edgy &quot;upgraded&quot; to 0.9.29 and now.."
date: 2007-01-20
forum: General Help
---

### Post by maestrobwh1 on 2007-01-20
I used a program called WineTools and now, after today's Adept's suggested upgrade I get, "WineTools cannot run on versions older than 20050628..."  Isn't 0.9.29 a newer version?  I see in Dapper, the latest wine version is 0.9.9 so is that considered newer or older than 0.9.29?

WineTools is supposed to run up to 0.9.3 so I am so confused on the nomenclature of the 0.9 works.  The ones that start with "2" make sense to me because of the yyyy/mm/dd format.

EDIT: I just downgraded for now with 0.9.24, as the new upgrade had no positive impact on any win apps I run.  

I respect the Wine dev's position and their work is SO appreciated to get us fruther away from "that other OS" more easily; however, winecfg doesn't do certain things, such as kill wine processes when one of them freezes, show and uninstall "installed" software, etc.  WineTools also allows access to winecfg.  WineEXS did continue to work with 0.9.29, but there was a also a glitch with a program I like to run.  Newer isn't better sometimes:-)

If there is a way to kill wine processes from the command line, I probably could get by without WineTools.  There probably is...

---

### Post by rai4shu2 on 2007-01-20
I think the Wine devs would prefer if you used winecfg rather than winetools.

---

### Post by John Jones on 2007-01-21
I too use Winetools, although I'm aware that the Wine devs would prefer me to use Winecfg.
I do this because Winetools guides me through the configuration process relatively painlessly, whereas I don't have a clue how to use Winecfg to achieve the same end.

I know that there's lots of documentation available on the WineHQ site, and if there was a way of downloading it as a single document (maybe there is, but if there is, I don't know about it), so that I could print it out (I hate trying to read documents from a monitor screen; I much prefer reading from paper), I'd plough through it all to see if I could configure Wine manually. Winetools makes it easy, and I don't really see why anyone has a problem with using it.

Incidentally, I have the same problem with Wine 0.9.29

Cheers,

John :)

---

### Post by John Jones on 2007-01-21
Oops.

My last post prompted me to have another look at downloading the documentation in order to print it, and I find that it is possible to do so.

I'll have a go at configuring Wine without using Winetools, but I still think Winetools is probably easier.

John :oops:

---

### Post by machoo02 on 2007-01-22
> **maestrobwh1 said:**
> If there is a way to kill wine processes from the command line, I probably could get by without WineTools.  There probably is...

```
ps -aux
```Look for any processes that are associated with wine (names are listed in the last column) and look at the process id (pid = second column), then ```
sudo kill pid
```replacing pid with the number of the process you want to kill.

The version numbers in wine work in an incremental fashion, so 0.9.29 is a newer release than 0.9.3 (since 29 > 3)

---

