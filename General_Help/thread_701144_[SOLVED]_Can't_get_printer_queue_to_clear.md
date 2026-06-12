---
title: "[SOLVED] Can't get printer queue to clear"
date: 2008-02-19
forum: General Help
---

### Post by ad_267 on 2008-02-19
Hi,

I have a Canon iP1600 that I had previously working on Ubuntu 7.10 using the iP2200 drivers. I had to reinstall Ubuntu because I messed some stuff up and I reinstalled the printer but this time I followed this guide: [http://sidux.com/PNphpBB2-viewtopic-t-4659.html](http://sidux.com/PNphpBB2-viewtopic-t-4659.html) and modified the ppd file to try and get options for higher resolutions. When I tried printing the jobs appeared to go through successfully but my printer didn't print.

So then I thought I should put the ppd file back how it was. I've reinstalled the drivers and deleted the printer and reinstalled it and I've restarted the printer and my computer and printed to it from windows but now every time I try to print from Ubuntu it won't work. I can't see any jobs under manage print jobs and I even cleared all jobs by going to [http://localhost:631/](http://localhost:631/). But  when I try to print a test page it says "Test page submitted as job 11", as if those previous jobs have not completed.

Hopefully there's an easy way to fix this and get the printer working again.

Thanks,
Adam

---

### Post by ad_267 on 2008-02-20
Help anyone?

My printer was working fine previously. Now nothing will print but I'm not getting any errors

---

### Post by BoeBoe on 2008-02-20
Hi,

Looks like the print jobs are still there hiding somewhere. Double check through System Settings > Printer.

Does your driver provide any interface of its own?

---

### Post by ad_267 on 2008-02-21
Thanks for the suggestions,

I've had a look through the printer configuration and printer job manager and can't see anything, even in the completed jobs. I deleted all the files in /var/spool/cups and that didn't help.

No, the driver doesn't provide any interface that I know of

---

### Post by ad_267 on 2008-02-25
For anyone else that has this problem, I got the printer to work by uninstalling the drivers through synaptic and then following this guide [https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/CanonPixmaIP2200](https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/CanonPixmaIP2200)

---

