---
title: "Printer sharing"
date: 2012-11-12
forum: General Help
---

### Post by afbratt on 2012-11-12
I am temporarily having to use my laptop that has Ubuntu 12.04 LTS as my family's main computer, however for the life of me I can't figure out how to correctly share the printer that is now connected to my laptop with other members of my family who all have windows based PC's. Can someone help me out please?

---

### Post by gerowen on 2012-11-12
Go to the system settings and click on printers on the Ubuntu machine.  Click "Server" then "Settings" (Menu items that will be at the main top of your screen if you're using Unity) and check the box that says "Publish Shared Printers Connected to this system", then click OK.  Right click the printer, and make sure it's set as shared.  Now make sure the Windows machines all have the printer drivers installed because they will not be able to use the Linux drivers in use by the print server, your laptop.  Open a web browser from the Windows machines, and go to the following address:

[http://foo:631](http://foo:631)

Where "foo" is the IP of the Ubuntu laptop.  On the top click on "Printers", then right click the shared printer in question and "Copy Link Location".  Now go through the normal process to add a network printer in Windows and point it to the http address you copied from the hyperlink.  For example the one to the printer shared across the room from my desktop is:

[http://10.1.1.4:631/printers/Deskjet-F2100-series](http://10.1.1.4:631/printers/Deskjet-F2100-series)

I've attached a few screenshots for your reference.  I don't have the options set on this computer the same as I wrote out because I'm actually posting this from my laptop, which is not serving as the print server, just a client, but these should serve as a visual guide of what to look for.  I have done this successfully several times, you just gotta keep a copy of the printer's drivers around in case the Windows machines need them.

---

### Post by gerowen on 2012-11-12
It's worth noting that it helps if the IP of your laptop remains the same.  A lot of times IPs get leased for a pre-determined amount of time, and as long as the laptop stays on, it should keep hold of that lease, but be aware that if you take the laptop somewhere with you for a while, and bring it back and the printer doesn't work, your IP lease may run out in the router, which might make it give you a different IP, and you may have to go edit the printer port on the windows machines to point to your laptop's new IP address.  You can avoid this by setting up a reservation in your router to make sure it always gets the same IP, I just thought I'd point this out in case it happened.

---

### Post by afbratt on 2012-11-14
thank you for the help

---

