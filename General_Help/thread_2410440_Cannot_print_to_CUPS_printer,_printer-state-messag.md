---
title: "Cannot print to CUPS printer, printer-state-message=&quot;filter failed&quot;, log attached"
date: 2019-01-15
forum: General Help
---

### Post by nasbit on 2019-01-15
Hello everyone,

So I have a Brother HL-L2320D connected via USB to my Ubuntu 18.04 Server install. I have installed the linux drivers and shared the printer in CUPS.

When I visit localhost:631/printers I see the printer listed there. I have also printed successfully to the printer from a Windows laptop. When I try to print from my Macbook the printer hangs in the "filter failed" state. I checked the error log and I found the following relevant sections:

```

Started filter /usr/lib/cups/filter/rastertopwg (PID 7151)
Started filter /usr/lib/cups/filter/rastertopdf (PID 7152)
Started filter /usr/lib/cups/filter/pdftopdf (PID 7153)
Started filter /usr/lib/cups/filter/brother_lpd_wrapper_HLL2320D (PID 7154)
...
PID 7152 (/usr/lib/cups/filter/rastertopdf) stopped with status 1
Error: Too many pages in Page tree.
No pages will be processed (FirstPage > LastPage)
printer-state=3(idle)
printer-state-message="Filter failed"
printer-state-reason=none

```

I have omitted most of the log but it seems that all of the PIDs return no error except for PID 7152 which returns the above error.

Does anyone know what is causing this error? I tried removing some paper in case this was relevant, same error.

Thanks

---

