---
title: "Broken cups install, unable to get past welcome page."
date: 2015-12-04
forum: General Help
---

### Post by a.grimley on 2015-12-04
[COLOR=#111111][FONT=Ubuntu]I seem to have broken my cups install, I can access [http://localhost:631/](http://localhost:631/) which shows the standard cups welcome page but if I try to visit any other page all that is displayed is "**Not Found**".[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]cups is definitely running (cups start/running, process 842), though I assume if it was not I would not be able to access [http://localhost:631/](http://localhost:631/)[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Any advice?[/FONT][/COLOR]

---

### Post by efflandt on 2015-12-04
I think you might need to be in lpadmin group to use the Administration tab. Other than that, do you have these files (this is in 14.04)?```
efflandt@XPS-8100-1404:~$ ls -l /usr/share/cups/doc-root
total 76
drwxr-xr-x 2 root root  4096 Jun 11 18:43 ca
drwxr-xr-x 2 root root  4096 Jun 11 18:43 cs
-rw-r--r-- 1 root root  7133 Jun  4  2015 cups.css
-rw-r--r-- 1 root root  5097 Jun  4  2015 cups-printable.css
drwxr-xr-x 2 root root  4096 Jun 11 18:43 de
drwxr-xr-x 2 root root  4096 Jun 11 18:43 es
drwxr-xr-x 2 root root  4096 Jun 11 18:43 fr
drwxr-xr-x 2 root root 16384 Jun 11 18:43 help
drwxr-xr-x 2 root root  4096 Jun 11 18:43 images
-rw-r--r-- 1 root root  3784 Jun  4  2015 index.html
drwxr-xr-x 2 root root  4096 Jun 11 18:43 it
drwxr-xr-x 2 root root  4096 Jun 11 18:43 ja
-rw-r--r-- 1 root root   901 Jun  4  2015 robots.txt
drwxr-xr-x 2 root root  4096 Jun 11 18:43 ru

efflandt@XPS-8100-1404:~$ ls /usr/share/cups/doc-root/help
accounting.html       man-filter.html         ppd-compiler.html
api-array.html        man-ipptoolfile.html    raster-driver.html
api-cgi.html          man-ipptool.html        ref-access_log.html
api-cups.html         man-lpadmin.html        ref-classes-conf.html
api-driver.html       man-lpc.html            ref-client-conf.html
api-filedir.html      man-lp.html             ref-cupsd-conf.html
api-filter.html       man-lpinfo.html         ref-cups-files-conf.html
api-httpipp.html      man-lpmove.html         ref-error_log.html
api-mime.html         man-lpoptions.html      ref-mailto-conf.html
api-overview.html     man-lppasswd.html       ref-page_log.html
api-ppdc.html         man-lpq.html            ref-ppdcfile.html
api-ppd.html          man-lpr.html            ref-printers-conf.html
api-raster.html       man-lprm.html           ref-snmp-conf.html
cgi.html              man-lpstat.html         ref-subscriptions-conf.html
glossary.html         man-mime.convs.html     security.html
kerberos.html         man-mime.types.html     sharing.html
license.html          man-notifier.html       spec-banner.html
man-backend.html      man-ppdc.html           spec-cmp.html
man-cancel.html       man-ppdhtml.html        spec-command.html
man-cupsaccept.html   man-ppdi.html           spec-design.html
man-cupsaddsmb.html   man-ppdmerge.html       spec-ipp.html
man-cups-config.html  man-ppdpo.html          spec-pdf.html
man-cupsd.html        network.html            spec-postscript.html
man-cupsenable.html   options.html            spec-ppd.html
man-cups-lpd.html     overview.html           spec-raster.html
man-cups-snmp.html    perqueue.html           spec-stp.html
man-cupstestdsc.html  policies.html           translation.html
man-cupstestppd.html  postscript-driver.html  whatsnew.html
```

---

### Post by a.grimley on 2015-12-07
> **efflandt said:**
> I think you might need to be in lpadmin group to use the Administration tab. Other than that, do you have these files (this is in 14.04)?```
efflandt@XPS-8100-1404:~$ ls -l /usr/share/cups/doc-root
total 76
drwxr-xr-x 2 root root  4096 Jun 11 18:43 ca
drwxr-xr-x 2 root root  4096 Jun 11 18:43 cs
-rw-r--r-- 1 root root  7133 Jun  4  2015 cups.css
-rw-r--r-- 1 root root  5097 Jun  4  2015 cups-printable.css
drwxr-xr-x 2 root root  4096 Jun 11 18:43 de
drwxr-xr-x 2 root root  4096 Jun 11 18:43 es
drwxr-xr-x 2 root root  4096 Jun 11 18:43 fr
drwxr-xr-x 2 root root 16384 Jun 11 18:43 help
drwxr-xr-x 2 root root  4096 Jun 11 18:43 images
-rw-r--r-- 1 root root  3784 Jun  4  2015 index.html
drwxr-xr-x 2 root root  4096 Jun 11 18:43 it
drwxr-xr-x 2 root root  4096 Jun 11 18:43 ja
-rw-r--r-- 1 root root   901 Jun  4  2015 robots.txt
drwxr-xr-x 2 root root  4096 Jun 11 18:43 ru

efflandt@XPS-8100-1404:~$ ls /usr/share/cups/doc-root/help
accounting.html       man-filter.html         ppd-compiler.html
api-array.html        man-ipptoolfile.html    raster-driver.html
api-cgi.html          man-ipptool.html        ref-access_log.html
api-cups.html         man-lpadmin.html        ref-classes-conf.html
api-driver.html       man-lpc.html            ref-client-conf.html
api-filedir.html      man-lp.html             ref-cupsd-conf.html
api-filter.html       man-lpinfo.html         ref-cups-files-conf.html
api-httpipp.html      man-lpmove.html         ref-error_log.html
api-mime.html         man-lpoptions.html      ref-mailto-conf.html
api-overview.html     man-lppasswd.html       ref-page_log.html
api-ppdc.html         man-lpq.html            ref-ppdcfile.html
api-ppd.html          man-lpr.html            ref-printers-conf.html
api-raster.html       man-lprm.html           ref-snmp-conf.html
cgi.html              man-lpstat.html         ref-subscriptions-conf.html
glossary.html         man-mime.convs.html     security.html
kerberos.html         man-mime.types.html     sharing.html
license.html          man-notifier.html       spec-banner.html
man-backend.html      man-ppdc.html           spec-cmp.html
man-cancel.html       man-ppdhtml.html        spec-command.html
man-cupsaccept.html   man-ppdi.html           spec-design.html
man-cupsaddsmb.html   man-ppdmerge.html       spec-ipp.html
man-cups-config.html  man-ppdpo.html          spec-pdf.html
man-cupsd.html        network.html            spec-postscript.html
man-cupsenable.html   options.html            spec-ppd.html
man-cups-lpd.html     overview.html           spec-raster.html
man-cups-snmp.html    perqueue.html           spec-stp.html
man-cupstestdsc.html  policies.html           translation.html
man-cupstestppd.html  postscript-driver.html  whatsnew.html
```

Thanks for the reply.

```
ls -l /usr/share/cups/doc-root
total 72
drwxr-xr-x 2 root root  4096 Nov 18 11:16 ca
drwxr-xr-x 2 root root  4096 Nov 18 11:16 cs
-rw-r--r-- 1 root root  7133 Jun  4  2015 cups.css
-rw-r--r-- 1 root root  5097 Jun  4  2015 cups-printable.css
drwxr-xr-x 2 root root  4096 Nov 18 11:16 de
drwxr-xr-x 2 root root  4096 Nov 18 11:16 es
drwxr-xr-x 2 root root  4096 Nov 18 11:16 fr
drwxr-xr-x 2 root root 12288 Nov 18 11:16 help
drwxr-xr-x 2 root root  4096 Nov 18 11:16 images
-rw-r--r-- 1 root root  3784 Jun  4  2015 index.html
drwxr-xr-x 2 root root  4096 Nov 18 11:16 it
drwxr-xr-x 2 root root  4096 Nov 18 11:16 ja
-rw-r--r-- 1 root root   901 Jun  4  2015 robots.txt
drwxr-xr-x 2 root root  4096 Nov 18 11:16 ru
```

```
ls /usr/share/cups/doc-root/help
accounting.html       man-filter.html         ppd-compiler.html
api-array.html        man-ipptoolfile.html    raster-driver.html
api-cgi.html          man-ipptool.html        ref-access_log.html
api-cups.html         man-lpadmin.html        ref-classes-conf.html
api-driver.html       man-lpc.html            ref-client-conf.html
api-filedir.html      man-lp.html             ref-cupsd-conf.html
api-filter.html       man-lpinfo.html         ref-cups-files-conf.html
api-httpipp.html      man-lpmove.html         ref-error_log.html
api-mime.html         man-lpoptions.html      ref-mailto-conf.html
api-overview.html     man-lppasswd.html       ref-page_log.html
api-ppdc.html         man-lpq.html            ref-ppdcfile.html
api-ppd.html          man-lpr.html            ref-printers-conf.html
api-raster.html       man-lprm.html           ref-snmp-conf.html
cgi.html              man-lpstat.html         ref-subscriptions-conf.html
glossary.html         man-mime.convs.html     security.html
kerberos.html         man-mime.types.html     sharing.html
license.html          man-notifier.html       spec-banner.html
man-backend.html      man-ppdc.html           spec-cmp.html
man-cancel.html       man-ppdhtml.html        spec-command.html
man-cupsaccept.html   man-ppdi.html           spec-design.html
man-cupsaddsmb.html   man-ppdmerge.html       spec-ipp.html
man-cups-config.html  man-ppdpo.html          spec-pdf.html
man-cupsd.html        network.html            spec-postscript.html
man-cupsenable.html   options.html            spec-ppd.html
man-cups-lpd.html     overview.html           spec-raster.html
man-cups-snmp.html    perqueue.html           spec-stp.html
man-cupstestdsc.html  policies.html           translation.html
man-cupstestppd.html  postscript-driver.html  whatsnew.html

```

All of the files seem to exist, and the local account is in the lpadmin group

```
sudo adduser local lpadmin
[sudo] password for local: 
The user `local' is already a member of `lpadmin'.

```

e; version I am running is 14.04.3 LTS, thanks.

---

### Post by a.grimley on 2015-12-11
Any other advice on how I can fix it?

---

### Post by a.grimley on 2015-12-14
Not sure but perhaps there is something in the following which may help.
```

E [14/Dec/2015:08:42:59 +0000] Unknown directive BrowseOrder on line 24 of /etc/cups/cupsd.conf.
E [14/Dec/2015:08:42:59 +0000] Unknown directive BrowseAllow on line 25 of /etc/cups/cupsd.conf.
E [14/Dec/2015:08:42:59 +0000] Unknown browse protocol "CUPS" ignored.
E [14/Dec/2015:08:42:59 +0000] Unknown directive BrowseAddress on line 27 of /etc/cups/cupsd.conf.
W [14/Dec/2015:08:42:59 +0000] No limit for Validate-Job defined in policy default and no suitable template found.
W [14/Dec/2015:08:42:59 +0000] No limit for Cancel-Jobs defined in policy default - using Pause-Printer's policy.
W [14/Dec/2015:08:42:59 +0000] No limit for Cancel-My-Jobs defined in policy default - using Send-Document's policy.
W [14/Dec/2015:08:42:59 +0000] No limit for Close-Job defined in policy default - using Send-Document's policy.
W [14/Dec/2015:08:42:59 +0000] No JobPrivateAccess defined in policy default - using defaults.
W [14/Dec/2015:08:42:59 +0000] No JobPrivateValues defined in policy default - using defaults.
W [14/Dec/2015:08:42:59 +0000] No SubscriptionPrivateAccess defined in policy default - using defaults.
W [14/Dec/2015:08:42:59 +0000] No SubscriptionPrivateValues defined in policy default - using defaults.
W [14/Dec/2015:08:42:59 +0000] No limit for Validate-Job defined in policy authenticated - using Print-Job's policy.
W [14/Dec/2015:08:42:59 +0000] No limit for Cancel-Jobs defined in policy authenticated - using Pause-Printer's policy.
W [14/Dec/2015:08:42:59 +0000] No limit for Cancel-My-Jobs defined in policy authenticated - using Send-Document's policy.
W [14/Dec/2015:08:42:59 +0000] No limit for Close-Job defined in policy authenticated - using Send-Document's policy.
W [14/Dec/2015:08:42:59 +0000] No JobPrivateAccess defined in policy authenticated - using defaults.
W [14/Dec/2015:08:42:59 +0000] No JobPrivateValues defined in policy authenticated - using defaults.
W [14/Dec/2015:08:42:59 +0000] No SubscriptionPrivateAccess defined in policy authenticated - using defaults.
W [14/Dec/2015:08:42:59 +0000] No SubscriptionPrivateValues defined in policy authenticated - using defaults.
E [14/Dec/2015:08:42:59 +0000] Filter "pstops" not found.
E [14/Dec/2015:08:42:59 +0000] Filter "pstops" not found.
E [14/Dec/2015:08:42:59 +0000] Filter "rastertopwg" not found.
E [14/Dec/2015:16:37:52 +0000] File "/usr/lib/cups/cgi-bin/classes.cgi" not available: No such file or directory

```

---

