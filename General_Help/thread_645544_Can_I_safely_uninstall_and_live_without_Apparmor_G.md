---
title: "Can I safely uninstall and live without Apparmor? Gutsy"
date: 2007-12-20
forum: General Help
---

### Post by alanbe on 2007-12-20
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/133982](https://bugs.launchpad.net/ubuntu/+bug/133982) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Greetings

I did a clean install from Kubuntu  Edgy to Kubuntu  7.10. Edgy was actually fine but I wanted the latest OpenOffice and other programs not backported to edgy.

Problem: my HP LaserJet no longer works. I did a forum search and found that this is a widespread problem. The problem appears to be AppArmor and Cups.
Bug #133982

Here is the error I get in cups:

E [19/Dec/2007:19:01:22 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [19/Dec/2007:19:01:24 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [19/Dec/2007:19:01:24 -0500] CUPS-Accept-Jobs: Unauthorized
E [19/Dec/2007:19:01:24 -0500] Resume-Printer: Unauthorized
E [19/Dec/2007:19:01:59 -0500] CUPS-Set-Default: Unauthorized
E [19/Dec/2007:19:08:17 -0500] Pause-Printer: Unauthorized
E [19/Dec/2007:19:08:22 -0500] Resume-Printer: Unauthorized
E [19/Dec/2007:19:10:56 -0500] CUPS-Delete-Printer: Unauthorized
E [19/Dec/2007:19:16:42 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [19/Dec/2007:19:16:43 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [19/Dec/2007:19:16:43 -0500] CUPS-Accept-Jobs: Unauthorized
E [19/Dec/2007:19:16:43 -0500] Resume-Printer: Unauthorized
E [19/Dec/2007:19:16:45 -0500] CUPS-Delete-Printer: Unauthorized
E [19/Dec/2007:19:17:45 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [19/Dec/2007:19:17:46 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [19/Dec/2007:19:17:46 -0500] CUPS-Accept-Jobs: Unauthorized
E [19/Dec/2007:19:17:46 -0500] Resume-Printer: Unauthorized
E [19/Dec/2007:19:18:13 -0500] CUPS-Set-Default: Unauthorized
E [19/Dec/2007:19:19:18 -0500] CUPS-Reject-Jobs: Unauthorized
E [19/Dec/2007:19:19:26 -0500] CUPS-Accept-Jobs: Unauthorized


Question can I correct this simply by uninstalling Apparmor? Will removing apparmor cause system instability? 

I don't use my PC as a server. I use Firestarter. I use Ubuntu repositories or compile new programs from source  myself.  I occasionally use XAMPP for website testing, but I always stop the servers after I am done. Apparmor would seem to not be as crucial to my work.


alanbe

---

### Post by alanbe on 2007-12-21
I was unsure whether apparmor was so tied into the kernel that Gutsy would not work without it.
I was a bit impatient for a reply. I really would like a computer to be able to print.
I went ahead and risked rendering my system unusable.

I purged apparmor and I also compiled and installed the latest cups.

Printing is working fine. I have read about the security benefits of apparmor. I guess I have to live with risk in order to have a desktop which can print hard copies if I need it. A Hobson's choice for me actually

alanbe.

---

