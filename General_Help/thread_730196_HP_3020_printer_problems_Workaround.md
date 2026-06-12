---
title: "HP 3020 printer problems Workaround"
date: 2008-03-20
forum: General Help
---

### Post by madcap_magician on 2008-03-20
I have an HP LaserJet 3020 and since upgrading to 7.10 it has not been working right. 

The problem:
When I plug in the USB cord Ubuntu auto-configures the printer using foomatic/hpijs and also configures fax drivers using HP Fax.  When I'd try to print something I'd only get the first quarter of the first page, the rest of the page would be blank and no additional pages would come out.  The job in the print queue would be stuck in a Pending status and any new print jobs would also be stuck in Pending status.

The workaround:
Disable the Fax device.  System->Administration->Printing, select the fax device. On the policies tab for the fax device, uncheck the Enabled box.  Now your 3020 should print just fine.

There is probably some underlying bug that needs fixing but I don't know what it is.  This workaround does the trick and now I can print again.  The 3020 doesn't actually have a fax machine built into it so I'm not sure why Ubuntu tries to configure a fax machine.  This hasn't been working right for me since upgrading to 7.10, it worked fine before that.  I noticed that whenever Ubuntu auto-configured both a printer and fax that it didn't work right but if I only manually set up the printer it worked fine.  So I needed a way to not have the fax machine configured every time I plugged in the usb cord.  Disabling the fax machine worked.

---

