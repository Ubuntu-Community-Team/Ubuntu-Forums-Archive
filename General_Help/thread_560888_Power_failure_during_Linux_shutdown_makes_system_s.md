---
title: "Power failure during Linux shutdown makes system stop working"
date: 2007-09-26
forum: General Help
---

### Post by thefirstM on 2007-09-26
One time when I was rebooting Kubuntu 7.04 installed in Wubi on my Windows XP Professional system, the electricity failed for a short time, but it was enough to make my computer shut down.  When I turned it back on, it tried to boot Windows XP but failed and rebooted.  I then tried to boot it in Kubuntu, and it failed and rebooted.

Here is how to get your system back working if such a problem occurs for you:
Obtain a Windows XP install CD.
Boot your PC from the XP install CD.
When given the option, press "R" for the Repair Console.
Windows will ask you which installation to repair.  Select "1"
Windows will ask you to log on.  Enter the Administrator password.  (NOT the user password.  If your system came preinstalled with XP, then chances are there is no administrator password.)
When Windows gives you the C:\ prompt, type "fixboot" without the quotes and hit enter.  Press "y" and press enter again to confirm.
When it is done, type "exit" and press enter.  Remove the XP CD from the drive.
When the system reboots, it should boot properly into your default operating system.

I hope this helps someone...

---

### Post by ago on 2007-09-27
Runc chkdsk /r from windows CD
If you do not have it download and run 

[http://www.tweakxp.com/article36941.aspx](http://www.tweakxp.com/article36941.aspx)

---

