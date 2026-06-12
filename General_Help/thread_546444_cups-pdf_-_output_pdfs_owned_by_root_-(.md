---
title: "cups-pdf - output pdfs owned by root :-("
date: 2007-09-08
forum: General Help
---

### Post by mflint on 2007-09-08
Hey all,

I have a problem with 'cups-pdf'. It's installed on a server, and I'm trying to print from another machine. Both are running Ubuntu 7.04.

When I print to the Virtual PDF Printer, the correct PDF appears in the right place, but it's owned by "root". So my non-root user cannot read the file.

The following settings in 'cups-pdf.conf' may be relevant:
```
Out ${HOME}/PDF
UserUMask 0000
#Grp lpadmin
```

I see the following in 'cups-pdf.log':
```
Sun Sep  9 01:37:22 2007  [DEBUG] output file unlinked (/home/matthew/PDF/job_61-Test_Page.pdf)
Sun Sep  9 01:37:22 2007  [DEBUG] TMPDIR set for GhostScript (/var/tmp)
Sun Sep  9 01:37:22 2007  [DEBUG] entering child process
Sun Sep  9 01:37:22 2007  [DEBUG] GID set for current user
Sun Sep  9 01:37:22 2007  [DEBUG] UID set for current user (matthew)
Sun Sep  9 01:37:27 2007  [DEBUG] ghostscript has finished (0)
Sun Sep  9 01:37:27 2007  [ERROR] **failed to set file mode for PDF file (non fatal) (/home/matthew/PDF/job_61-Test_Page.pdf)**
Sun Sep  9 01:37:27 2007  [DEBUG] ERRNO: 1
Sun Sep  9 01:37:22 2007  [DEBUG] waiting for child to exit
Sun Sep  9 01:37:27 2007  [DEBUG] spoolfile unlinked (/var/spool/cups-pdf/SPOOL/cups2pdf-4127)
Sun Sep  9 01:37:27 2007  [DEBUG] all memory has been freed
Sun Sep  9 01:37:27 2007  [STATUS] PDF creation successfully finished (matthew)
```

It looks like cups-pdf knows the correct user ("matthew") but for some reason cannot chown or chmod.

The backend program /usr/lib/cups/backend/cups-pdf is:
```
-rwsr-xr-- 1 root lp 25504 Mar  2  2007 /usr/lib/cups/backend/cups-pdf
```

Has anyone seen this before?

Thanks in advance for any hints...

  Matthew

---

### Post by mflint on 2007-09-08
To answer my own question:

```
sudo apt-get --purge remove cups-pdf cupsys cupsys-common libcupsimage2 libcupsys2
sudo apt-get install cups-pdf
```

I don't know why, but just happy it works now :)

Matthew

---

