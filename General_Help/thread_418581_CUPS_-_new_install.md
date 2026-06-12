---
title: "CUPS - new install"
date: 2007-04-22
forum: General Help
---

### Post by tomp on 2007-04-22
Install of Xubuntu went well.  Small issue with login screen (shows about 3 overlapping screens) but I can get past that.  Tried looking to add the, fb=false, to the grub config file - but can't seem to find the file yet (thought it was: /boot/grub/grub.conf ?? but - for a later time).

My major issue is with CUPS - setting up my printers.  Following the documentation:  file:///usr/share/xubuntu-docs/desktopguide/C/printer-configuration.html

#1 Launch Applications->System->Users and Groups, click on the tab Groups, and check Show all users and groups
#2 Select the group shadow and click Properties.
#3 Add the user cupsys to the group.
#4 Restart CUPS with this command: 

There is no "shadow" group, to select???
Should I create a "shadow" group ???

May seem like a minor issue but it's got me stopped cold.
PS - went through all the posts using "printing/printer/cups" as a search terms.

Any assistance is much appreciated.

TomP

---

### Post by tomp on 2007-04-22
By-passed the initial printer documentation and I now have 1 of 2 printers - printing, using a Linksys Print Server.  

#1: Description: Laser-default
Location: Office
Make and Model: Brother HL-5250DN BR-Script3
Printer State: idle, accepting jobs, published.
Device URI: socket://192.168.xx.xxx:4010
Laser prints fine . . . . . .

#2: Description: ColorJet
Location: Office
Make and Model: Canon S800 - CUPS+Gutenprint v5.0.0
Printer State: idle, accepting jobs, published.
Device URI: socket://192.168.xx.xxx:4020
Canon i860 - send a test page and it just keeps sending the page to the printer but my printer is acting like it's not receiving the signal.

Any suggestions.

Thanks,
TomP

---

### Post by tomp on 2007-04-22
Here are the log files:

ACCESS_LOG

localhost - - [22/Apr/2007:13:12:24 -0400] "GET /admin HTTP/1.1" 200 0 - -
localhost - - [22/Apr/2007:13:12:26 -0400] "POST / HTTP/1.1" 200 1470 CUPS-Get-Devices -
data removed to accommodate posting request: 
localhost - - [22/Apr/2007:14:54:30 -0400] "POST / HTTP/1.1" 200 461 Get-Jobs successful-ok
localhost - sheriff [22/Apr/2007:14:54:34 -0400] "GET /images/button-set-printer-options.gif HTTP/1.1" 304 0 - -
localhost - sheriff [22/Apr/2007:14:54:28 -0400] "GET /printers/Canon:i860 HTTP/1.1" 200 8053 - -
localhost - sheriff [22/Apr/2007:14:54:34 -0400] "GET /images/button-delete-printer.gif HTTP/1.1" 304 0 - -
localhost - sheriff [22/Apr/2007:14:54:34 -0400] "GET /images/button-set-as-default.gif HTTP/1.1" 304 0 - -
localhost - sheriff [22/Apr/2007:14:54:34 -0400] "GET /images/button-set-allowed-users.gif HTTP/1.1" 304 0 - -
localhost - sheriff [22/Apr/2007:14:54:34 -0400] "GET /images/button-search.gif HTTP/1.1" 304 0 - -
localhost - sheriff [22/Apr/2007:14:54:35 -0400] "GET /images/button-clear.gif HTTP/1.1" 304 0 - -
localhost - sheriff [22/Apr/2007:14:54:35 -0400] "GET /images/button-show-completed.gif HTTP/1.1" 304 0 - -
localhost - sheriff [22/Apr/2007:14:54:35 -0400] "GET /images/button-show-all.gif HTTP/1.1" 304 0 - -
localhost - sheriff [22/Apr/2007:14:54:35 -0400] "GET /images/button-sort-descending.gif HTTP/1.1" 304 0 - -
localhost - sheriff [22/Apr/2007:14:54:35 -0400] "GET /images/button-restart-job.gif HTTP/1.1" 304 0 - -
localhost - sheriff [22/Apr/2007:14:54:35 -0400] "GET /images/button-cancel-job.gif HTTP/1.1" 304 0 - -
localhost - sheriff [22/Apr/2007:14:54:35 -0400] "GET /images/button-move-job.gif HTTP/1.1" 304 0 - -
localhost - sheriff [22/Apr/2007:14:54:35 -0400] "GET /images/bottom-left.gif HTTP/1.1" 304 0 - -
localhost - sheriff [22/Apr/2007:14:54:35 -0400] "GET /images/bottom-right.gif HTTP/1.1" 304 0 - -
localhost - sheriff [22/Apr/2007:14:54:45 -0400] "GET /printers/Canon:i860 HTTP/1.1" 200 0 - -
localhost - sheriff [22/Apr/2007:14:54:48 -0400] "GET /cups.css HTTP/1.1" 304 0 - -
localhost - - [22/Apr/2007:14:54:48 -0400] "POST / HTTP/1.1" 200 461 Get-Jobs successful-ok
localhost - sheriff [22/Apr/2007:14:54:45 -0400] "GET /printers/Canon:i860 HTTP/1.1" 200 8053 - -
localhost - sheriff [22/Apr/2007:14:54:49 -0400] "GET /images/top-middle.gif HTTP/1.1" 304 0 - -
localhost - sheriff [22/Apr/2007:14:54:49 -0400] "GET /images/top-left.gif HTTP/1.1" 304 0 - -
localhost - sheriff [22/Apr/2007:14:54:50 -0400] "GET /images/top-right.gif HTTP/1.1" 304 0 - -
localhost - sheriff [22/Apr/2007:14:54:50 -0400] "GET /images/tab-left.gif HTTP/1.1" 304 0 - -
localhost - sheriff [22/Apr/2007:14:54:50 -0400] "GET /images/tab-right.gif HTTP/1.1" 304 0 - -
localhost - sheriff [22/Apr/2007:14:54:50 -0400] "GET /images/printer-processing.gif HTTP/1.1" 304 0 - -
localhost - sheriff [22/Apr/2007:14:54:50 -0400] "GET /images/button-print-test-page.gif HTTP/1.1" 304 0 - -
localhost - sheriff [22/Apr/2007:14:54:50 -0400] "GET /images/button-stop-printer.gif HTTP/1.1" 304 0 - -
localhost - sheriff [22/Apr/2007:14:54:50 -0400] "GET /images/button-reject-jobs.gif HTTP/1.1" 304 0 - -
localhost - sheriff [22/Apr/2007:14:54:50 -0400] "GET /images/button-move-jobs.gif HTTP/1.1" 304 0 - -
localhost - sheriff [22/Apr/2007:14:54:50 -0400] "GET /images/button-cancel-all-jobs.gif HTTP/1.1" 304 0 - -
localhost - sheriff [22/Apr/2007:14:54:50 -0400] "GET /images/button-unpublish-printer.gif HTTP/1.1" 304 0 - -
localhost - sheriff [22/Apr/2007:14:54:51 -0400] "GET /images/button-modify-printer.gif HTTP/1.1" 304 0 - -
localhost - sheriff [22/Apr/2007:14:54:51 -0400] "GET /images/button-set-printer-options.gif HTTP/1.1" 304 0 - -
localhost - sheriff [22/Apr/2007:14:54:51 -0400] "GET /images/button-delete-printer.gif HTTP/1.1" 304 0 - -
localhost - sheriff [22/Apr/2007:14:54:51 -0400] "GET /images/button-set-as-default.gif HTTP/1.1" 304 0 - -
localhost - sheriff [22/Apr/2007:14:54:51 -0400] "GET /images/button-set-allowed-users.gif HTTP/1.1" 304 0 - -
localhost - sheriff [22/Apr/2007:14:54:51 -0400] "GET /images/button-search.gif HTTP/1.1" 304 0 - -
localhost - sheriff [22/Apr/2007:14:54:51 -0400] "GET /images/button-clear.gif HTTP/1.1" 304 0 - -
localhost - sheriff [22/Apr/2007:14:54:51 -0400] "GET /images/button-show-completed.gif HTTP/1.1" 304 0 - -
localhost - sheriff [22/Apr/2007:14:54:51 -0400] "GET /images/button-show-all.gif HTTP/1.1" 304 0 - -
localhost - sheriff [22/Apr/2007:14:54:51 -0400] "GET /images/button-sort-descending.gif HTTP/1.1" 304 0 - -
localhost - sheriff [22/Apr/2007:14:54:51 -0400] "GET /images/button-restart-job.gif HTTP/1.1" 304 0 - -
localhost - sheriff [22/Apr/2007:14:54:51 -0400] "GET /images/button-cancel-job.gif HTTP/1.1" 304 0 - -
localhost - sheriff [22/Apr/2007:14:54:51 -0400] "GET /images/button-move-job.gif HTTP/1.1" 304 0 - -
localhost - sheriff [22/Apr/2007:14:54:52 -0400] "GET /images/bottom-left.gif HTTP/1.1" 304 0 - -
localhost - sheriff [22/Apr/2007:14:54:52 -0400] "GET /images/bottom-right.gif HTTP/1.1" 304 0 - -
localhost - sheriff [22/Apr/2007:14:55:02 -0400] "GET /printers/Canon:i860 HTTP/1.1" 200 0 - -
localhost - sheriff [22/Apr/2007:14:55:04 -0400] "GET /cups.css HTTP/1.1" 304 0 - -
localhost - - [22/Apr/2007:14:55:04 -0400] "POST / HTTP/1.1" 200 461 Get-Jobs successful-ok
localhost - sheriff [22/Apr/2007:14:55:02 -0400] "GET /printers/Canon:i860 HTTP/1.1" 200 8053 - -
localhost - sheriff [22/Apr/2007:14:55:04 -0400] "GET /images/top-left.gif HTTP/1.1" 304 0 - -
localhost - sheriff [22/Apr/2007:14:55:06 -0400] "GET /images/top-right.gif HTTP/1.1" 304 0 - -
localhost - sheriff [22/Apr/2007:14:55:06 -0400] "GET /images/top-middle.gif HTTP/1.1" 304 0 - -
localhost - sheriff [22/Apr/2007:14:55:06 -0400] "GET /images/tab-left.gif HTTP/1.1" 304 0 - -
localhost - sheriff [22/Apr/2007:14:55:06 -0400] "GET /images/tab-right.gif HTTP/1.1" 304 0 - -
localhost - sheriff [22/Apr/2007:14:55:06 -0400] "GET /images/printer-processing.gif HTTP/1.1" 304 0 - -
localhost - sheriff [22/Apr/2007:14:55:06 -0400] "GET /images/button-print-test-page.gif HTTP/1.1" 304 0 - -
localhost - sheriff [22/Apr/2007:14:55:06 -0400] "GET /images/button-stop-printer.gif HTTP/1.1" 304 0 - -
localhost - sheriff [22/Apr/2007:14:55:07 -0400] "GET /images/button-reject-jobs.gif HTTP/1.1" 304 0 - -
localhost - sheriff [22/Apr/2007:14:55:07 -0400] "GET /images/button-move-jobs.gif HTTP/1.1" 304 0 - -
localhost - sheriff [22/Apr/2007:14:55:07 -0400] "GET /images/button-cancel-all-jobs.gif HTTP/1.1" 304 0 - -
localhost - sheriff [22/Apr/2007:14:55:07 -0400] "GET /images/button-unpublish-printer.gif HTTP/1.1" 304 0 - -
localhost - sheriff [22/Apr/2007:14:55:07 -0400] "GET /images/button-modify-printer.gif HTTP/1.1" 304 0 - -
localhost - sheriff [22/Apr/2007:14:55:07 -0400] "GET /images/button-set-printer-options.gif HTTP/1.1" 304 0 - -
localhost - sheriff [22/Apr/2007:14:55:07 -0400] "GET /images/button-delete-printer.gif HTTP/1.1" 304 0 - -
localhost - sheriff [22/Apr/2007:14:55:07 -0400] "GET /images/button-set-as-default.gif HTTP/1.1" 304 0 - -
localhost - sheriff [22/Apr/2007:14:55:07 -0400] "GET /images/button-set-allowed-users.gif HTTP/1.1" 304 0 - -
localhost - sheriff [22/Apr/2007:14:55:08 -0400] "GET /images/button-search.gif HTTP/1.1" 304 0 - -
localhost - sheriff [22/Apr/2007:14:55:08 -0400] "GET /images/button-clear.gif HTTP/1.1" 304 0 - -
localhost - sheriff [22/Apr/2007:14:55:08 -0400] "GET /images/button-show-completed.gif HTTP/1.1" 304 0 - -
localhost - sheriff [22/Apr/2007:14:55:08 -0400] "GET /images/button-show-all.gif HTTP/1.1" 304 0 - -
localhost - sheriff [22/Apr/2007:14:55:08 -0400] "GET /images/button-sort-descending.gif HTTP/1.1" 304 0 - -
localhost - sheriff [22/Apr/2007:14:55:08 -0400] "GET /images/button-restart-job.gif HTTP/1.1" 304 0 - -
localhost - sheriff [22/Apr/2007:14:55:08 -0400] "GET /images/button-cancel-job.gif HTTP/1.1" 304 0 - -
localhost - sheriff [22/Apr/2007:14:55:08 -0400] "GET /images/button-move-job.gif HTTP/1.1" 304 0 - -
localhost - sheriff [22/Apr/2007:14:55:08 -0400] "GET /images/bottom-left.gif HTTP/1.1" 304 0 - -
localhost - sheriff [22/Apr/2007:14:55:08 -0400] "GET /images/bottom-right.gif HTTP/1.1" 304 0 - -
localhost - sheriff [22/Apr/2007:14:55:12 -0400] "GET /admin/?op=purge-jobs&printer_name=Canon:i860 HTTP/1.1" 200 0 - -
localhost - - [22/Apr/2007:14:55:13 -0400] "POST /admin/ HTTP/1.1" 401 126 Purge-Jobs successful-ok
localhost - sheriff [22/Apr/2007:14:55:14 -0400] "POST /admin/ HTTP/1.1" 200 126 Purge-Jobs successful-ok
localhost - sheriff [22/Apr/2007:14:55:12 -0400] "GET /admin/?op=purge-jobs&printer_name=Canon:i860 HTTP/1.1" 200 3477 - -
localhost - sheriff [22/Apr/2007:14:55:21 -0400] "GET /admin/?OP=redirect&URL=/printers/Canon:i860 HTTP/1.1" 200 0 - -
localhost - sheriff [22/Apr/2007:14:55:21 -0400] "GET /admin/?OP=redirect&URL=/printers/Canon:i860 HTTP/1.1" 200 0 - -
localhost - sheriff [22/Apr/2007:14:55:23 -0400] "GET /printers/Canon:i860 HTTP/1.1" 200 0 - -
localhost - - [22/Apr/2007:14:55:25 -0400] "POST / HTTP/1.1" 200 461 Get-Jobs successful-ok
localhost - sheriff [22/Apr/2007:14:55:23 -0400] "GET /printers/Canon:i860 HTTP/1.1" 200 6325 - -
localhost - sheriff [22/Apr/2007:14:55:33 -0400] "GET /admin/?op=set-printer-options&printer_name=Canon:i860 HTTP/1.1" 200 0 - -
localhost - - [22/Apr/2007:14:55:35 -0400] "GET /ppd/Canon:i860.ppd HTTP/1.1" 200 38680 - -
localhost - sheriff [22/Apr/2007:14:55:33 -0400] "GET /admin/?op=set-printer-options&printer_name=Canon:i860 HTTP/1.1" 200 20498 - -
localhost - sheriff [22/Apr/2007:14:56:47 -0400] "POST /admin HTTP/1.1" 200 528 - -
localhost - - [22/Apr/2007:14:56:49 -0400] "GET /ppd/Canon:i860.ppd HTTP/1.1" 200 38680 - -
localhost - - [22/Apr/2007:14:56:49 -0400] "POST /admin/ HTTP/1.1" 401 39148 CUPS-Add-Modify-Printer successful-ok
localhost - sheriff [22/Apr/2007:14:56:49 -0400] "POST /admin/ HTTP/1.1" 200 39148 CUPS-Add-Modify-Printer successful-ok
localhost - sheriff [22/Apr/2007:14:56:47 -0400] "POST /admin HTTP/1.1" 200 4033 - -
localhost - sheriff [22/Apr/2007:14:56:55 -0400] "GET /admin/?OP=redirect&URL=/printers/Canon:i860 HTTP/1.1" 200 0 - -
localhost - sheriff [22/Apr/2007:14:56:55 -0400] "GET /admin/?OP=redirect&URL=/printers/Canon:i860 HTTP/1.1" 200 0 - -
localhost - sheriff [22/Apr/2007:14:56:57 -0400] "GET /printers/Canon:i860 HTTP/1.1" 200 0 - -
localhost - - [22/Apr/2007:14:56:57 -0400] "POST / HTTP/1.1" 200 461 Get-Jobs successful-ok
localhost - sheriff [22/Apr/2007:14:56:57 -0400] "GET /printers/Canon:i860 HTTP/1.1" 200 6325 - -
localhost - sheriff [22/Apr/2007:14:57:03 -0400] "GET /printers/ HTTP/1.1" 200 0 - -
localhost - sheriff [22/Apr/2007:14:57:03 -0400] "GET /printers/ HTTP/1.1" 200 8940 - -

PAGE_LOG
Brother:HL5250DN sheriff 1 [22/Apr/2007:14:26:07 -0400] 1 1 - localhost
Canon:i860 sheriff 2 [22/Apr/2007:14:42:56 -0400] 1 1 - localhost
Canon:i860 sheriff 3 [22/Apr/2007:14:53:32 -0400] 1 1 - localhost

ERROR_LOG
E [22/Apr/2007:11:34:25 -0400] Creating missing directory "/var/run/cups/certs"
E [22/Apr/2007:13:52:26 -0400] CUPS-Add-Modify-Printer: Unauthorized
E [22/Apr/2007:13:52:54 -0400] CUPS-Add-Modify-Printer: Unauthorized
E [22/Apr/2007:14:09:56 -0400] CUPS-Add-Modify-Printer: Unauthorized
E [22/Apr/2007:14:12:11 -0400] CUPS-Add-Modify-Printer: Unauthorized
E [22/Apr/2007:14:12:52 -0400] CUPS-Delete-Printer: Unauthorized
E [22/Apr/2007:14:25:19 -0400] CUPS-Add-Modify-Printer: Unauthorized
E [22/Apr/2007:14:25:45 -0400] CUPS-Add-Modify-Printer: Unauthorized
E [22/Apr/2007:14:41:24 -0400] CUPS-Add-Modify-Printer: Unauthorized
E [22/Apr/2007:14:42:27 -0400] CUPS-Add-Modify-Printer: Unauthorized
E [22/Apr/2007:14:44:40 -0400] Purge-Jobs: Unauthorized
E [22/Apr/2007:14:46:08 -0400] Purge-Jobs: Unauthorized
E [22/Apr/2007:14:47:06 -0400] CUPS-Set-Default: Unauthorized
E [22/Apr/2007:14:48:17 -0400] CUPS-Reject-Jobs: Unauthorized
E [22/Apr/2007:14:48:37 -0400] Pause-Printer: Unauthorized
E [22/Apr/2007:14:48:58 -0400] Resume-Printer: Unauthorized
E [22/Apr/2007:14:49:14 -0400] CUPS-Accept-Jobs: Unauthorized
E [22/Apr/2007:14:54:00 -0400] PID 5350 (/usr/lib/cups/cgi-bin/admin.cgi) crashed on signal 9!
E [22/Apr/2007:14:55:13 -0400] Purge-Jobs: Unauthorized
E [22/Apr/2007:14:56:49 -0400] CUPS-Add-Modify-Printer: Unauthorized
E [22/Apr/2007:15:06:07 -0400] PID 5060 (/usr/lib/cups/backend/socket) stopped with status 1!

---

