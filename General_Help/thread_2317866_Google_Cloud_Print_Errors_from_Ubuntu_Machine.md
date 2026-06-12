---
title: "Google Cloud Print Errors from Ubuntu Machine"
date: 2016-03-20
forum: General Help
---

### Post by chiques on 2016-03-20
Hello Community,
I have been using Google Cloud Print on a client for a few months. Recently something happened which stopped my Ubuntu machine from being able to install the printers.

Steps Taken:
[LIST=1]
[*]I removed repository and cupscloudprint.py
[*]Reboot System
[*]Installed Updated Repository
[*]Attempted to Reinstall couldprint
[/LIST]

The installation and instructions are from:
[https://www.niftiestsoftware.com/cups-cloud-print/]("https://www.niftiestsoftware.com/cups-cloud-print/")


Below is a capture of the terminal printout:
```

ubuntu-admin@users-linuxstation:~$ sudo /usr/share/cloudprint-cups/setupcloudprint.py
You currently have these accounts configured: 
mygmailacct@gmail.com
Add more accounts (Y/N)? n
Add all Google Cloud Print printers from mygmailacct@gmail.com to CUPS (Y/N)? y
Use a prefix for names of created printers (Y/N)? y
Prefix ( e.g. GCP- )? 
Not using prefix
Error adding: Save_to_Google_Drive (1280, u'server-error-internal-error')
Error adding: Brother_MFC-J470DW_Printer_USB (1280, u'server-error-internal-error')
Error adding: Microsoft_Print_to_PDF (1280, u'server-error-internal-error')
Added 3 new printers to CUPS
ubuntu-admin@users-linuxstation:~$ sudo /usr/share/cloudprint-cups/upgrade.py
Fetching list of available ppds...
List retrieved successfully
ubuntu-admin@users-linuxstation:~$ 

```


As you can see in the prinout, there are errors when attempting to install the Printers. 

Any guidance or suggestions are welcomed.

---

### Post by mickcalcara on 2016-03-26
Having same issue.

---

