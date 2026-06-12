---
title: "upgrade to Edgy - now unable to print to printers on XP"
date: 2007-04-04
forum: General Help
---

### Post by HereInOz on 2007-04-04
Hi All,

I have just upgraded from Dapper to Edgy, and where previously I could happily print to a couple of printers (HP Laserjet and Epson C41X Inkjet) on a Windows XP machine, I now find that I cannot print to these from my Ubuntu machine.

The printers are still apparently installed, and you can send the print job to the print spool, but nothing ever prints and eventually the job is stopped and that is it.

Anybody got any clues on this one?

These two printers are set up in Ubuntu as Windows (SMB) printers and have been working fine until the upgrade.  Is there anything perhaps that may have been removed during the upgrade, or some package(s) which may need to be re-installed to get things working again.

I hope you can help.

---

### Post by HereInOz on 2007-04-04
Just for the record, I have solved this one.  For reasons that elude me, I removed the shares on both printers on the XP machine, rebooted both the XP machine and the Ubuntu machine, then re-instated the shares on both the printers, using different share names, and all now works well.

I have no idea why this worked, given that I changed nothing on the XP box prior to this, but I will accept the fix and have an early night.

---

