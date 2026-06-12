---
title: "Shared Printer Problem"
date: 2008-07-05
forum: General Help
---

### Post by mike4477 on 2008-07-05
I'm trying to use a shared printer on a home peer to peer network using a 7.10 install.  I can see the printer when I map to it through the System - Administration - Printing window but when I try to print a test page or anything else it just never prints.

Any thoughts?  Thanks.

---

### Post by funkydan2 on 2008-07-07
What type of printer is it?
What driver did you select in the printer setup wizard?

---

### Post by mike4477 on 2008-07-08
HP LaserJet 6L
I picked the driver for this specific printer during the setup.

Thanks.

---

### Post by mike4477 on 2008-07-10
bump

---

### Post by danwood76 on 2008-07-10
When you say share a printer is this a windows printer or a shared linux printer?
If its a shared linux printer its just a matter of ticking the share printer buttons in cups.

If you are trying to go windows -> linux or linux -> windows it can be a little harder to get samba setup correctly to do the sharing.

---

### Post by mike4477 on 2008-07-11
I'm trying to share a printer on a linux 8.04 server install from a desktop 7.10 install.  I can already get to the printer from my Windows desktop.

Thanks.

---

### Post by danwood76 on 2008-07-13
So you have setup the printer to share over samba from the linux server?

To share between linux boxes is very easy with cups, you have to set cups to share the printer on the server by clicking 'share published printers connected to this system' and then you simply enable 'Show printers shared by other systems' on  the boxes you want to use the printer.

---

### Post by mike4477 on 2008-07-16
How do I get to those options in CUPS on both the desktop and the server?

Thanks.

---

### Post by amba on 2008-07-17
thank you danwood, was looking for same problem.

Mike, you should set up the printing server:
connect to [http://serverip:631](http://serverip:631) with your browser, click on "administration" button and click 
[quote="danwood76"]
'share published printers connected to this system'
[/quote]

Then you have to setup your client.
[http://localhost:631](http://localhost:631) 
click administration button and enable
[quote="danwood76"]
'Show printers shared by other systems'
[/quote]

If your browser doesn't give cups page, then you should start cupsd.
Go in /etc/init.d/ and check if file cupsys got these rights:
-rwxr-xr-x

If not, type into a shell
```

sudo chmod 755 /etc/init.d/cupsys

```

and then start it
```

sudo /etc/init.d/cupsys start

```

enjoy :popcorn:

Edit: AH i didn't read you got windows printing already. So probably you need only to set up client, not server

---

