---
title: "[SOLVED] Printer Problem PSC 1310"
date: 2008-02-16
forum: General Help
---

### Post by troy1of2 on 2008-02-16
I have an HP PSC 1310 which I have used for a few years now. I don't print very often but whenever I have needed to in the past it has worked just fine with my Dell Inspiron E1505 running Ubuntu 7.10 until recently. I'm not sure but I think the problem might be related to GutenPrint which I think got installed with an update of Gimp a few months back. But here is what happens. Whenever I try to print something, be it in Firefox, Open Office, Gimp or anything else the printer goes through the usual motions as if it were printing something, the head moves back in forth in the usual jerky fashion it would if it were actually prinitng but a blank page comes out.

**Now before you say it. IT'S NOT THE INK CARTRIDGE!**

If I go to System>Administration>Printing and Print a Test Page the test page prints perfectly without a hitch. But that's the only thing I seem able to print without getting a blank page. Now, the reason I suspect GutenPrint might be involved is I went into the setup for GutenPrint and there is no setting for the PSC 1310. The list of HP printers goes from PSC 950xi then skips all the way down to PSC 2110 with nothing in between. So if all of these programs are using GutenPrint (which I don't know for sure if they are) then maybe that is why things aren't working. I tried some of the other printer models on the list but to no avail. So, should I try removing GutenPrint? Should I reinstall the HP drivers? Any thoughts?

Thanks!

---

### Post by linuxwizard on 2008-02-16
According to this page the gutenprint does not support your printer, not listed.
[http://openprinting.org/show_driver.cgi?driver=gutenprint](http://openprinting.org/show_driver.cgi?driver=gutenprint)

Here is your printer Recommended driver bottom of page.
[http://www.openprinting.org/show_printer.cgi?recnum=HP-PSC_1310](http://www.openprinting.org/show_printer.cgi?recnum=HP-PSC_1310)

---

### Post by troy1of2 on 2008-02-17
That's what I thought. Well, here is my next problem. 

When I go into Synaptic and tell it to remove GutenPrint so I can go back to using the good old reliable printer driver I was using before (The one in the link you posted)  it tells me the Ubuntu Desktop will be removed with it. 

Well, I don't want to remove the Ubuntu Desktop. That's happened to me before when I tried to remove a bad modem driver and I was left with only the command line interface. Is there someway of removing this GutenPrint (Which I don't recall asking for in the first place, like I said, I think it came bundled with a GIMP update) without hosing my system?

:(

---

### Post by linuxwizard on 2008-02-17
Why can't you just leave GutenPrint installed ? When you setup your printer again you know which driver you need just don't choose GutenPrint. I wouldn't think their would be problem, for sure you don't want to remove Ubuntu desktop.

---

### Post by kellemes on 2008-02-17
Well, I don't know the answer to your problem I'm afraid..
But I would at least try to reinstall the hp-drivers indeed, is it **cupsys-driver-gutenprint** that whas installed maybe? I have it installed too but my HP PSV 1610 uses hplip/hpijs (driver) without issues..

---

### Post by troy1of2 on 2008-02-18
Okay guys, well then, maybe the problem isn't GutenPrint after all then as I was thinking because according to System>Administration>Printing I am using the HP PSC 1310 Foomatic/hpijs as recommended yet I still have the same symptoms.

 I can print a test page and every single time the test page prints out perfectly but any time I try to print documents in Open Office, Web Pages in Firefox or Images in GIMP the printer acts like it is printing but only blank pages come out.

 I don't get this. Why would the test page print out perfectly every single time but everything else comes out looking like I am out of ink?

:confused::confused::confused::confused::confused:

---

### Post by troy1of2 on 2008-02-18
Okay, well here is another oddity to add to this puzzle. I just loaded up an image in gThumb image viewer and printed it and it actually printed. But once again I still only get blank pages when I try to print a document in GEdit or print from Firefox. What weirdness is this? There has to be a common thread somewhere between these programs but I can't figure out what it is. What does gThumb do differently that is allowing it to print normally while these other programs are printing blank pages?

BTW, back in the good old days before I "upgraded" GIMP I could print from it just fine. Since they moved to GutenPrint I have no way whatsoever to print from GIMP since it will only print using GutenPrint and GutenPrint does not support my printer. What kind of an upgrade is this? I need to revert back to an older version I guess.

Still, I would like to figure out why I can't print from most of my other programs.

:(

---

### Post by troy1of2 on 2008-02-18
Well, I'm not sure what exactly did it but I suspect it was installing this previously uninstalled package hpoj that made things start working again. Thanks for the feedback guys. Trying some of the suggestions helped me to think in different directions than I was and break out of the loop I was in.

---

