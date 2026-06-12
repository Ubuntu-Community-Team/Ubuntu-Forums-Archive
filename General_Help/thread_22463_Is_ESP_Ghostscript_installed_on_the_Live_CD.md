---
title: "Is ESP Ghostscript installed on the Live CD?"
date: 2005-03-27
forum: General Help
---

### Post by Nathaniel Firethorn on 2005-03-27
Hi, all,

I'm trying to get my printer working from the Live CD before I do a complete install. My printer is a Lexmark E322. 

Nothing is getting printed. lp commands are accepted normally but nothing is going to the printer. Digging a bit deeper, I'm getting the following error in /var/log/cups/error_log whenever I try to print:

> Unable to convert file 0 to printable format for job <whatver>!
Do you have ESP Ghostscript installed?So, my big question is: Does the Live CD have ESP Ghostscript installed, or is this error message a red herring?  How can I check whether ESP Ghostscript is installed?

P.S.  Here's what's worked for me in /etc/printcap under Red Hat 7:

> LexmarkE312:\
	:sh:\
	:ml=0:\
	:mx=0:\
	:sd=/var/spool/lpd/LexmarkE312:\
	:lp=/dev/lp0:\
	:lpd_bounce=true:\
	:if=/usr/share/printconf/mf_wrapper:

---

