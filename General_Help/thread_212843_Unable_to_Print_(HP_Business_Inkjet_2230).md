---
title: "Unable to Print (HP Business Inkjet 2230)"
date: 2006-07-10
forum: General Help
---

### Post by davemicc on 2006-07-10
I am unable to print to my HP Business Inkjet 2230 printer in Dapper. I used to be able to print fine in Breezy. This machine also has Windows on another partition and Windows will print to it fine.

The problem printer is connected to the machine over a parallel port connection. Dapper will print to a HP Deskjet 960c connected to a Windows 98 machine on the network over SMB without trouble.

When I try to print anything the printer does nothing at all. The job does show up in the job queue accessed via the print icon in the "Notification Area", but after a few seconds the "state" changes from "Printing: job-printing" to "Stopped: job-stopped."

I changed the LogLevel to debug in /etc/cups/cupsd.conf and tried to print. I pasted part of /var/log/cups/error_log to [http://paste.ubuntu-nl.org/17686]("http://paste.ubuntu-nl.org/17686") afterwards.

Any help or info about similar experiences would be appreciated.

---

### Post by klytu on 2006-07-10
> **davemicc said:**
> I am unable to print to my HP Business Inkjet 2230 printer in Dapper. I used to be able to print fine in Breezy. This machine also has Windows on another partition and Windows will print to it fine.

The problem printer is connected to the machine over a parallel port connection. Dapper will print to a HP Deskjet 960c connected to a Windows 98 machine on the network over SMB without trouble.

When I try to print anything the printer does nothing at all. The job does show up in the job queue accessed via the print icon in the "Notification Area", but after a few seconds the "state" changes from "Printing: job-printing" to "Stopped: job-stopped."

I changed the LogLevel to debug in /etc/cups/cupsd.conf and tried to print. I pasted part of /var/log/cups/error_log to [http://paste.ubuntu-nl.org/17686]("http://paste.ubuntu-nl.org/17686") afterwards.

Any help or info about similar experiences would be appreciated.

I had a similar problem with an HPDeskJet parallel port printer. See this thread: [http://www.ubuntuforums.org/showthread.php?t=184838](http://www.ubuntuforums.org/showthread.php?t=184838) and read all of it. I don't think your printer driver is the same as mine, but I am pretty sure that it has a configuration file and you might want to check it to make sure the version section is not blank and includes your specific printer model. 

Hope that helps you.

---

### Post by davemicc on 2006-07-10
I wasn't able to find such a file. That one seems to be specific to Deskjets.

The devices supported by HPLIB are listed on its site and Business Inkjet 2230 [is listed]("http://hplip.sourceforge.net/supported_devices/inkjet.html"). However, in the "Parallel" column it says "No." I guess that means it's not supposed to be able to print over a parallel connection? How was it working in Breezy then? In the "USB" column it says "Yes," but there doesn't seem to be a USB connection on the printer.

The [error log I posted to pastebin]("http://paste.ubuntu-nl.org/17686") includes these lines (starting at line 330), and I think they look more interesting than the rest of it:
```
D [10/Jul/2006:12:01:08 -0400] [Job 24] hpijs: printer.cpp:1192: apdk::DRIVER_ERROR apdk::Printer::SetPenInfo(char*&, BOOL): Assertion `0' failed.
D [10/Jul/2006:12:01:08 -0400] [Job 24] ESP Ghostscript 815.02: Can't start ijs server "hpijs"
D [10/Jul/2006:12:01:08 -0400] [Job 24] **** Unable to open the initial device, quitting.
D [10/Jul/2006:12:01:08 -0400] [Job 24] renderer return value: 1
D [10/Jul/2006:12:01:08 -0400] [Job 24] renderer received signal: 1
D [10/Jul/2006:12:01:08 -0400] [Job 24] Process dying with "Possible error on renderer command line or PostScript error. Check options.", exit stat: 3
D [10/Jul/2006:12:01:08 -0400] [Job 24] error: Illegal seek (29)
D [10/Jul/2006:12:01:08 -0400] [Job 24] Possible error on renderer command line or PostScript error. Check options.
D [10/Jul/2006:12:01:08 -0400] [Job 24] KID3 exited with status 3
D [10/Jul/2006:12:01:08 -0400] [Job 24] Renderer exit stat: 3
D [10/Jul/2006:12:01:08 -0400] [Job 24] Renderer process finished
D [10/Jul/2006:12:01:08 -0400] [Job 24] Killing process 9923 (KID3)
D [10/Jul/2006:12:01:08 -0400] [Job 24] Process dying with "Error closing renderer", exit stat: 3
D [10/Jul/2006:12:01:08 -0400] [Job 24] error: Bad file descriptor (9)
D [10/Jul/2006:12:01:08 -0400] [Job 24] Error closing renderer
E [10/Jul/2006:12:01:08 -0400] PID 9916 (/usr/lib/cups/filter/foomatic-rip) stopped with status 3!
D [10/Jul/2006:12:01:08 -0400] [Job 24] tail process done writing data to STDOUT
D [10/Jul/2006:12:01:08 -0400] [Job 24] KID4 finished
```

---

### Post by klytu on 2006-07-10
> **davemicc said:**
> I wasn't able to find such a file. That one seems to be specific to Deskjets.

The devices supported by HPLIB are listed on its site and Business Inkjet 2230 [is listed]("http://hplip.sourceforge.net/supported_devices/inkjet.html"). However, in the "Parallel" column it says "No." I guess that means it's not supposed to be able to print over a parallel connection? How was it working in Breezy then? In the "USB" column it says "Yes," but there doesn't seem to be a USB connection on the printer.



I don't think that chart means your printer won't print over a parallel connection, it just means it's not supported by HPLIP. Mine isn't either, but it prints fine in Ubuntu. Looking at the error log you linked in your original post, there appears to be an error condition just before line 330. I wish I could be of more help, but I don't have your printer model available to test any theories on what is causing the trouble. Based on the error log you might want to Google "apdk" and also that along with your printer model and see what you turn up. Since your printer worked before I doubt there is anything wrong with the driver itself. Looks to me like it's being fed an unrecognizable option or it's missing a necessary option at some point when it's being called, which is why I suggested poking around for a configuration file for the driver.

---

### Post by davemicc on 2006-07-12
Thanks for trying to help...I will try some more when I have more time.

---

