---
title: "Problem printing in CUPS on Network"
date: 2007-04-12
forum: General Help
---

### Post by ronald_stall on 2007-04-12
I am running Feisty with HP Photosmart C3100 connected to it. Trying to print from a Windows XP computer.

I followed these directions [https://help.ubuntu.com/community/NetworkPrintingFromWinXP]("https://help.ubuntu.com/community/NetworkPrintingFromWinXP")
 and I can now set the printer up but when I print I get an error from the Windows XP computer.

Here are the errors from the Feisty computer

/var/log/cups/access_log

192.168.1.101 - - [12/Apr/2007:15:12:58 -0500] "POST /printers/Photosmart_C3100 HTTP/1.1" 200 75 windows-ext client-error-bad-request


/var/log/cups/error_log

E [12/Apr/2007:15:12:58 -0500] Missing printer-uri or job-uri attribute!

Can anyone help me work through this?

Thanks in advance!

---

### Post by zwanzig on 2007-09-08
I get the exact same problem with a HP P2015

EDIT: Workaround for me was to delete printer in windows, and then install it as "local port" (not physical) and choosing a newly windows-system created port named [http://ubuntumachine:631/printer/HP_P2015](http://ubuntumachine:631/printer/HP_P2015). Now it works to print to, but cpu goes to 100% if I try to open settings for the printer in windows.

---

