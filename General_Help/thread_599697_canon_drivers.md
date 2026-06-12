---
title: "canon drivers"
date: 2007-11-01
forum: General Help
---

### Post by pgfox46 on 2007-11-01
i need drivers for canonImageRunner 2830 for printing and scanning.
i try ppd install and BrightQ Pro, that installs nicely but dont work call canon and got told to email then this is there answer 
(see bottom for my reply)

[email]customer_support@canada.canon.com[/email] wrote:
>
> Dear  Paulo Graca
>
> Thank you for your E-mail inquiry regarding your Image Runner 2830.
>
> Since your product inquiry falls under our commercial product line-up, all information and support is available exclusively through our commercial dealers.  Please contact them directly with your inquiry. There may be a sticker on the unit indicating a telephone number to contact.  Alternately, dealers in your area are:
>
> Pitney Bowes Danka
> 286 Rutherford Road South
> Brampton, ON, L6W 3K7
> Tel.: 905/458-4168
>
> IKON Office Solutions
> 5935 Airport Road
> Mississauga, ON, L4V 1W5
> Tel.: 905/602-1220
>
> Pitney Bowes of Canada Ltd.
> 1200 Sheppard Ave E Suite 300
> North York, ON, M2K 2R8
> Tel.: 416/753-2300
>
> Should you require further assistance, please feel free to email us or visit our customer support website at [http://www.canon.ca](http://www.canon.ca) 
>
> Sincerely,
>
> Sylvester C.
>
> Technical Support Representative
>
> Customer Information Centre
>
> Canon Canada Inc.
>
>
> You wrote: 
>
> hi i need linux drivers for my leased ir2830 as we are moving to set workstations as linux box
> or my have to exchange to a supported model need printing faxing and scanning capability


and i reply 

"Gentleman i think you fail to see this product is leased directly from canon Canada inc tel #1 866 266 6634
i have call tech support and im told that BrightQ Pro is Canon's Unix and Linux Printer Driver and device management application for the Canon imageRUNNER series of printers.
please see [http://canon.codehost.com/](http://canon.codehost.com/) ,however it dos not have the ir 2830 printer the closest is ir 2870 and it dos not work.

So please i need your support  not the run around, as Technical Support Representative's you all know the relevance of linux and the need the costumers have for drivers

thank you   Paulo Graca"

if some one can help me let me know thanks

---

### Post by pgfox46 on 2007-11-01
no 1 can help?
bump

---

### Post by pgfox46 on 2007-11-02
boy cold welcome:confused: to a brand new guy
2 weeks in to trying Ubuntu and i joust cant do it 
I guess i ill look @ this in another year 
pg out

---

### Post by VON_CAPO on 2007-11-02
This machine is for corporative use (it is not a standard device) and it looks like is not compatible at all.

The Canon brochure states that:
[[IMG]http://img337.imageshack.us/img337/6826/58234446mo8.th.png[/IMG]](http://img337.imageshack.us/my.php?image=58234446mo8.png)

I believe that your best hope is Canon Support.

---

### Post by Maestro23 on 2007-11-02
Check the Open Printing Website to see if that printer can be used in Linux.

[http://www.linux-foundation.org/en/OpenPrinting](http://www.linux-foundation.org/en/OpenPrinting)

---

### Post by pgfox46 on 2007-11-02
try that ir2870 is 2200 is also but that is it and BrightQ Pro sees it but no go so thus unbuntu it sees the printer something windows cant do but it prints 1 line per page and garbled 

thank you for you response  and help :)

---

### Post by VON_CAPO on 2007-11-02
> **pgfox46 said:**
> unbuntu it sees the printer something windows cant do but it prints 1 line per page and garbled 

thank you for you response  and help :)
If Ubuntu recognized the printer is a good start.
Now you should find a driver that use the same or similar consumables (toner).

---

### Post by pgfox46 on 2007-11-02
> **VON_CAPO said:**
> If Ubuntu recognized the printer is a good start.
Now you should find a driver that use the same or similar consumables (toner).

please elaborate 
and thank you

---

### Post by VON_CAPO on 2007-11-02
> **pgfox46 said:**
> please elaborate 
and thank you
As Maestro23 wrote:
[QUOTE=Maestro23]
Check the Open Printing Website to see if that printer can be used in Linux.

[http://www.linux-foundation.org/en/OpenPrinting](http://www.linux-foundation.org/en/OpenPrinting)[/QUOTE]
You will find 3 or 4 models of ** ImageRunner ** devices at the OpenPrinting web site (no one of them is your model), look for the drivers reported as working, and play with them.

Use the printer manager located at "System/Administration/Printing"

As you can see in the following screenshots, the driver that I am using is not for my printer, but it works perfect.

Follow the same method.

[[IMG]http://img217.imageshack.us/img217/5927/12425394hq6.th.png[/IMG]](http://img217.imageshack.us/my.php?image=12425394hq6.png)

[[IMG]http://img404.imageshack.us/img404/3161/49483573fp1.th.png[/IMG]](http://img404.imageshack.us/my.php?image=49483573fp1.png)

[[IMG]http://img404.imageshack.us/img404/3493/31898712jc2.th.png[/IMG]](http://img404.imageshack.us/my.php?image=31898712jc2.png)

If it does not work... look for another **LASER PRINTER** model in the list.

---

### Post by pgfox46 on 2007-11-02
ok im going to give it a try ill report back:lolflag:

---

### Post by pgfox46 on 2007-11-02
it seems the problem is the printer dos not support post script canon support told me to install pcl 5 generic drivers

---

### Post by pgfox46 on 2007-11-02
yes it works generic driver pcl5e

---

### Post by phonky on 2007-11-02
Hi

check out this link:

[http://forums.linux-foundation.org/file.php?25,file=92](http://forums.linux-foundation.org/file.php?25,file=92)

This will download a zip file with the canon imageRunner drivers for linux.

good luck

---

### Post by pgfox46 on 2007-11-02
can not download from there

---

### Post by pgfox46 on 2007-11-02
One other thing, I've been working on sane at the same time.  

I've made the following scripting changes:

/etc/sane.d/dll.conf

added the line:

net


/etc/sane.d/net.conf

192.168.1.24:9100



nothing seems to work, firing up xsane fails to see it.

Any thoughts??

PG

---

### Post by phonky on 2007-11-03
Instead of clicking on
the link,
copy the link

[http://forums.linux-foundation.org/file.php?25,file=92](http://forums.linux-foundation.org/file.php?25,file=92)

into your address field in the browser.

That should download the file (at least it works for me).

---

### Post by pgfox46 on 2007-11-04
thank you you are correct

---

### Post by pgfox46 on 2008-05-23
6 months later and still cant get the scanner to work and is the last thing holding me from totally going to Linux:( on this machine

---

