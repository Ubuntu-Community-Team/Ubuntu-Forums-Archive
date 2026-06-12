---
title: "Something wrong with CUPS?"
date: 2007-01-11
forum: General Help
---

### Post by turtlboy on 2007-01-11
Hi, I've got a laptop at my house that I'm trying to repurpose as a print/scan server using Dapper. I have several computers on a wireless network, and a printer that just sits in a corner, now connected to this Dapper laptop.

The Dapper laptop is connected via usb to an HP OfficeJet 5610. It prints just fine, scans just fine, etc. Setup was a breeze. However, when trying to share this printer to other computers, I am having problems.

My other computers are Macs running OS X 10.4 (Tiger). I have tried a lot of different things to no avail, but I'm getting to the point where I'm wondering if it's CUPS that is broken. I use the standard Printer setup utility in OS X, and add a network printer as an IPP printer. For the address of the printer, I'm using 192.168.1.110, the ip of the Dapper laptop. The Queue I'm using is "printers/OfficeJet-5600" since OfficeJet-5600 is the name of the printer. I tell it to print using a Generic PostScript driver.

It adds this and doesn't complain. If I go to print something, it acts like everything is cool. I see network traffic (it's sending the postscript file to the dapper laptop, i assume). If I look at [http://localhost:631](http://localhost:631) and check the printers page, I see something like this:

```
Generic PostScript Printer  	
Description: 192.168.1.110
Location:
Printer State: idle, accepting jobs.
": Print file accepted - job ID 10."
Device URI: http://192.168.1.110:631/printers/OfficeJet-5600
```

If I look at completed jobs, I see:

```
_192_168_1_110-49   	Admin on localhost - CUPS v1.1.23   	anson   	26k   	 completed at
Tue Jan 9 00:18:26 2007
```

So, everything looks like it should. But nothing prints. So I go look at the laptop's [http://localhost:631](http://localhost:631) cups page. Everything looks normal (idle, accepting jobs, published.). Look at completed jobs, sure enough, there's my job marked as completed that I sent remotely. But nothing ever printed!

If I print a test page from the Dapper laptop, it does everything expected. If I print a test page from my Mac, it looks like it goes. It says it went. The Dapper laptop says it went. But it didn't.

What's the deal? Is it me, or is it CUPS, or what? This is driving me batty.

---

### Post by yetanothersteve on 2007-01-20
I had a similar problem, Ubuntu Dapper host connected to an HP LaserJet 5P via parallel port and then a MacBook Pro attempting to print through the Ubuntu host acting as a print server.

Did you Allow other servers to browse and print from Ubuntu by changing the default Ubuntu CUPS configuration which only allows the localhost to print?
[URL="http://ubuntuguide.org/wiki/Dapper#Print_Server_.28cupsd.29"]
See this guide [/URL]

I changed /etc/cups/cups.d/browse.conf to
```
Browsing on
```


I changed /etc/cups/cups.d/ports.conf to
```
Port 631
#Listen localhost:631
Listen /var/run/cups/cups.sock
```
To cause cups to listen on all interfaces at port 631.

And I added to /etc/cups/cupsd.conf
```
BrowseAllow 192.168.11.*
BrowseAddress @IF(eth0)

```
where eth0 is the ethernet interface that the Mac can reach
and 
in the <Location /> section
```
Allow 192.168.11.*
 
```

Where 192.168.11.* represents the IP addresses on my local network.

You have to restart Cups after changing the configuration files:
```
sudo /etc/init.d/cupsys restart
```

Remember to back up all files befoe changing them.

The settings on your mac look good to me. The mistake I made was not adding printers/ to the front of the queue name in the Mac client configuration.

Also check if maybe you need to update the printer driver on the Mac client. For my ancient printer, I needed to use the [Gutenprint]("http://gimp-print.sourceforge.net/MacOSX.php3") driver, formerly known as Gimpprint.

Check your log files at /var/log/cups  
The access_log and error_log may have clues

---

