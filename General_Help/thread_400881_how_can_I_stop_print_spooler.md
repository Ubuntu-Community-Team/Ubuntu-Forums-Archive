---
title: "how can I stop print spooler?"
date: 2007-04-04
forum: General Help
---

### Post by mdurham on 2007-04-04
Hi, I'm using Feisty, If I attempt to print several pages and want to stop, say, after the first page or so, I press the off_line button on the printer to stop it. Then I click on the spooler (or whatever) icon and stop (not pause) the printing job.
BUT it still wants to keep printing. Even if I turn the printer off and back on, which means there must be some stored up print file just waiting to be printed.
How can I flush this out? The only way I've found to kill the print job is to reboot.
I would have expected stopping the print job to do this but apparently not.
Cheers, Mike

---

### Post by amohanty on 2007-04-04
Check the manual for the following commands:
lpq (to view the printer queue)
lprm (to cancel a print job)

Technically stopping the print job should stop printing after whatevers in the printer's buffer is done. Instead of restarting try restarting the cupsys service (if its an HP printer the hplip service too) using
sudo /etc/init.d/cupsys restart

HTH
AM

---

### Post by Stoneface on 2008-06-22
lpq as a command does not work. Neither does sudo /etc/init.d/cupsys restart cancel printing.. I need to loose the printing job. I need paper for another one :-(
lprm does not stop the printer from printing either... Isn't there a lprm all?

---

### Post by Stoneface on 2008-06-22
Well I lprm-ed and then disconnected the HP from the electricity grid. The job was still there, but lpq -a showed the jobs. Then cancel job# did the job. Now all seems to be peachy again. I saved another tree today :-)

---

