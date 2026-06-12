---
title: "CUPS not printing on Brother MFC-L2700DW"
date: 2017-08-01
forum: General Help
---

### Post by Jim_Lynch on 2017-08-01
There is a Brother MFC-L2700DW all in one printer wirelessly connected to a network as 192.168.30.118.  I'm sure of the ip address because I can connect to it via http and look at the status.  I also see the mac address on the lcd panel and it corresponds to the mac address in pfsense which links to .118.   

The cups server on 192.168.50.2 sees the printer fine and I was able to configure it without difficulty.  I can telnet to port 9100 on .118 and was able to connect the cups server with either server://192.168.30.118:9100 or server://192.168.30.118.  Everything looks great and when I print a test page, it shows me the job in the print queue and then show it finished in the jobs completed.  The only problem is that it must be  using invisible paper. 

I used the driver marked as   MFC-L2700DW from the list.

 I attempted to use the print self test page and it claimed it was successful, but again, no paper.
I don't know what to try next.  I did browse the printer and look at the settings and all looks fine.
Anything else I might do?
Thanks,
Jim

---

### Post by him610 on 2017-08-01
It seems to be configured incorrectly. Is this address really what you have for the server, or is it a mistype?

> 192.168.[COLOR="#FF0000"]50[/COLOR].2

I have an operational Brother MFC7360N with a wired connection, *socket://192.168.1.99* , not *server://*

> I used the driver marked as MFC-L2700DW from the list.

What list? Where did you get the driver from?

My suggestion would be to download the *Driver Install Tool* from this link....
[http://support.brother.com/g/b/downloadlist.aspx?c=us&lang=en&prod=mfcl2700dw_us_eu_as&os=128]("http://support.brother.com/g/b/downloadlist.aspx?c=us&lang=en&prod=mfcl2700dw_us_eu_as&os=128")

And, read the instructions that come with it.

Note: After rereading your original message, I realized I may be out of my element here. It appears your CUPS server is on a separate machine - is that correct?

---

### Post by Jim_Lynch on 2017-08-02
It is a typo, It's socket://192.168.30.118.  Sorry.  Yes, there are multiple vlans in the network and the network configuration is such that the .30 net is visible from the .50 net.  The .50.2 is a server.  There are currently 5 other printers, some of them on the .30 net configured and working under the CUPS server so I don't think it's a network issue.  I can telnet to port 9100 on .30.118 from 50.2.  That tells me there is no network issue.  

I installed the file,  mfcl2700dwcupswrapper-3.2.0-1.i386.deb, which I downloaded from the Brother web site.  It included a file, brother-MFCL2700DW-cups-en.ppd which is what I used.

Yes the printer is a wirfi printer at .30.118 and the server is at .50.2.  I'll take a look at that web site, but it looks very much like the site I got the aforementioned .deb file from. 

Thanks,
Jim.

---

### Post by him610 on 2017-08-02
> My suggestion would be to download the Driver Install Tool 
Referenced *Driver Install Tool* downloads, installs the drivers, and configures CUPS on your own machine. I don't know how it works when going through CUPS installed on a separate system - beyond my pay grade and accumulated skill set. ;)

Good luck.

---

### Post by Jim_Lynch on 2017-08-03
It seemed to work OK but the command line that it suggested I execute implied it was expecting the printer on a usb port.  However the .ppt file was installed.  

Jim.

---

