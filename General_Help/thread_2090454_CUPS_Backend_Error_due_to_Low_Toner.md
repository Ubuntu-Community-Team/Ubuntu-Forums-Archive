---
title: "CUPS Backend Error due to Low Toner?"
date: 2012-12-02
forum: General Help
---

### Post by Martom on 2012-12-02
Hello all,

Starting today, halfway through a pdf print job, I am no longer able to print from Ubuntu. Since at about the same time, my printer started displaying a "low toner" message, I figure it might have something to do with it.

I have an old office printer, an HP Laserjet 4300, connected to my network. It works just fine, I was able to print the document I needed from Windows. When I try to print from Ubuntu, however, the print job remains pending indefinitely and my printer becomes disabled (i.e. in the list of printers, it gets the pause icon.) If I try to enable the printer, the print queue window just freezes up. A couple of times, the first page of the document was printed, but nothing beyond that.

The error log shows the following.

```

D [02/Dec/2012:14:31:03 +0100] [Job 449] Before copy_prolog - %%BeginDefaults
D [02/Dec/2012:14:31:03 +0100] [Job 449] STATE: +connecting-to-device
D [02/Dec/2012:14:31:03 +0100] [Job 449] Before copy_setup - %%BeginSetup
D [02/Dec/2012:14:31:03 +0100] [Job 449] STATE: -connecting-to-device
D [02/Dec/2012:14:31:03 +0100] [Job 449] STATE: -media-empty-error,media-jam-error,hplip.plugin-error,cover-open-error,toner-empty-error,other
D [02/Dec/2012:14:31:03 +0100] [Job 449] Before page loop - %%Page: 1 1
D [02/Dec/2012:14:31:03 +0100] [Job 449] Copying page 1...
D [02/Dec/2012:14:31:03 +0100] [Job 449] PAGE: 1 1
D [02/Dec/2012:14:31:03 +0100] [Job 449] pagew = 571.1, pagel = 817.6
D [02/Dec/2012:14:31:03 +0100] [Job 449] bboxx = 0, bboxy = 0, bboxw = 595, bboxl = 842
D [02/Dec/2012:14:31:03 +0100] [Job 449] PageLeft = 12.0, PageRight = 583.1
D [02/Dec/2012:14:31:03 +0100] [Job 449] PageTop = 829.7, PageBottom = 12.1
D [02/Dec/2012:14:31:03 +0100] [Job 449] PageWidth = 595.0, PageLength = 842.0
D [02/Dec/2012:14:31:03 +0100] [Job 449] Copying page 2...
D [02/Dec/2012:14:31:03 +0100] [Job 449] PAGE: 2 1
D [02/Dec/2012:14:31:03 +0100] [Job 449] pagew = 571.1, pagel = 817.6
D [02/Dec/2012:14:31:03 +0100] [Job 449] bboxx = 0, bboxy = 0, bboxw = 595, bboxl = 842
D [02/Dec/2012:14:31:03 +0100] [Job 449] PageLeft = 12.0, PageRight = 583.1
D [02/Dec/2012:14:31:03 +0100] [Job 449] PageTop = 829.7, PageBottom = 12.1
D [02/Dec/2012:14:31:03 +0100] [Job 449] PageWidth = 595.0, PageLength = 842.0
D [02/Dec/2012:14:31:03 +0100] [Job 449] Copying page 3...
D [02/Dec/2012:14:31:03 +0100] [Job 449] PAGE: 3 1
D [02/Dec/2012:14:31:03 +0100] [Job 449] pagew = 571.1, pagel = 817.6
D [02/Dec/2012:14:31:03 +0100] [Job 449] bboxx = 0, bboxy = 0, bboxw = 595, bboxl = 842
D [02/Dec/2012:14:31:03 +0100] [Job 449] PageLeft = 12.0, PageRight = 583.1
D [02/Dec/2012:14:31:03 +0100] [Job 449] PageTop = 829.7, PageBottom = 12.1
D [02/Dec/2012:14:31:03 +0100] [Job 449] PageWidth = 595.0, PageLength = 842.0
D [02/Dec/2012:14:31:03 +0100] [Job 449] prnt/backend/hp.c 625: ERROR: 5012 device communication error!
D [02/Dec/2012:14:31:03 +0100] [Job 449] Backend returned status 4 (stop printer)
D [02/Dec/2012:14:31:03 +0100] [Job 449] Printer stopped due to backend errors; please consult the error_log file for details.
D [02/Dec/2012:14:31:03 +0100] [Job 449] End of messages
D [02/Dec/2012:14:31:03 +0100] [Job 449] printer-state=5(stopped)
D [02/Dec/2012:14:31:03 +0100] [Job 449] printer-state-message="/usr/lib/cups/backend/hp failed"
D [02/Dec/2012:14:31:03 +0100] [Job 449] printer-state-reasons=paused

```So, apparently it sends three pages (though they don't get printed) and then something breaks. Does anyone have any idea why this might be? Does CUPS not know how to deal with the message about the low toner?

Cheers.


P.S. I have no intention of replacing the toner since the printer's idea of "low toner" is being able to print only 2800 pages more, which might be close to 0 for an office, but will last me quite a while...

---

### Post by JKyleOKC on 2012-12-02
I've found that when I get a "low toner" failure, I can open the printer, remove the toner cartridge, shake it horizontally a few times to redistribute the toner, [ut it back, and print a few hundred more pages before the error recurs...

---

### Post by Martom on 2012-12-03
Thanks for the suggestion, however, no luck there, I'm afraid. Even if it worked, the problem would be back in due time.

---

### Post by JKyleOKC on 2012-12-03
Definitely true. However I stretched out the previous toner cartridge for almost a year by the "shake" treatment, and only had to do it every couple of months.

---

### Post by Martom on 2012-12-04
Perhaps I'll give it another go, then, and shake it a bit harder. For now, though, does anyone have any idea why my CUPS is tripping up?

---

