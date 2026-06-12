---
title: "Ubuntu 7.10 - Need Help Setting Up Network Printer"
date: 2008-01-20
forum: General Help
---

### Post by norwestdata on 2008-01-20
I am having a small issue with getting a network printer installed.   My main desktop runs Ubuntu 7.10 and the printer is an HP PhotoSmart D7160 that is attached via USB to a Windows XP Home machine on my network.   

When I go into the printer configuration tool in Ubuntu.   I start off by clicking "New Printer" then choosing "Windows Printer via SAMBA" for the connection.  The next thing I did was click "browse" since I do not know the smb:// url for the printer.  When I click browse, another window pops up and it scans my network for printers at which I am able to see the computer and printer that I want to set up.  I double clicked on the printer and then it fills in the smb:// url for me.   

The next step asks me to select a driver so I choose the option to "Select Printer from  Database", then choose "HP", then I choose PhotoSmart D7100 in the list of models since that is the closest model to mine in the list.  The driver shows "HP PhotoSmart D7100 Foomatic/hpijs (recommended)".

Now after all these steps, it takes me back to the main screen and shows the printer in the list.  It shows the smb:// url, the make and model, and printer state as "idle"   When I click on "Print Test Page", it says "test page submitted as job 8" but after several minutes of waiting I get nothing.  The printer does not even become active.   

I've verified that the computer the printer is attached to is on, all cable are connected, the printer is on and in a ready state, the printer is set to shared on the windows machine and all firewalls are off. On the Ubuntu machine, I've verified that Samba is running.

Now after all this I am still having no luck.   Can anyone help me figure this out?

Thank You

:confused:

---

### Post by Nexusx6 on 2008-01-20
I've never tried doing a Network Connect via. a Windows USB in Linux before, (and admittedly, it sounds like a hell of a mess lol) so I can't offer you direct guidance, but I maybe able to point you in the right direction.

[http://hplip.sourceforge.net/](http://hplip.sourceforge.net/) is a site dedicated to getting HP printers working under Linux. You can poke around in there and see if you can find a solution. If I can find the time, I'll help with poking also and see what I can dig up.

---

### Post by norwestdata on 2008-01-23
I don't believe the issue has anything to do with the fact that it's a USB printer?   I can see the host computer and the printer using the network browser in Ubuntu so I know it's there.   When this desktop ran windows, I was able to set up the network printer very easily.   Now that it runs Ubuntu I have a problem.

---

