---
title: "Configuring Network Printer: Sharp AL-1655CS"
date: 2008-07-10
forum: General Help
---

### Post by kevCast on 2008-07-10
Hello. My last obstacle in setting up this Ubuntu box for my family is this printer. I'm trying to set it up so it can be accessed by all computers on the network, however, I'm not sure how. I don't know the protocols it's using nor the IP address of the system. Please help, as I really don't want to have to pull out the XP install disc.

---

### Post by theorist on 2008-12-17
> **kevCast said:**
> Hello. My last obstacle in setting up this Ubuntu box for my family is this printer. I'm trying to set it up so it can be accessed by all computers on the network, however, I'm not sure how. I don't know the protocols it's using nor the IP address of the system. Please help, as I really don't want to have to pull out the XP install disc.
I'm facing the same obstacle.  Have you had any success using te Sharp AL-1655CS as a network printer?  

I know the IP address of my printer, as assigned by my router and confirmed with the rudimentary HTML interface of the printer, but don't know how to print to it over the network from Ubuntu or any other Linux distribution.

Thanks,
Eric

---

### Post by fbugnon on 2009-02-16
I've also tried printing from other Linux distros to the AL-1655CS as a network printer (ie., connected to a Windows-based computer), but no success either.  Nothing comes out of the printer and all jobs are blocked afterward.

I've also tried using the original CD from the Sharp with **wine**. It seems like it installs correctly, but - as it appears to me - it has problems trying to find the printer in the USB connection.

Has anyone tried or has managed to make a work-around this way, using wine and the original software provided by Sharp?

Please let us know :)

Cheers

---

### Post by jobdrb on 2009-05-07
I had successful printing from ubuntu on Sharp 1655CS.

The ONLY way, to print from Linux, Mac OSX, Vista, Vista 64.
is intalling the printer driver (Network or USB) in a Windows XP,
and then use the Virtual Printer Driver (GhostScript).
The Virtual Driver, will appear like a PS printer, and will 
work for every Linux, OSX, (Cups).

---

### Post by fbugnon on 2009-06-26
> **jobdrb said:**
> I had successful printing from ubuntu on Sharp 1655CS.

The ONLY way, to print from Linux, Mac OSX, Vista, Vista 64.
is intalling the printer driver (Network or USB) in a Windows XP,
and then use the Virtual Printer Driver (GhostScript).
The Virtual Driver, will appear like a PS printer, and will 
work for every Linux, OSX, (Cups).

Hi jobdrb,

I'm not sure I understand how you manage this.  Are you saying we should try to use the driver installed on a XP machine by simply adding (to Mac OS, Linux, etc.) a shared printer?  I guess I've tried this but couldn't print.

Could you please explain (for newbes!).  Thank you!

---

### Post by fbugnon on 2009-09-19
OK, this is just to let the community know that SHARP is not willing to help us on this matter and, please correct me if I'm wrong, but up until now there is no solution for this problem.

I´ve contact SHARP customer relationship.  To whom in may concern, I´ve copied below their answer, my reply and their final position on the subjetc:

**SHARP first answer:**
[INDENT]February 17, - Subject:	AL1655CS
	
"Good Morning Mr. _______, 

Thank you for contacting Sharp Electronics Corporation allowing us the opportunity to assist you. 

Unfortunately, our units will not work on Linux.

Regards,

Johanna Vicich
Sharp Electronics Corp. USA
Service and Support Group
Customer Assistance Center"
[/INDENT]

**My reply:**
[INDENT]February 17, 2009 - Subjetct: Re.: AL1655CS
"Good morning Ms. Vicich,

Yes - and I have to say, unfortunately -, I've notice that the Sharp AL-1655CS does not work on Linux.

Since I do like your product very much, I was wondering if you could (or maybe have a plan to do in the near future) provide me with a driver to make it work under Linux, for we're switching the operational system of the whole company.

Thank you once again,

Best regards,
(...)"
[/INDENT]

**SHARP final position:**
[INDENT]February 17, 2009 - Subjetct:	Re.: AL1655CS

"Good morning Mr. _______,

Unfortunately, at this time we are not planning to create any new drivers for this unit.

Regards,

Johanna Vicich

Sharp Electronics Corp. USA
Service and Support Group
Customer Assistance Center
630-378-3370 - Telephone no.
630-378-9980 - Fax no.
[email]jvicich@sharpsec.com[/email] - email"[/INDENT]

---

### Post by nmgraywiz on 2009-11-25
Have been attempting to get sharp printers to work with ubuntu for some time now.. had it working marginaly, but now things are worthlessly useless.... I have an AL-2040CS, which I managed to get working once. however since upgrading to 9.10 I'm having to re-hunt things down to get a working configuration. Has anyone had any luck with Sharp Printers. Personally the best recommendation I can make to folks with Sharp Products.

Send them back to the company with a letter that will selfdistruct once read.

Currently I am ADAMANTLY UN RECOMMENDING ANY AND ALL SHARP Products. Their support is worthless, and they have NO plans on supporting their crappy products. Publish this far and wide. DO NOT BUY SHARP PRODUCTS. The company will not support their products being sold.

---

