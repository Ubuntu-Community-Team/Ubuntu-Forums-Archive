---
title: "Xubuntu, samba, CUPS, and no luck printing from Windows"
date: 2007-03-01
forum: General Help
---

### Post by abstrakt on 2007-03-01
Hi everyone.  I'm really sick of the tutorials on this subject - they aren't helping.  So I'm turning to you guys for some desparate help!

Here's the deal.  I'm not a total Linux newbie - but I'm still learning some things, so if I omit any information please tell me how to find the info you need and I'll happily reply with it.

The system with the printer attached is Xubuntu, based on the 6.06 release of Ubuntu.  By default, samba was not installed.  I used Synaptic to download samba, as well as inetd with swat (for web administration).  I should also mention that although I can log into swat, I don't actually see any of the drop down menus that the swat tutorials mention, all I see are 4 big icons at the top of my screen (Home, Status, View, and Password), but nothing that actually lets me modify settings.

I want to use EITHER samba -or- CUPS.  I don't think I need to use both, even though some of the tutorials guided me through installing and configuring both services.  I don't know a lot, but what I do know leads me to believe that's a sloppy solution, and either/or should work but I don't see why I need both.

I set up a shared folder, just for fun, which I can see from my Windows machines correctly. I also set up a printer, by following several of the dozens of printer sharing tutorials that exist on the web, and it ALMOST works!  I can -see- the printer from my Windows machine, the status shows ready (it's doesn't seem to be authentication problem).  I can manually add it to the Windows box by browsing for a network printer and then manually installing the driver it needs.

Current status - When I try to print a test page, I get the following:
*Test page failed to print. Would you like to view the print troubleshooter for assistance?  Unable to create print job.*

Now this seems odd, but I found another symptom.  When I view the Ports tab of the printer, it isn't mapped to one!  No port, no printing.  Makes sense, but I don't know how to solve it.

I'm going to attach my cups.conf and my smb.conf files for reference.  They are currently set for zero security (I just want it to work, I'll lock it down later).  One thing I suspect is wrong is the path in the [printers] section of smb.conf - I was getting desperate and trying random settings there.

Any help on this would be wonderful.
Thanks for reading my long winded typing, and I appreciate any feedback in advance.

---

### Post by WW on 2007-03-01
You are right, you shouldn't need samba to share a printer--CUPS should be able to handle it.

The only thing I can suggest is to add this (or something like it) to your cupsd.conf:
> 
Browsing on
BrowseOrder allow,deny
BrowseAllow all
BrowseAddress @LOCAL

and then restart CUPS. I don't know if this will fix your problem; I can only say that when I last did something like this, enabling "Browsing" was part of the process.  You might have to tweak the BrowseOrder, BrowseAllow and BrowseAddress options.

---

### Post by abstrakt on 2007-03-01
Thanks for the reply, but that didn't help me much.  The CUPS server doesn't seem to be working at all for me.  When I try to map a printer to [http://server:631/printers/printer](http://server:631/printers/printer) I simply get a 'path not found' type error, even though I know darn well it's there since I can see it in network places when I browse.

I'm so frustrated with this I'm about to give up and go back to windows for the print server, it's making me crazy.

---

