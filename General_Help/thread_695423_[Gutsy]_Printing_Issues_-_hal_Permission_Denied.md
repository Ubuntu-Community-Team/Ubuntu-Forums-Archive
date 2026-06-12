---
title: "[Gutsy] Printing Issues - hal Permission Denied"
date: 2008-02-13
forum: General Help
---

### Post by unixharuspex on 2008-02-13
Hello all.

I have been working on this for several hours now, and have not had any luck getting my HP Photosmart c4250 working after some recent update.  Initially, foomatic-rip was barfing because of a missing library (libnetsnmp.so.9) for which I created a symlink to so.10.  Next, I changed AppArmor to "complain" for cups.  At this point, cupsys is erroring that hal is not allowing it to open the URI for the blasted printer.

E [12/Feb/2008:22:36:40 -0800] [Job 56] Unable to open device "hal:///org/freedesktop/Hal/devices/usb_device_3f0_5c11_CN7A8NC0K904VP_if1_printer_CN7A8NC0K904VP": Permission denied
E [12/Feb/2008:22:36:40 -0800] PID 6861 (/usr/lib/cups/backend/hal) stopped with status 1!
I [12/Feb/2008:22:36:40 -0800] Hint: Try setting the LogLevel to "debug" to find out more.
E [12/Feb/2008:22:36:41 -0800] PID 6860 (/usr/lib/cups/filter/foomatic-rip) stopped with status 9!
I [12/Feb/2008:22:36:41 -0800] Hint: Try setting the LogLevel to "debug" to find out more.
I [12/Feb/2008:22:36:41 -0800] [Job 56] Backend returned status 1 (failed)
I [12/Feb/2008:22:36:42 -0800] Started "/usr/lib/cups/cgi-bin/printers.cgi" (pid=6877)

This causes all jobs to be in a "held" state when started.

What follows is debug output from my /var/log/cups/error_log file.  I have looked over this and over this, and I am pretty certain that there is a policy change that I need to make in HAL, but I don't have any experience with that.  I hope that someone here can help.  Please let me know if there is any more information that would be useful.


Thanks,
--jacob


I [12/Feb/2008:22:25:04 -0800] Loading NextJobId from job cache file "/var/cache/cups/job.cache"...
I [12/Feb/2008:22:25:04 -0800] Full reload complete.
I [12/Feb/2008:22:25:04 -0800] Cleaning out old temporary files in "/var/spool/cups/tmp"...
I [12/Feb/2008:22:25:04 -0800] Listening to :::631 on fd 3...
I [12/Feb/2008:22:25:04 -0800] Listening to 0.0.0.0:631 on fd 4...
I [12/Feb/2008:22:25:04 -0800] Listening to /var/run/cups/cups.sock on fd 5...
I [12/Feb/2008:22:25:04 -0800] Resuming new connection processing...
I [12/Feb/2008:22:25:04 -0800] [Job 54] Started filter /usr/lib/cups/filter/pstops (PID 6769)
I [12/Feb/2008:22:25:04 -0800] [Job 54] Started filter /usr/lib/cups/filter/foomatic-rip (PID 6771)
I [12/Feb/2008:22:25:04 -0800] [Job 54] Started backend /usr/lib/cups/backend/hal (PID 6772)
E [12/Feb/2008:22:25:04 -0800] [Job 54] Unable to open device "hal:///org/freedesktop/Hal/devices/usb_device_3f0_5c11_CN7A8NC0K904VP_if1_printer_CN7A8NC0K904VP": Permission denied
E [12/Feb/2008:22:25:04 -0800] PID 6772 (/usr/lib/cups/backend/hal) stopped with status 1!
I [12/Feb/2008:22:25:04 -0800] Hint: Try setting the LogLevel to "debug" to find out more.
E [12/Feb/2008:22:25:05 -0800] PID 6771 (/usr/lib/cups/filter/foomatic-rip) stopped with status 9!
I [12/Feb/2008:22:25:05 -0800] Hint: Try setting the LogLevel to "debug" to find out more.
I [12/Feb/2008:22:25:05 -0800] [Job 54] Backend returned status 1 (failed)
I [12/Feb/2008:22:25:15 -0800] Started "/usr/lib/cups/cgi-bin/admin.cgi" (pid=6787)
I [12/Feb/2008:22:25:17 -0800] Started "/usr/lib/cups/cgi-bin/admin.cgi" (pid=6788)
I [12/Feb/2008:22:25:17 -0800] Started "/usr/lib/cups/daemon/cups-deviced" (pid=6789)
I [12/Feb/2008:22:25:21 -0800] Started "/usr/lib/cups/cgi-bin/printers.cgi" (pid=6808)
I [12/Feb/2008:22:25:24 -0800] Started "/usr/lib/cups/cgi-bin/printers.cgi" (pid=6809)
I [12/Feb/2008:22:25:24 -0800] [Job 55] Adding start banner page "none".
I [12/Feb/2008:22:25:24 -0800] [Job 55] Adding job file of type application/postscript.
I [12/Feb/2008:22:25:24 -0800] [Job 55] Adding end banner page "none".
I [12/Feb/2008:22:25:24 -0800] [Job 55] Queued on "HP_Photosmart_C4200_series" by "mike".
I [12/Feb/2008:22:25:24 -0800] [Job 55] Started filter /usr/lib/cups/filter/pstops (PID 6810)
I [12/Feb/2008:22:25:24 -0800] [Job 55] Started filter /usr/lib/cups/filter/foomatic-rip (PID 6811)
I [12/Feb/2008:22:25:24 -0800] [Job 55] Started backend /usr/lib/cups/backend/hal (PID 6812)
E [12/Feb/2008:22:25:24 -0800] [Job 55] Unable to open device "hal:///org/freedesktop/Hal/devices/usb_device_3f0_5c11_CN7A8NC0K904VP_if1_printer_CN7A8NC0K904VP": Permission denied
E [12/Feb/2008:22:25:24 -0800] PID 6812 (/usr/lib/cups/backend/hal) stopped with status 1!
I [12/Feb/2008:22:25:24 -0800] Hint: Try setting the LogLevel to "debug" to find out more.
E [12/Feb/2008:22:25:25 -0800] PID 6811 (/usr/lib/cups/filter/foomatic-rip) stopped with status 9!
I [12/Feb/2008:22:25:25 -0800] Hint: Try setting the LogLevel to "debug" to find out more.
I [12/Feb/2008:22:25:25 -0800] [Job 55] Backend returned status 1 (failed)
I [12/Feb/2008:22:25:26 -0800] Started "/usr/lib/cups/cgi-bin/printers.cgi" (pid=6827)
I [12/Feb/2008:22:25:32 -0800] Started "/usr/lib/cups/cgi-bin/jobs.cgi" (pid=6828)
I [12/Feb/2008:22:25:32 -0800] [Job 54] Canceled by "mike".
I [12/Feb/2008:22:25:37 -0800] Started "/usr/lib/cups/cgi-bin/printers.cgi" (pid=6829)
I [12/Feb/2008:22:25:39 -0800] Started "/usr/lib/cups/cgi-bin/jobs.cgi" (pid=6830)
I [12/Feb/2008:22:25:39 -0800] [Job 55] Canceled by "mike".
I [12/Feb/2008:22:25:44 -0800] Started "/usr/lib/cups/cgi-bin/printers.cgi" (pid=6831)
I [12/Feb/2008:22:36:40 -0800] Started "/usr/lib/cups/cgi-bin/printers.cgi" (pid=6858)
I [12/Feb/2008:22:36:40 -0800] [Job 56] Adding start banner page "none".
I [12/Feb/2008:22:36:40 -0800] [Job 56] Adding job file of type application/postscript.
I [12/Feb/2008:22:36:40 -0800] [Job 56] Adding end banner page "none".
I [12/Feb/2008:22:36:40 -0800] [Job 56] Queued on "HP_Photosmart_C4200_series" by "mike".
I [12/Feb/2008:22:36:40 -0800] [Job 56] Started filter /usr/lib/cups/filter/pstops (PID 6859)
I [12/Feb/2008:22:36:40 -0800] [Job 56] Started filter /usr/lib/cups/filter/foomatic-rip (PID 6860)
I [12/Feb/2008:22:36:40 -0800] [Job 56] Started backend /usr/lib/cups/backend/hal (PID 6861)
E [12/Feb/2008:22:36:40 -0800] [Job 56] Unable to open device "hal:///org/freedesktop/Hal/devices/usb_device_3f0_5c11_CN7A8NC0K904VP_if1_printer_CN7A8NC0K904VP": Permission denied
E [12/Feb/2008:22:36:40 -0800] PID 6861 (/usr/lib/cups/backend/hal) stopped with status 1!
I [12/Feb/2008:22:36:40 -0800] Hint: Try setting the LogLevel to "debug" to find out more.
E [12/Feb/2008:22:36:41 -0800] PID 6860 (/usr/lib/cups/filter/foomatic-rip) stopped with status 9!
I [12/Feb/2008:22:36:41 -0800] Hint: Try setting the LogLevel to "debug" to find out more.
I [12/Feb/2008:22:36:41 -0800] [Job 56] Backend returned status 1 (failed)
I [12/Feb/2008:22:36:42 -0800] Started "/usr/lib/cups/cgi-bin/printers.cgi" (pid=6877)
I [12/Feb/2008:22:38:35 -0800] Started "/usr/lib/cups/cgi-bin/admin.cgi" (pid=6880)
I [12/Feb/2008:22:38:38 -0800] Started "/usr/lib/cups/cgi-bin/admin.cgi" (pid=6882)
I [12/Feb/2008:22:38:38 -0800] Installing config file "/etc/cups/cupsd.conf"...
I [12/Feb/2008:22:38:38 -0800] Loaded configuration file "/etc/cups/cupsd.conf"
N [12/Feb/2008:22:38:38 -0800] Group and SystemGroup cannot use the same groups!
I [12/Feb/2008:22:38:38 -0800] Resetting Group to "root"...
I [12/Feb/2008:22:38:38 -0800] Configured for up to 100 clients.
I [12/Feb/2008:22:38:38 -0800] Allowing up to 100 client connections per host.
I [12/Feb/2008:22:38:38 -0800] Using policy "default" as the default!
I [12/Feb/2008:22:38:38 -0800] Partial reload complete.
I [12/Feb/2008:22:38:38 -0800] Listening to :::631 on fd 3...
I [12/Feb/2008:22:38:38 -0800] Listening to 0.0.0.0:631 on fd 4...
I [12/Feb/2008:22:38:38 -0800] Listening to /var/run/cups/cups.sock on fd 5...
I [12/Feb/2008:22:38:38 -0800] Resuming new connection processing...
D [12/Feb/2008:22:38:43 -0800] cupsdAcceptClient: 9 from localhost:631 (IPv4)
D [12/Feb/2008:22:38:43 -0800] cupsdReadClient: 9 GET /admin/?OP=redirect HTTP/1.1
D [12/Feb/2008:22:38:43 -0800] cupsdAuthorize: Authorized as mike using Basic
D [12/Feb/2008:22:38:43 -0800] [CGI] /usr/lib/cups/cgi-bin/admin.cgi started - PID = 6883
I [12/Feb/2008:22:38:43 -0800] Started "/usr/lib/cups/cgi-bin/admin.cgi" (pid=6883)
D [12/Feb/2008:22:38:43 -0800] cupsdSendCommand: 9 file=10
D [12/Feb/2008:22:38:43 -0800] [CGI] admin.cgi started...
D [12/Feb/2008:22:38:43 -0800] cupsdAcceptClient: 12 from localhost (Domain)
D [12/Feb/2008:22:38:43 -0800] [CGI] http=0x80790d0
D [12/Feb/2008:22:38:43 -0800] [CGI] op="redirect"...
D [12/Feb/2008:22:38:43 -0800] cupsdCloseClient: 12
D [12/Feb/2008:22:38:43 -0800] PID 6883 (/usr/lib/cups/cgi-bin/admin.cgi) exited with no errors.
D [12/Feb/2008:22:38:43 -0800] cupsdReadClient: 9 GET /admin HTTP/1.1
D [12/Feb/2008:22:38:43 -0800] cupsdAuthorize: Authorized as mike using Basic
D [12/Feb/2008:22:38:43 -0800] [CGI] /usr/lib/cups/cgi-bin/admin.cgi started - PID = 6884
I [12/Feb/2008:22:38:43 -0800] Started "/usr/lib/cups/cgi-bin/admin.cgi" (pid=6884)
D [12/Feb/2008:22:38:43 -0800] cupsdSendCommand: 9 file=10
D [12/Feb/2008:22:38:43 -0800] [CGI] admin.cgi started...
D [12/Feb/2008:22:38:43 -0800] cupsdAcceptClient: 12 from localhost (Domain)
D [12/Feb/2008:22:38:43 -0800] [CGI] http=0x80790d0
D [12/Feb/2008:22:38:43 -0800] [CGI] No form data, showing main menu...
D [12/Feb/2008:22:38:43 -0800] [CGI] /usr/share/cups/drivers/pscript5.dll: No such file or directory
D [12/Feb/2008:22:38:43 -0800] cupsdReadClient: 12 POST / HTTP/1.1
D [12/Feb/2008:22:38:43 -0800] cupsdAuthorize: No authentication data provided.
D [12/Feb/2008:22:38:43 -0800] Get-Subscriptions ipp://localhost/
D [12/Feb/2008:22:38:43 -0800] Get-Subscriptions client-error-not-found: No subscriptions found.
D [12/Feb/2008:22:38:43 -0800] cupsdProcessIPPRequest: 12 status_code=406 (client-error-not-found)
D [12/Feb/2008:22:38:43 -0800] [CGI] lang="en_US.UTF-8", locale="/en_US"...
D [12/Feb/2008:22:38:43 -0800] [CGI] lang="en_US.UTF-8", locale="/en_US"...
D [12/Feb/2008:22:38:43 -0800] [CGI] lang="en_US.UTF-8", locale="/en_US"...
D [12/Feb/2008:22:38:43 -0800] cupsdCloseClient: 12
D [12/Feb/2008:22:38:43 -0800] PID 6884 (/usr/lib/cups/cgi-bin/admin.cgi) exited with no errors.
D [12/Feb/2008:22:38:45 -0800] cupsdReadClient: 9 GET /printers/ HTTP/1.1
D [12/Feb/2008:22:38:45 -0800] cupsdAuthorize: Authorized as mike using Basic
D [12/Feb/2008:22:38:45 -0800] [CGI] /usr/lib/cups/cgi-bin/printers.cgi started - PID = 6885
I [12/Feb/2008:22:38:45 -0800] Started "/usr/lib/cups/cgi-bin/printers.cgi" (pid=6885)
D [12/Feb/2008:22:38:45 -0800] cupsdSendCommand: 9 file=10
D [12/Feb/2008:22:38:45 -0800] cupsdAcceptClient: 12 from localhost (Domain)
D [12/Feb/2008:22:38:45 -0800] cupsdReadClient: 12 POST / HTTP/1.1
D [12/Feb/2008:22:38:45 -0800] cupsdAuthorize: No authentication data provided.
D [12/Feb/2008:22:38:45 -0800] CUPS-Get-Default
D [12/Feb/2008:22:38:45 -0800] CUPS-Get-Default client-error-not-found: No default printer
D [12/Feb/2008:22:38:45 -0800] cupsdProcessIPPRequest: 12 status_code=406 (client-error-not-found)
D [12/Feb/2008:22:38:45 -0800] [CGI] show_all_printers(http=0x80761d0, user="mike")
D [12/Feb/2008:22:38:45 -0800] [CGI] lang="en_US.UTF-8", locale="/en_US"...
D [12/Feb/2008:22:38:45 -0800] cupsdReadClient: 12 POST / HTTP/1.1
D [12/Feb/2008:22:38:45 -0800] cupsdAuthorize: No authentication data provided.
D [12/Feb/2008:22:38:45 -0800] CUPS-Get-Printers
D [12/Feb/2008:22:38:45 -0800] cupsdProcessIPPRequest: 12 status_code=0 (successful-ok)
D [12/Feb/2008:22:38:45 -0800] [CGI] lang="en_US.UTF-8", locale="/en_US"...
D [12/Feb/2008:22:38:45 -0800] [CGI] lang="en_US.UTF-8", locale="/en_US"...
D [12/Feb/2008:22:38:45 -0800] [CGI] lang="en_US.UTF-8", locale="/en_US"...
D [12/Feb/2008:22:38:45 -0800] [CGI] lang="en_US.UTF-8", locale="/en_US"...
D [12/Feb/2008:22:38:45 -0800] [CGI] lang="en_US.UTF-8", locale="/en_US"...
D [12/Feb/2008:22:38:45 -0800] [CGI] lang="en_US.UTF-8", locale="/en_US"...
D [12/Feb/2008:22:38:45 -0800] cupsdCloseClient: 12
D [12/Feb/2008:22:38:45 -0800] PID 6885 (/usr/lib/cups/cgi-bin/printers.cgi) exited with no errors.
D [12/Feb/2008:22:38:48 -0800] cupsdReadClient: 9 GET /printers/HP_Photosmart_C4200_series?op=print-test-page HTTP/1.1
D [12/Feb/2008:22:38:48 -0800] cupsdAuthorize: Authorized as mike using Basic
D [12/Feb/2008:22:38:48 -0800] [CGI] /usr/lib/cups/cgi-bin/printers.cgi started - PID = 6886
I [12/Feb/2008:22:38:48 -0800] Started "/usr/lib/cups/cgi-bin/printers.cgi" (pid=6886)
D [12/Feb/2008:22:38:48 -0800] cupsdSendCommand: 9 file=10
D [12/Feb/2008:22:38:48 -0800] cupsdAcceptClient: 12 from localhost (Domain)
D [12/Feb/2008:22:38:48 -0800] cupsdReadClient: 12 POST /printers/HP_Photosmart_C4200_series HTTP/1.1
D [12/Feb/2008:22:38:48 -0800] cupsdAuthorize: No authentication data provided.
D [12/Feb/2008:22:38:48 -0800] Print-Job ipp://localhost:631/printers/HP_Photosmart_C4200_series
D [12/Feb/2008:22:38:48 -0800] add_job: requesting-user-name="mike"
D [12/Feb/2008:22:38:48 -0800] Adding default job-sheets values "none,none"...
I [12/Feb/2008:22:38:48 -0800] [Job 57] Adding start banner page "none".
D [12/Feb/2008:22:38:48 -0800] Discarding unused job-created event...
I [12/Feb/2008:22:38:48 -0800] [Job 57] Adding job file of type application/postscript.
I [12/Feb/2008:22:38:48 -0800] [Job 57] Adding end banner page "none".
I [12/Feb/2008:22:38:48 -0800] [Job 57] Queued on "HP_Photosmart_C4200_series" by "mike".
D [12/Feb/2008:22:38:48 -0800] [Job 57] hold_until = 0
D [12/Feb/2008:22:38:48 -0800] Discarding unused printer-state-changed event...
D [12/Feb/2008:22:38:48 -0800] [Job 57] job-sheets=none,none
D [12/Feb/2008:22:38:48 -0800] [Job 57] banner_page = 0
D [12/Feb/2008:22:38:48 -0800] [Job 57] argv[0]="HP_Photosmart_C4200_series"
D [12/Feb/2008:22:38:48 -0800] [Job 57] argv[1]="57"
D [12/Feb/2008:22:38:48 -0800] [Job 57] argv[2]="mike"
D [12/Feb/2008:22:38:48 -0800] [Job 57] argv[3]="Test Page"
D [12/Feb/2008:22:38:48 -0800] [Job 57] argv[4]="1"
D [12/Feb/2008:22:38:48 -0800] [Job 57] argv[5]="job-uuid=urn:uuid:737f9078-58a9-34e6-7eab-ba8901bc66eb"
D [12/Feb/2008:22:38:48 -0800] [Job 57] argv[6]="/var/spool/cups/d00057-001"
D [12/Feb/2008:22:38:48 -0800] [Job 57] envp[0]="CUPS_CACHEDIR=/var/cache/cups"
D [12/Feb/2008:22:38:48 -0800] [Job 57] envp[1]="CUPS_DATADIR=/usr/share/cups"
D [12/Feb/2008:22:38:48 -0800] [Job 57] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"
D [12/Feb/2008:22:38:48 -0800] [Job 57] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"
D [12/Feb/2008:22:38:48 -0800] [Job 57] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"
D [12/Feb/2008:22:38:48 -0800] [Job 57] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"
D [12/Feb/2008:22:38:48 -0800] [Job 57] envp[6]="CUPS_SERVERROOT=/etc/cups"
D [12/Feb/2008:22:38:48 -0800] [Job 57] envp[7]="CUPS_STATEDIR=/var/run/cups"
D [12/Feb/2008:22:38:48 -0800] [Job 57] envp[8]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"
D [12/Feb/2008:22:38:48 -0800] [Job 57] envp[9]="SERVER_ADMIN=root@mike-desktop"
D [12/Feb/2008:22:38:48 -0800] [Job 57] envp[10]="SOFTWARE=CUPS/1.3.2"
D [12/Feb/2008:22:38:48 -0800] [Job 57] envp[11]="TMPDIR=/var/spool/cups/tmp"
D [12/Feb/2008:22:38:48 -0800] [Job 57] envp[12]="TZ=America/Vancouver"
D [12/Feb/2008:22:38:48 -0800] [Job 57] envp[13]="USER=root"
D [12/Feb/2008:22:38:48 -0800] [Job 57] envp[14]="CUPS_SERVER=/var/run/cups/cups.sock"
D [12/Feb/2008:22:38:48 -0800] [Job 57] envp[15]="CUPS_ENCRYPTION=IfRequested"
D [12/Feb/2008:22:38:48 -0800] [Job 57] envp[16]="IPP_PORT=631"
D [12/Feb/2008:22:38:48 -0800] [Job 57] envp[17]="CHARSET=utf-8"
D [12/Feb/2008:22:38:48 -0800] [Job 57] envp[18]="LANG=en_US"
D [12/Feb/2008:22:38:48 -0800] [Job 57] envp[19]="PPD=/etc/cups/ppd/HP_Photosmart_C4200_series.ppd"
D [12/Feb/2008:22:38:48 -0800] [Job 57] envp[20]="RIP_MAX_CACHE=32m"
D [12/Feb/2008:22:38:48 -0800] [Job 57] envp[21]="CONTENT_TYPE=application/postscript"
D [12/Feb/2008:22:38:48 -0800] [Job 57] envp[22]="DEVICE_URI=hal:///org/freedesktop/Hal/devices/usb_device_3f0_5c11_CN7A8NC0K904VP_if1_printer_CN7A8NC0K904VP"
D [12/Feb/2008:22:38:48 -0800] [Job 57] envp[23]="PRINTER=HP_Photosmart_C4200_series"
D [12/Feb/2008:22:38:48 -0800] [Job 57] envp[24]="FINAL_CONTENT_TYPE=printer/HP_Photosmart_C4200_series"
I [12/Feb/2008:22:38:48 -0800] [Job 57] Started filter /usr/lib/cups/filter/pstops (PID 6887)
I [12/Feb/2008:22:38:48 -0800] [Job 57] Started filter /usr/lib/cups/filter/foomatic-rip (PID 6888)
I [12/Feb/2008:22:38:48 -0800] [Job 57] Started backend /usr/lib/cups/backend/hal (PID 6889)
D [12/Feb/2008:22:38:48 -0800] Discarding unused job-state event...
D [12/Feb/2008:22:38:48 -0800] cupsdProcessIPPRequest: 12 status_code=0 (successful-ok)
D [12/Feb/2008:22:38:48 -0800] PID 6887 (/usr/lib/cups/filter/pstops) exited with no errors.
D [12/Feb/2008:22:38:48 -0800] [Job 57] Page = 612x792; 18,36 to 594,783
D [12/Feb/2008:22:38:48 -0800] [Job 57] slow_collate=0, slow_duplex=0, slow_order=0
D [12/Feb/2008:22:38:48 -0800] [Job 57] Before copy_comments - %!PS-Adobe-3.0
D [12/Feb/2008:22:38:48 -0800] [Job 57] %!PS-Adobe-3.0
D [12/Feb/2008:22:38:48 -0800] [Job 57] %%BoundingBox: 0 0 612 792
D [12/Feb/2008:22:38:48 -0800] [Job 57] %%Pages: 1
D [12/Feb/2008:22:38:48 -0800] [Job 57] %%LanguageLevel: 1
D [12/Feb/2008:22:38:48 -0800] [Job 57] %%DocumentData: Clean7Bit
D [12/Feb/2008:22:38:48 -0800] [Job 57] %%DocumentSuppliedResources: procset testprint/1.3
D [12/Feb/2008:22:38:48 -0800] [Job 57] %%DocumentNeededResources: font Helvetica Helvetica-Bold Times-Roman
D [12/Feb/2008:22:38:48 -0800] [Job 57] %%Creator: Michael Sweet, Apple Inc.
D [12/Feb/2008:22:38:48 -0800] [Job 57] %%CreationDate: D:20070606214000+0500
D [12/Feb/2008:22:38:48 -0800] [Job 57] %%Title: Test Page
D [12/Feb/2008:22:38:48 -0800] [Job 57] %%EndComments
D [12/Feb/2008:22:38:48 -0800] [Job 57] Before copy_prolog - %%BeginProlog
D [12/Feb/2008:22:38:48 -0800] [Job 57] Before copy_setup - %%Page: 1 1
D [12/Feb/2008:22:38:48 -0800] [Job 57] Before page loop - %%Page: 1 1
D [12/Feb/2008:22:38:48 -0800] [Job 57] Copying page 1...
D [12/Feb/2008:22:38:48 -0800] [Job 57] pagew = 576.0, pagel = 747.0
D [12/Feb/2008:22:38:48 -0800] [Job 57] bboxw = 612, bboxl = 792
D [12/Feb/2008:22:38:48 -0800] [Job 57] PageLeft = 18.0, PageRight = 594.0
D [12/Feb/2008:22:38:48 -0800] [Job 57] PageTop = 783.0, PageBottom = 36.0
D [12/Feb/2008:22:38:48 -0800] [Job 57] PageWidth = 612.0, PageLength = 792.0
D [12/Feb/2008:22:38:48 -0800] [Job 57] Wrote 1 pages...
D [12/Feb/2008:22:38:48 -0800] [CGI] lang="en_US.UTF-8", locale="/en_US"...
D [12/Feb/2008:22:38:48 -0800] [Job 57] perl: warning: Setting locale failed.
D [12/Feb/2008:22:38:48 -0800] [Job 57] perl: warning: Please check that your locale settings:
D [12/Feb/2008:22:38:48 -0800] [Job 57] LANGUAGE = (unset),
D [12/Feb/2008:22:38:48 -0800] [Job 57] LC_ALL = (unset),
D [12/Feb/2008:22:38:48 -0800] [Job 57] LANG = "en_US"
D [12/Feb/2008:22:38:48 -0800] [Job 57] are supported and installed on your system.
D [12/Feb/2008:22:38:48 -0800] [Job 57] perl: warning: Falling back to the standard locale ("C").
E [12/Feb/2008:22:38:48 -0800] [Job 57] Unable to open device "hal:///org/freedesktop/Hal/devices/usb_device_3f0_5c11_CN7A8NC0K904VP_if1_printer_CN7A8NC0K904VP": Permission denied
D [12/Feb/2008:22:38:48 -0800] Discarding unused printer-state-changed event...
D [12/Feb/2008:22:38:48 -0800] cupsdCloseClient: 12
D [12/Feb/2008:22:38:48 -0800] cupsdAcceptClient: 12 from localhost (Domain)
D [12/Feb/2008:22:38:48 -0800] PID 6886 (/usr/lib/cups/cgi-bin/printers.cgi) exited with no errors.
E [12/Feb/2008:22:38:48 -0800] PID 6889 (/usr/lib/cups/backend/hal) stopped with status 1!
D [12/Feb/2008:22:38:48 -0800] cupsdReadClient: 12 POST / HTTP/1.1
D [12/Feb/2008:22:38:48 -0800] cupsdAuthorize: No authentication data provided.
D [12/Feb/2008:22:38:48 -0800] Get-Jobs ipp://localhost/jobs/
D [12/Feb/2008:22:38:48 -0800] cupsdProcessIPPRequest: 12 status_code=0 (successful-ok)
D [12/Feb/2008:22:38:48 -0800] [CGI] lang="en_US.UTF-8", locale="/en_US"...
D [12/Feb/2008:22:38:48 -0800] [Job 57] foomatic-rip version $Revision$ running...
D [12/Feb/2008:22:38:48 -0800] [Job 57] Parsing PPD file ...
D [12/Feb/2008:22:38:48 -0800] [Job 57] *cupsFilter: "application/vnd.cups-postscript 0 foomatic-rip"
D [12/Feb/2008:22:38:48 -0800] [Job 57] Added option ColorSpace
D [12/Feb/2008:22:38:48 -0800] [Job 57] Added option Resolution
D [12/Feb/2008:22:38:48 -0800] [Job 57] Added option PageSize
D [12/Feb/2008:22:38:48 -0800] [Job 57] Added option PageRegion
D [12/Feb/2008:22:38:48 -0800] [Job 57] Added option Model
D [12/Feb/2008:22:38:48 -0800] [Job 57] Added option PrintoutMode
D [12/Feb/2008:22:38:48 -0800] [Job 57] Added option InputSlot
D [12/Feb/2008:22:38:48 -0800] [Job 57] Added option ImageableArea
D [12/Feb/2008:22:38:48 -0800] [Job 57] Added option PaperDimension
D [12/Feb/2008:22:38:48 -0800] [Job 57] Added option Duplex
D [12/Feb/2008:22:38:48 -0800] [Job 57] Added option Quality
D [12/Feb/2008:22:38:48 -0800] [Job 57] Added option Font
D [12/Feb/2008:22:38:48 -0800] [Job 57] 
D [12/Feb/2008:22:38:48 -0800] [Job 57] Parameter Summary
D [12/Feb/2008:22:38:48 -0800] [Job 57] -----------------
D [12/Feb/2008:22:38:48 -0800] [Job 57] 
D [12/Feb/2008:22:38:48 -0800] [Job 57] Spooler: cups
D [12/Feb/2008:22:38:48 -0800] [Job 57] Printer: HP_Photosmart_C4200_series
D [12/Feb/2008:22:38:48 -0800] [Job 57] Shell: /bin/bash
D [12/Feb/2008:22:38:48 -0800] [Job 57] PPD file: /etc/cups/ppd/HP_Photosmart_C4200_series.ppd
D [12/Feb/2008:22:38:48 -0800] [Job 57] ATTR file: 
D [12/Feb/2008:22:38:48 -0800] [Job 57] Printer model: HP PhotoSmart C4200 Foomatic/hpijs (recommended) - HPLIP 2.7.7.dfsg.1
D [12/Feb/2008:22:38:48 -0800] [Job 57] Job title: Test Page
D [12/Feb/2008:22:38:48 -0800] [Job 57] File(s) to be printed: 
D [12/Feb/2008:22:38:48 -0800] [Job 57] <STDIN>
D [12/Feb/2008:22:38:48 -0800] [Job 57] 
D [12/Feb/2008:22:38:48 -0800] [Job 57] GhostScript extra search path ('GS_LIB'): /usr/share/cups/fonts
D [12/Feb/2008:22:38:48 -0800] [Job 57] Pondering option 'job-uuid=urn:uuid:737f9078-58a9-34e6-7eab-ba8901bc66eb'
D [12/Feb/2008:22:38:48 -0800] [Job 57] Unknown option job-uuid=urn:uuid:737f9078-58a9-34e6-7eab-ba8901bc66eb.
D [12/Feb/2008:22:38:48 -0800] [Job 57] 
D [12/Feb/2008:22:38:48 -0800] [Job 57] ================================================
D [12/Feb/2008:22:38:48 -0800] [Job 57] 
D [12/Feb/2008:22:38:48 -0800] [Job 57] File: <STDIN>
D [12/Feb/2008:22:38:48 -0800] [Job 57] 
D [12/Feb/2008:22:38:48 -0800] [CGI] lang="en_US.UTF-8", locale="/en_US"...
D [12/Feb/2008:22:38:48 -0800] [Job 57] ================================================
D [12/Feb/2008:22:38:48 -0800] [Job 57] 
D [12/Feb/2008:22:38:48 -0800] [Job 57] Reading PostScript input ...
D [12/Feb/2008:22:38:48 -0800] [Job 57] --> This document is DSC-conforming!
D [12/Feb/2008:22:38:48 -0800] [Job 57] 
D [12/Feb/2008:22:38:48 -0800] [Job 57] -----------
D [12/Feb/2008:22:38:48 -0800] [Job 57] Found: %%BeginProlog
D [12/Feb/2008:22:38:48 -0800] [Job 57] Found: %%EndProlog
D [12/Feb/2008:22:38:48 -0800] [Job 57] 
D [12/Feb/2008:22:38:48 -0800] [Job 57] -----------
D [12/Feb/2008:22:38:48 -0800] [Job 57] Found: %%BeginSetup
D [12/Feb/2008:22:38:48 -0800] [Job 57] Found: %%BeginFeature: *PrintoutMode Normal
D [12/Feb/2008:22:38:48 -0800] [Job 57] Option: PrintoutMode=Normal --> Setting option
D [12/Feb/2008:22:38:48 -0800] [Job 57] Found: %% FoomaticRIPOptionSetting: PrintoutMode=Normal
D [12/Feb/2008:22:38:48 -0800] [Job 57] Option: PrintoutMode=Normal --> Setting option
D [12/Feb/2008:22:38:48 -0800] [Job 57] Found: %%BeginFeature: *InputSlot Default
D [12/Feb/2008:22:38:48 -0800] [Job 57] Option: InputSlot=Default --> Setting option
D [12/Feb/2008:22:38:48 -0800] [Job 57] Found: %% FoomaticRIPOptionSetting: InputSlot=Default
D [12/Feb/2008:22:38:48 -0800] [Job 57] Option: InputSlot=Default --> Setting option
D [12/Feb/2008:22:38:48 -0800] [Job 57] Found: %%BeginFeature: *Quality FromPrintoutMode
D [12/Feb/2008:22:38:48 -0800] [Job 57] Option: Quality=FromPrintoutMode --> Setting option
D [12/Feb/2008:22:38:48 -0800] [Job 57] Found: %% FoomaticRIPOptionSetting: Quality=@PrintoutMode
D [12/Feb/2008:22:38:48 -0800] [Job 57] Option: Quality=FromPrintoutMode --> Setting option
D [12/Feb/2008:22:38:48 -0800] [Job 57] Found: %%BeginFeature: *PageRegion Letter
D [12/Feb/2008:22:38:48 -0800] [Job 57] Option: PageRegion=Letter --> Option will be set by PostScript interpreter
D [12/Feb/2008:22:38:48 -0800] [Job 57] Found: %% FoomaticRIPOptionSetting: PageSize=Letter
D [12/Feb/2008:22:38:48 -0800] [Job 57] Option: PageSize=Letter --> Setting option
D [12/Feb/2008:22:38:48 -0800] [Job 57] Found: %%BeginFeature: *Duplex None
D [12/Feb/2008:22:38:48 -0800] [Job 57] Option: Duplex=None --> Setting option
D [12/Feb/2008:22:38:48 -0800] [Job 57] Found: %% FoomaticRIPOptionSetting: Duplex=None
D [12/Feb/2008:22:38:48 -0800] [Job 57] Option: Duplex=None --> Setting option
D [12/Feb/2008:22:38:48 -0800] [Job 57] Found: %%EndSetup
D [12/Feb/2008:22:38:48 -0800] [Job 57] Inserting PostScript code for CUPS' page accounting
D [12/Feb/2008:22:38:48 -0800] [Job 57] 
D [12/Feb/2008:22:38:48 -0800] [Job 57] -----------
D [12/Feb/2008:22:38:48 -0800] [Job 57] New page:  1 1
D [12/Feb/2008:22:38:48 -0800] [Job 57] Inserting option code into "PageSetup" section.
D [12/Feb/2008:22:38:48 -0800] [Job 57] 
D [12/Feb/2008:22:38:48 -0800] [Job 57] Found: %%BeginPageSetup
D [12/Feb/2008:22:38:48 -0800] [Job 57] Found: %%EndPageSetup
D [12/Feb/2008:22:38:48 -0800] [Job 57] End of page header
D [12/Feb/2008:22:38:48 -0800] [Job 57] Stopping search for page header options
D [12/Feb/2008:22:38:48 -0800] [Job 57] Found:       lineto                             % Move there...
D [12/Feb/2008:22:38:48 -0800] [Job 57] --> Output goes directly to the renderer now.
D [12/Feb/2008:22:38:48 -0800] [Job 57] 
D [12/Feb/2008:22:38:48 -0800] [Job 57] 
D [12/Feb/2008:22:38:48 -0800] [Job 57] Starting renderer
D [12/Feb/2008:22:38:48 -0800] [Job 57] JCL: <job data> 
D [12/Feb/2008:22:38:48 -0800] [Job 57] 
D [12/Feb/2008:22:38:48 -0800] [Job 57] renderer PID kid4=6897
D [12/Feb/2008:22:38:48 -0800] [Job 57] renderer command: gs -q -dBATCH -dPARANOIDSAFER -dQUIET -dNOPAUSE -sDEVICE=ijs -sIjsServer=hpijs -sDeviceManufacturer="HEWLETT-PACKARD" -sDeviceModel="deskjet 5600" -dDEVICEWIDTHPOINTS=612 -dDEVICEHEIGHTPOINTS=792 -dDuplex=false -r300 -sIjsParams=Quality:Quality=0,Quality:ColorMode=2,Quality:MediaType=0,Quality:PenSet=2,PS:MediaPosition=7 -dIjsUseOutputFD -sOutputFile=- -
D [12/Feb/2008:22:38:48 -0800] [Job 57] Found: %%Trailer
D [12/Feb/2008:22:38:48 -0800] [Job 57] --> Continue DSC parsing now.
D [12/Feb/2008:22:38:48 -0800] [Job 57] 
D [12/Feb/2008:22:38:48 -0800] [Job 57] Found: %%Pages: 1
D [12/Feb/2008:22:38:48 -0800] [Job 57] --> Continue DSC parsing now.
D [12/Feb/2008:22:38:48 -0800] [Job 57] 
D [12/Feb/2008:22:38:48 -0800] [Job 57] Found: %%BoundingBox: 0 0 612 792
D [12/Feb/2008:22:38:48 -0800] [Job 57] --> Continue DSC parsing now.
D [12/Feb/2008:22:38:48 -0800] [Job 57] 
D [12/Feb/2008:22:38:48 -0800] [Job 57] Found: %%EOF
D [12/Feb/2008:22:38:48 -0800] [Job 57] --> Continue DSC parsing now.
D [12/Feb/2008:22:38:48 -0800] [Job 57] 
D [12/Feb/2008:22:38:48 -0800] [Job 57] 
D [12/Feb/2008:22:38:48 -0800] [Job 57] Closing renderer
D [12/Feb/2008:22:38:48 -0800] cupsdReadClient: 12 POST / HTTP/1.1
D [12/Feb/2008:22:38:48 -0800] cupsdAuthorize: No authentication data provided.
D [12/Feb/2008:22:38:48 -0800] CUPS-Get-Printers
D [12/Feb/2008:22:38:48 -0800] cupsdProcessIPPRequest: 12 status_code=0 (successful-ok)
D [12/Feb/2008:22:38:48 -0800] cupsdCloseClient: 12
D [12/Feb/2008:22:38:48 -0800] [Job 57] perl: warning: Setting locale failed.
D [12/Feb/2008:22:38:48 -0800] [Job 57] perl: warning: Please check that your locale settings:
D [12/Feb/2008:22:38:48 -0800] [Job 57] LANGUAGE = (unset),
D [12/Feb/2008:22:38:48 -0800] [Job 57] LC_ALL = (unset),
D [12/Feb/2008:22:38:48 -0800] [Job 57] LANG = "en_US"
D [12/Feb/2008:22:38:48 -0800] [Job 57] are supported and installed on your system.
D [12/Feb/2008:22:38:48 -0800] [Job 57] perl: warning: Falling back to the standard locale ("C").
D [12/Feb/2008:22:38:48 -0800] [Job 57] foomatic-gswrapper: gs '-sstdout=%stderr' '-dBATCH' '-dPARANOIDSAFER' '-dQUIET' '-dNOPAUSE' '-sDEVICE=ijs' '-sIjsServer=hpijs' '-sDeviceManufacturer=HEWLETT-PACKARD' '-sDeviceModel=deskjet 5600' '-dDEVICEWIDTHPOINTS=612' '-dDEVICEHEIGHTPOINTS=792' '-dDuplex=false' '-r300' '-sIjsParams=Quality:Quality=0,Quality:ColorMode=2,Quality:MediaType=0,Quality:PenSet=2,PS:MediaPosition=7' '-dIjsUseOutputFD' '-sOutputFile=%stdout' '-'
D [12/Feb/2008:22:38:48 -0800] Discarding unused job-progress event...
D [12/Feb/2008:22:38:49 -0800] cupsdAcceptClient: 12 from localhost (Domain)
D [12/Feb/2008:22:38:49 -0800] cupsdReadClient: 12 POST / HTTP/1.1
D [12/Feb/2008:22:38:49 -0800] cupsdAuthorize: No authentication data provided.
D [12/Feb/2008:22:38:49 -0800] Get-Jobs ipp://localhost/jobs/
D [12/Feb/2008:22:38:49 -0800] cupsdProcessIPPRequest: 12 status_code=0 (successful-ok)
D [12/Feb/2008:22:38:49 -0800] cupsdReadClient: 12 POST / HTTP/1.1
D [12/Feb/2008:22:38:49 -0800] cupsdAuthorize: No authentication data provided.
D [12/Feb/2008:22:38:49 -0800] CUPS-Get-Printers
D [12/Feb/2008:22:38:49 -0800] cupsdProcessIPPRequest: 12 status_code=0 (successful-ok)
D [12/Feb/2008:22:38:49 -0800] cupsdCloseClient: 12
D [12/Feb/2008:22:38:49 -0800] [Job 57] Process dying with "error closing *main::STDOUT", exit stat: 9
D [12/Feb/2008:22:38:49 -0800] [Job 57] error: Broken pipe (32)
D [12/Feb/2008:22:38:49 -0800] [Job 57] error closing *main::STDOUT
D [12/Feb/2008:22:38:49 -0800] [Job 57] KID3 exited with status 0
D [12/Feb/2008:22:38:49 -0800] [Job 57] KID4 exited with status 9
D [12/Feb/2008:22:38:49 -0800] [Job 57] Renderer exit stat: 9
D [12/Feb/2008:22:38:49 -0800] [Job 57] KID3 finished
D [12/Feb/2008:22:38:49 -0800] [Job 57] Renderer process finished
D [12/Feb/2008:22:38:49 -0800] [Job 57] Killing process 6896 (KID3)
D [12/Feb/2008:22:38:49 -0800] [Job 57] Process dying with "Error closing renderer", exit stat: 9
D [12/Feb/2008:22:38:49 -0800] [Job 57] error: Bad file descriptor (9)
D [12/Feb/2008:22:38:49 -0800] [Job 57] Error closing renderer
E [12/Feb/2008:22:38:49 -0800] PID 6888 (/usr/lib/cups/filter/foomatic-rip) stopped with status 9!
D [12/Feb/2008:22:38:49 -0800] [Job 57] File 0 is complete.
I [12/Feb/2008:22:38:49 -0800] [Job 57] Backend returned status 1 (failed)
D [12/Feb/2008:22:38:49 -0800] Discarding unused printer-state-changed event...
D [12/Feb/2008:22:38:49 -0800] set_hold_until: hold_until = 1202885029
D [12/Feb/2008:22:38:49 -0800] Discarding unused job-state event...
D [12/Feb/2008:22:38:50 -0800] cupsdReadClient: 9 GET /printers/HP_Photosmart_C4200_series HTTP/1.1
D [12/Feb/2008:22:38:50 -0800] cupsdAuthorize: Authorized as mike using Basic
D [12/Feb/2008:22:38:50 -0800] [CGI] /usr/lib/cups/cgi-bin/printers.cgi started - PID = 6904
I [12/Feb/2008:22:38:50 -0800] Started "/usr/lib/cups/cgi-bin/printers.cgi" (pid=6904)
D [12/Feb/2008:22:38:50 -0800] cupsdSendCommand: 9 file=12
D [12/Feb/2008:22:38:50 -0800] cupsdAcceptClient: 13 from localhost (Domain)
D [12/Feb/2008:22:38:50 -0800] cupsdReadClient: 13 POST / HTTP/1.1
D [12/Feb/2008:22:38:50 -0800] cupsdAuthorize: No authentication data provided.
D [12/Feb/2008:22:38:50 -0800] CUPS-Get-Default
D [12/Feb/2008:22:38:50 -0800] CUPS-Get-Default client-error-not-found: No default printer
D [12/Feb/2008:22:38:50 -0800] cupsdProcessIPPRequest: 13 status_code=406 (client-error-not-found)
D [12/Feb/2008:22:38:50 -0800] [CGI] show_printer(http=0x80761d0, printer="HP_Photosmart_C4200_series")
D [12/Feb/2008:22:38:50 -0800] cupsdReadClient: 13 POST / HTTP/1.1
D [12/Feb/2008:22:38:50 -0800] cupsdAuthorize: No authentication data provided.
D [12/Feb/2008:22:38:50 -0800] Get-Printer-Attributes ipp://localhost/printers/HP_Photosmart_C4200_series
D [12/Feb/2008:22:38:50 -0800] cupsdProcessIPPRequest: 13 status_code=0 (successful-ok)
D [12/Feb/2008:22:38:50 -0800] [CGI] lang="en_US.UTF-8", locale="/en_US"...
D [12/Feb/2008:22:38:50 -0800] [CGI] lang="en_US.UTF-8", locale="/en_US"...
D [12/Feb/2008:22:38:50 -0800] [CGI] lang="en_US.UTF-8", locale="/en_US"...
D [12/Feb/2008:22:38:50 -0800] cupsdReadClient: 13 POST / HTTP/1.1
D [12/Feb/2008:22:38:50 -0800] cupsdAuthorize: No authentication data provided.
D [12/Feb/2008:22:38:50 -0800] Get-Jobs ipp://localhost:631/printers/HP_Photosmart_C4200_series
D [12/Feb/2008:22:38:50 -0800] cupsdProcessIPPRequest: 13 status_code=0 (successful-ok)
D [12/Feb/2008:22:38:50 -0800] [CGI] lang="en_US.UTF-8", locale="/en_US"...
D [12/Feb/2008:22:38:50 -0800] [CGI] lang="en_US.UTF-8", locale="/en_US"...
D [12/Feb/2008:22:38:50 -0800] [CGI] lang="en_US.UTF-8", locale="/en_US"...
D [12/Feb/2008:22:38:50 -0800] [CGI] lang="en_US.UTF-8", locale="/en_US"...
D [12/Feb/2008:22:38:50 -0800] [CGI] lang="en_US.UTF-8", locale="/en_US"...
D [12/Feb/2008:22:38:50 -0800] [CGI] lang="en_US.UTF-8", locale="/en_US"...
D [12/Feb/2008:22:38:50 -0800] cupsdCloseClient: 13
D [12/Feb/2008:22:38:50 -0800] PID 6904 (/usr/lib/cups/cgi-bin/printers.cgi) exited with no errors.
D [12/Feb/2008:22:38:50 -0800] cupsdAcceptClient: 12 from localhost (Domain)
D [12/Feb/2008:22:38:50 -0800] cupsdReadClient: 12 POST / HTTP/1.1
D [12/Feb/2008:22:38:50 -0800] cupsdAuthorize: No authentication data provided.
D [12/Feb/2008:22:38:50 -0800] Get-Jobs ipp://localhost/jobs/
D [12/Feb/2008:22:38:50 -0800] cupsdProcessIPPRequest: 12 status_code=0 (successful-ok)
D [12/Feb/2008:22:38:50 -0800] cupsdReadClient: 12 POST / HTTP/1.1
D [12/Feb/2008:22:38:50 -0800] cupsdAuthorize: No authentication data provided.
D [12/Feb/2008:22:38:50 -0800] CUPS-Get-Printers
D [12/Feb/2008:22:38:50 -0800] cupsdProcessIPPRequest: 12 status_code=0 (successful-ok)
D [12/Feb/2008:22:38:50 -0800] cupsdCloseClient: 12
D [12/Feb/2008:22:38:53 -0800] cupsdReadClient: 9 GET /jobs/?op=cancel-job&job_id=57&job_printer_uri=/printers/HP_Photosmart_C4200_series HTTP/1.1
D [12/Feb/2008:22:38:53 -0800] cupsdAuthorize: Authorized as mike using Basic
D [12/Feb/2008:22:38:53 -0800] [CGI] /usr/lib/cups/cgi-bin/jobs.cgi started - PID = 6905
I [12/Feb/2008:22:38:53 -0800] Started "/usr/lib/cups/cgi-bin/jobs.cgi" (pid=6905)
D [12/Feb/2008:22:38:53 -0800] cupsdSendCommand: 9 file=12
D [12/Feb/2008:22:38:53 -0800] cupsdAcceptClient: 13 from localhost (Domain)
D [12/Feb/2008:22:38:53 -0800] cupsdReadClient: 13 POST /jobs HTTP/1.1
D [12/Feb/2008:22:38:53 -0800] cupsdAuthorize: No authentication data provided.
D [12/Feb/2008:22:38:53 -0800] Cancel-Job ipp://localhost/jobs/57
D [12/Feb/2008:22:38:53 -0800] Discarding unused job-completed event...
I [12/Feb/2008:22:38:53 -0800] [Job 57] Canceled by "mike".
D [12/Feb/2008:22:38:53 -0800] cupsdProcessIPPRequest: 13 status_code=0 (successful-ok)
D [12/Feb/2008:22:38:53 -0800] [CGI] lang="en_US.UTF-8", locale="/en_US"...
D [12/Feb/2008:22:38:53 -0800] [CGI] lang="en_US.UTF-8", locale="/en_US"...
D [12/Feb/2008:22:38:53 -0800] [CGI] lang="en_US.UTF-8", locale="/en_US"...
D [12/Feb/2008:22:38:53 -0800] cupsdCloseClient: 13
D [12/Feb/2008:22:38:53 -0800] PID 6905 (/usr/lib/cups/cgi-bin/jobs.cgi) exited with no errors.
D [12/Feb/2008:22:38:58 -0800] cupsdReadClient: 9 GET /printers/HP_Photosmart_C4200_series HTTP/1.1
D [12/Feb/2008:22:38:58 -0800] cupsdAuthorize: Authorized as mike using Basic
D [12/Feb/2008:22:38:58 -0800] [CGI] /usr/lib/cups/cgi-bin/printers.cgi started - PID = 6906
I [12/Feb/2008:22:38:58 -0800] Started "/usr/lib/cups/cgi-bin/printers.cgi" (pid=6906)
D [12/Feb/2008:22:38:58 -0800] cupsdSendCommand: 9 file=12
D [12/Feb/2008:22:38:58 -0800] [Job 57] Unloading...
D [12/Feb/2008:22:38:58 -0800] cupsdAcceptClient: 13 from localhost (Domain)
D [12/Feb/2008:22:38:58 -0800] cupsdReadClient: 13 POST / HTTP/1.1
D [12/Feb/2008:22:38:58 -0800] cupsdAuthorize: No authentication data provided.
D [12/Feb/2008:22:38:58 -0800] CUPS-Get-Default
D [12/Feb/2008:22:38:58 -0800] CUPS-Get-Default client-error-not-found: No default printer
D [12/Feb/2008:22:38:58 -0800] cupsdProcessIPPRequest: 13 status_code=406 (client-error-not-found)
D [12/Feb/2008:22:38:58 -0800] [CGI] show_printer(http=0x80761d0, printer="HP_Photosmart_C4200_series")
D [12/Feb/2008:22:38:58 -0800] cupsdReadClient: 13 POST / HTTP/1.1
D [12/Feb/2008:22:38:58 -0800] cupsdAuthorize: No authentication data provided.
D [12/Feb/2008:22:38:58 -0800] Get-Printer-Attributes ipp://localhost/printers/HP_Photosmart_C4200_series
D [12/Feb/2008:22:38:58 -0800] cupsdProcessIPPRequest: 13 status_code=0 (successful-ok)
D [12/Feb/2008:22:38:58 -0800] [CGI] lang="en_US.UTF-8", locale="/en_US"...
D [12/Feb/2008:22:38:58 -0800] [CGI] lang="en_US.UTF-8", locale="/en_US"...
D [12/Feb/2008:22:38:58 -0800] [CGI] lang="en_US.UTF-8", locale="/en_US"...
D [12/Feb/2008:22:38:58 -0800] cupsdReadClient: 13 POST / HTTP/1.1
D [12/Feb/2008:22:38:58 -0800] cupsdAuthorize: No authentication data provided.
D [12/Feb/2008:22:38:58 -0800] Get-Jobs ipp://localhost:631/printers/HP_Photosmart_C4200_series
D [12/Feb/2008:22:38:58 -0800] cupsdProcessIPPRequest: 13 status_code=0 (successful-ok)
D [12/Feb/2008:22:38:58 -0800] [CGI] lang="en_US.UTF-8", locale="/en_US"...
D [12/Feb/2008:22:38:58 -0800] [CGI] lang="en_US.UTF-8", locale="/en_US"...
D [12/Feb/2008:22:38:58 -0800] [CGI] lang="en_US.UTF-8", locale="/en_US"...
D [12/Feb/2008:22:38:58 -0800] [CGI] lang="en_US.UTF-8", locale="/en_US"...
D [12/Feb/2008:22:38:58 -0800] [CGI] lang="en_US.UTF-8", locale="/en_US"...
D [12/Feb/2008:22:38:58 -0800] [CGI] lang="en_US.UTF-8", locale="/en_US"...
D [12/Feb/2008:22:38:58 -0800] cupsdCloseClient: 13
D [12/Feb/2008:22:38:58 -0800] PID 6906 (/usr/lib/cups/cgi-bin/printers.cgi) exited with no errors.

---

### Post by j8a on 2008-04-29
I think we have the same problem, but I did not find the solution yet

D [29/Apr/2008:16:51:39 -0300] cupsdCloseClient: 8
D [29/Apr/2008:16:51:39 -0300] PID 6803 (/usr/lib/cups/daemon/cups-driverd) exited with no errors.
D [29/Apr/2008:16:51:45 -0300] cupsdAcceptClient: 8 from localhost (Domain)
D [29/Apr/2008:16:51:45 -0300] cupsdReadClient: 8 POST /admin/ HTTP/1.1
E [29/Apr/2008:16:51:45 -0300] cupsdAuthorize: Local authentication certificate not found!
D [29/Apr/2008:16:51:45 -0300] CUPS-Add-Modify-Printer ipp://localhost/printers/hp1020
D [29/Apr/2008:16:51:45 -0300] cupsdIsAuthorized: username=""
E [29/Apr/2008:16:51:45 -0300] CUPS-Add-Modify-Printer: Unauthorized
D [29/Apr/2008:16:51:45 -0300] cupsdSendError: 8 code=401 (Unauthorized)
D [29/Apr/2008:16:51:45 -0300] cupsdSendHeader: WWW-Authenticate: Basic realm="CUPS"
D [29/Apr/2008:16:51:45 -0300] cupsdCloseClient: 8
D [29/Apr/2008:16:51:45 -0300] cupsdAcceptClient: 8 from localhost (Domain)
D [29/Apr/2008:16:51:45 -0300] cupsdReadClient: 8 POST /admin/ HTTP/1.1
D [29/Apr/2008:16:51:45 -0300] cupsdAuthorize: Authorized as root using Local
D [29/Apr/2008:16:51:45 -0300] CUPS-Add-Modify-Printer ipp://localhost/printers/hp1020
D [29/Apr/2008:16:51:45 -0300] cupsdIsAuthorized: username="root"
I [29/Apr/2008:16:51:45 -0300] Setting hp1020 device-uri to "smb://192.168.2.244/192.168.2.95/hp1020" (was "smb:///192.168.2.244/192.168.2.95/hp1020".)
I [29/Apr/2008:16:51:45 -0300] Saving printers.conf...
D [29/Apr/2008:16:51:45 -0300] Discarding unused printer-modified event...
I [29/Apr/2008:16:51:45 -0300] Printer "hp1020" modified by "root".
D [29/Apr/2008:16:51:45 -0300] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)
D [29/Apr/2008:16:51:45 -0300] cupsdReadClient: 8 POST / HTTP/1.1
D [29/Apr/2008:16:51:45 -0300] cupsdAuthorize: Authorized as root using Local
D [29/Apr/2008:16:51:45 -0300] CUPS-Get-Printers
D [29/Apr/2008:16:51:45 -0300] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)
D [29/Apr/2008:16:51:45 -0300] cupsdReadClient: 8 POST / HTTP/1.1
D [29/Apr/2008:16:51:45 -0300] cupsdAuthorize: Authorized as root using Local
D [29/Apr/2008:16:51:45 -0300] CUPS-Get-Classes
D [29/Apr/2008:16:51:45 -0300] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)
D [29/Apr/2008:16:51:45 -0300] cupsdReadClient: 8 POST / HTTP/1.1
D [29/Apr/2008:16:51:45 -0300] cupsdAuthorize: Authorized as root using Local
D [29/Apr/2008:16:51:45 -0300] Get-Printer-Attributes ipp://localhost/printers/hp1020
D [29/Apr/2008:16:51:45 -0300] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)
D [29/Apr/2008:16:51:45 -0300] cupsdReadClient: 8 GET /admin/conf/printers.conf HTTP/1.1
D [29/Apr/2008:16:51:45 -0300] cupsdAuthorize: Authorized as root using Local
D [29/Apr/2008:16:51:45 -0300] cupsdIsAuthorized: username="root"
D [29/Apr/2008:16:51:45 -0300] cupsdReadClient: 8 POST / HTTP/1.1
D [29/Apr/2008:16:51:45 -0300] cupsdAuthorize: Authorized as root using Local
D [29/Apr/2008:16:51:45 -0300] Get-Printer-Attributes ipp://localhost/printers/DeskJet
D [29/Apr/2008:16:51:45 -0300] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)
D [29/Apr/2008:16:51:46 -0300] cupsdAcceptClient: 9 from localhost (Domain)
D [29/Apr/2008:16:51:46 -0300] cupsdReadClient: 9 POST / HTTP/1.1
D [29/Apr/2008:16:51:46 -0300] cupsdAuthorize: No authentication data provided.
D [29/Apr/2008:16:51:46 -0300] Get-Jobs ipp://localhost/jobs/
D [29/Apr/2008:16:51:46 -0300] cupsdProcessIPPRequest: 9 status_code=0 (successful-ok)
D [29/Apr/2008:16:51:46 -0300] cupsdReadClient: 9 POST / HTTP/1.1
D [29/Apr/2008:16:51:46 -0300] cupsdAuthorize: No authentication data provided.
D [29/Apr/2008:16:51:46 -0300] CUPS-Get-Printers
D [29/Apr/2008:16:51:46 -0300] cupsdProcessIPPRequest: 9 status_code=0 (successful-ok)
D [29/Apr/2008:16:51:46 -0300] cupsdCloseClient: 9
D [29/Apr/2008:16:51:48 -0300] cupsdReadClient: 8 POST / HTTP/1.1
D [29/Apr/2008:16:51:48 -0300] cupsdAuthorize: Authorized as root using Local
D [29/Apr/2008:16:51:48 -0300] Get-Printer-Attributes ipp://localhost/printers/hp1020
D [29/Apr/2008:16:51:48 -0300] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)
D [29/Apr/2008:16:51:48 -0300] cupsdReadClient: 8 GET /printers/hp1020.ppd HTTP/1.1
D [29/Apr/2008:16:51:48 -0300] cupsdAuthorize: Authorized as root using Local
D [29/Apr/2008:16:51:48 -0300] cupsdReadClient: 8 POST / HTTP/1.1
D [29/Apr/2008:16:51:48 -0300] cupsdAuthorize: Authorized as root using Local
D [29/Apr/2008:16:51:48 -0300] Get-Jobs ipp://localhost/jobs/
D [29/Apr/2008:16:51:48 -0300] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)
D [29/Apr/2008:16:52:07 -0300] cupsdAcceptClient: 9 from localhost:631 (IPv4)
D [29/Apr/2008:16:52:07 -0300] cupsdReadClient: 9 GET /printers/ HTTP/1.1
D [29/Apr/2008:16:52:07 -0300] cupsdAuthorize: Authorized as jochoa using Basic
D [29/Apr/2008:16:52:07 -0300] [CGI] /usr/lib/cups/cgi-bin/printers.cgi started - PID = 6813
I [29/Apr/2008:16:52:07 -0300] Started "/usr/lib/cups/cgi-bin/printers.cgi" (pid=6813)
D [29/Apr/2008:16:52:07 -0300] cupsdSendCommand: 9 file=11
D [29/Apr/2008:16:52:07 -0300] cupsdAcceptClient: 13 from localhost (Domain)
D [29/Apr/2008:16:52:07 -0300] cupsdReadClient: 13 POST / HTTP/1.1
D [29/Apr/2008:16:52:07 -0300] cupsdAuthorize: No authentication data provided.
D [29/Apr/2008:16:52:07 -0300] CUPS-Get-Default
D [29/Apr/2008:16:52:07 -0300] cupsdProcessIPPRequest: 13 status_code=0 (successful-ok)
D [29/Apr/2008:16:52:08 -0300] [CGI] show_all_printers(http=0x80761d0, user="jochoa")
D [29/Apr/2008:16:52:08 -0300] [CGI] lang="en_US.UTF-8", locale="/en_US"...
D [29/Apr/2008:16:52:08 -0300] cupsdReadClient: 13 POST / HTTP/1.1
D [29/Apr/2008:16:52:08 -0300] cupsdAuthorize: No authentication data provided.
D [29/Apr/2008:16:52:08 -0300] CUPS-Get-Printers
D [29/Apr/2008:16:52:08 -0300] cupsdProcessIPPRequest: 13 status_code=0 (successful-ok)
D [29/Apr/2008:16:52:08 -0300] [CGI] lang="en_US.UTF-8", locale="/en_US"...
D [29/Apr/2008:16:52:08 -0300] [CGI] lang="en_US.UTF-8", locale="/en_US"...
D [29/Apr/2008:16:52:08 -0300] [CGI] lang="en_US.UTF-8", locale="/en_US"...
D [29/Apr/2008:16:52:08 -0300] [CGI] lang="en_US.UTF-8", locale="/en_US"...
D [29/Apr/2008:16:52:08 -0300] [CGI] lang="en_US.UTF-8", locale="/en_US"...
D [29/Apr/2008:16:52:08 -0300] [CGI] lang="en_US.UTF-8", locale="/en_US"...
D [29/Apr/2008:16:52:08 -0300] cupsdCloseClient: 13
D [29/Apr/2008:16:52:08 -0300] PID 6813 (/usr/lib/cups/cgi-bin/printers.cgi) exited with no errors.
D [29/Apr/2008:16:52:20 -0300] cupsdReadClient: 9 GET /admin HTTP/1.1
D [29/Apr/2008:16:52:20 -0300] cupsdAuthorize: Authorized as jochoa using Basic
D [29/Apr/2008:16:52:20 -0300] [CGI] /usr/lib/cups/cgi-bin/admin.cgi started - PID = 6815
I [29/Apr/2008:16:52:20 -0300] Started "/usr/lib/cups/cgi-bin/admin.cgi" (pid=6815)
D [29/Apr/2008:16:52:20 -0300] cupsdSendCommand: 9 file=11
D [29/Apr/2008:16:52:20 -0300] [CGI] admin.cgi started...
D [29/Apr/2008:16:52:20 -0300] cupsdAcceptClient: 13 from localhost (Domain)
D [29/Apr/2008:16:52:20 -0300] [CGI] http=0x80790d0
D [29/Apr/2008:16:52:20 -0300] [CGI] No form data, showing main menu...
D [29/Apr/2008:16:52:20 -0300] [CGI] /usr/share/cups/drivers/pscript5.dll: No such file or directory
D [29/Apr/2008:16:52:20 -0300] cupsdReadClient: 13 POST / HTTP/1.1
D [29/Apr/2008:16:52:20 -0300] cupsdAuthorize: No authentication data provided.
D [29/Apr/2008:16:52:20 -0300] Get-Subscriptions ipp://localhost/
D [29/Apr/2008:16:52:20 -0300] Get-Subscriptions client-error-not-found: No subscriptions found.
D [29/Apr/2008:16:52:20 -0300] cupsdProcessIPPRequest: 13 status_code=406 (client-error-not-found)
D [29/Apr/2008:16:52:20 -0300] [CGI] lang="en_US.UTF-8", locale="/en_US"...
D [29/Apr/2008:16:52:21 -0300] [CGI] lang="en_US.UTF-8", locale="/en_US"...
D [29/Apr/2008:16:52:21 -0300] [CGI] lang="en_US.UTF-8", locale="/en_US"...
D [29/Apr/2008:16:52:21 -0300] cupsdCloseClient: 13
D [29/Apr/2008:16:52:21 -0300] PID 6815 (/usr/lib/cups/cgi-bin/admin.cgi) exited with no errors.
D [29/Apr/2008:16:52:26 -0300] cupsdReadClient: 9 GET /printers/ HTTP/1.1
D [29/Apr/2008:16:52:26 -0300] cupsdAuthorize: Authorized as jochoa using Basic
D [29/Apr/2008:16:52:26 -0300] [CGI] /usr/lib/cups/cgi-bin/printers.cgi started - PID = 6816
I [29/Apr/2008:16:52:26 -0300] Started "/usr/lib/cups/cgi-bin/printers.cgi" (pid=6816)
D [29/Apr/2008:16:52:26 -0300] cupsdSendCommand: 9 file=11
D [29/Apr/2008:16:52:26 -0300] cupsdAcceptClient: 13 from localhost (Domain)
D [29/Apr/2008:16:52:26 -0300] cupsdReadClient: 13 POST / HTTP/1.1
D [29/Apr/2008:16:52:26 -0300] cupsdAuthorize: No authentication data provided.
D [29/Apr/2008:16:52:26 -0300] CUPS-Get-Default
D [29/Apr/2008:16:52:26 -0300] cupsdProcessIPPRequest: 13 status_code=0 (successful-ok)
D [29/Apr/2008:16:52:26 -0300] [CGI] show_all_printers(http=0x80761d0, user="jochoa")
D [29/Apr/2008:16:52:26 -0300] [CGI] lang="en_US.UTF-8", locale="/en_US"...
D [29/Apr/2008:16:52:26 -0300] cupsdReadClient: 13 POST / HTTP/1.1
D [29/Apr/2008:16:52:26 -0300] cupsdAuthorize: No authentication data provided.
D [29/Apr/2008:16:52:26 -0300] CUPS-Get-Printers
D [29/Apr/2008:16:52:26 -0300] cupsdProcessIPPRequest: 13 status_code=0 (successful-ok)
D [29/Apr/2008:16:52:26 -0300] [CGI] lang="en_US.UTF-8", locale="/en_US"...
D [29/Apr/2008:16:52:26 -0300] [CGI] lang="en_US.UTF-8", locale="/en_US"...
D [29/Apr/2008:16:52:26 -0300] [CGI] lang="en_US.UTF-8", locale="/en_US"...
D [29/Apr/2008:16:52:26 -0300] [CGI] lang="en_US.UTF-8", locale="/en_US"...
D [29/Apr/2008:16:52:28 -0300] [CGI] lang="en_US.UTF-8", locale="/en_US"...
D [29/Apr/2008:16:52:28 -0300] [CGI] lang="en_US.UTF-8", locale="/en_US"...
D [29/Apr/2008:16:52:28 -0300] cupsdCloseClient: 13
D [29/Apr/2008:16:52:29 -0300] PID 6816 (/usr/lib/cups/cgi-bin/printers.cgi) exited with no errors.
D [29/Apr/2008:16:52:33 -0300] cupsdReadClient: 9 GET /printers/hp1020?op=print-test-page HTTP/1.1
D [29/Apr/2008:16:52:33 -0300] cupsdAuthorize: Authorized as jochoa using Basic
D [29/Apr/2008:16:52:33 -0300] [CGI] /usr/lib/cups/cgi-bin/printers.cgi started - PID = 6817
I [29/Apr/2008:16:52:33 -0300] Started "/usr/lib/cups/cgi-bin/printers.cgi" (pid=6817)
D [29/Apr/2008:16:52:33 -0300] cupsdSendCommand: 9 file=11
D [29/Apr/2008:16:52:33 -0300] cupsdAcceptClient: 13 from localhost (Domain)
D [29/Apr/2008:16:52:33 -0300] cupsdReadClient: 13 POST /printers/hp1020 HTTP/1.1
D [29/Apr/2008:16:52:33 -0300] cupsdAuthorize: No authentication data provided.
D [29/Apr/2008:16:52:33 -0300] Print-Job ipp://localhost:631/printers/hp1020
D [29/Apr/2008:16:52:33 -0300] add_job: requesting-user-name="jochoa"
D [29/Apr/2008:16:52:33 -0300] Adding default job-sheets values "none,none"...
I [29/Apr/2008:16:52:33 -0300] [Job 91] Adding start banner page "none".
D [29/Apr/2008:16:52:33 -0300] Discarding unused job-created event...
I [29/Apr/2008:16:52:33 -0300] [Job 91] Adding job file of type application/postscript.
I [29/Apr/2008:16:52:33 -0300] [Job 91] Adding end banner page "none".
I [29/Apr/2008:16:52:33 -0300] [Job 91] Queued on "hp1020" by "jochoa".
D [29/Apr/2008:16:52:33 -0300] [Job 91] hold_until = 0
D [29/Apr/2008:16:52:33 -0300] Discarding unused printer-state-changed event...
D [29/Apr/2008:16:52:33 -0300] [Job 91] job-sheets=none,none
D [29/Apr/2008:16:52:33 -0300] [Job 91] banner_page = 0
D [29/Apr/2008:16:52:33 -0300] [Job 91] argv[0]="hp1020"
D [29/Apr/2008:16:52:33 -0300] [Job 91] argv[1]="91"
D [29/Apr/2008:16:52:33 -0300] [Job 91] argv[2]="jochoa"
D [29/Apr/2008:16:52:33 -0300] [Job 91] argv[3]="Test Page"
D [29/Apr/2008:16:52:33 -0300] [Job 91] argv[4]="1"
D [29/Apr/2008:16:52:33 -0300] [Job 91] argv[5]="job-uuid=urn:uuid:65ca67fe-b2b3-316f-617a-d270c64fc47f"
D [29/Apr/2008:16:52:33 -0300] [Job 91] argv[6]="/var/spool/cups/d00091-001"
D [29/Apr/2008:16:52:33 -0300] [Job 91] envp[0]="CUPS_CACHEDIR=/var/cache/cups"
D [29/Apr/2008:16:52:33 -0300] [Job 91] envp[1]="CUPS_DATADIR=/usr/share/cups"
D [29/Apr/2008:16:52:33 -0300] [Job 91] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"
D [29/Apr/2008:16:52:33 -0300] [Job 91] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"
D [29/Apr/2008:16:52:33 -0300] [Job 91] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"
D [29/Apr/2008:16:52:33 -0300] [Job 91] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"
D [29/Apr/2008:16:52:33 -0300] [Job 91] envp[6]="CUPS_SERVERROOT=/etc/cups"
D [29/Apr/2008:16:52:33 -0300] [Job 91] envp[7]="CUPS_STATEDIR=/var/run/cups"
D [29/Apr/2008:16:52:33 -0300] [Job 91] envp[8]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"
D [29/Apr/2008:16:52:33 -0300] [Job 91] envp[9]="SERVER_ADMIN=root@(none)"
D [29/Apr/2008:16:52:33 -0300] [Job 91] envp[10]="SOFTWARE=CUPS/1.3.2"
D [29/Apr/2008:16:52:33 -0300] [Job 91] envp[11]="TMPDIR=/var/spool/cups/tmp"
D [29/Apr/2008:16:52:33 -0300] [Job 91] envp[12]="TZ=America/Argentina/Tucuman"
D [29/Apr/2008:16:52:33 -0300] [Job 91] envp[13]="USER=root"
D [29/Apr/2008:16:52:33 -0300] [Job 91] envp[14]="CUPS_SERVER=/var/run/cups/cups.sock"
D [29/Apr/2008:16:52:33 -0300] [Job 91] envp[15]="CUPS_ENCRYPTION=IfRequested"
D [29/Apr/2008:16:52:33 -0300] [Job 91] envp[16]="IPP_PORT=631"
D [29/Apr/2008:16:52:33 -0300] [Job 91] envp[17]="CHARSET=utf-8"
D [29/Apr/2008:16:52:33 -0300] [Job 91] envp[18]="LANG=en_US"
D [29/Apr/2008:16:52:33 -0300] [Job 91] envp[19]="PPD=/etc/cups/ppd/hp1020.ppd"
D [29/Apr/2008:16:52:33 -0300] [Job 91] envp[20]="RIP_MAX_CACHE=8m"
D [29/Apr/2008:16:52:33 -0300] [Job 91] envp[21]="CONTENT_TYPE=application/postscript"
D [29/Apr/2008:16:52:33 -0300] [Job 91] envp[22]="DEVICE_URI=smb://192.168.2.244/192.168.2.95/hp1020"
D [29/Apr/2008:16:52:33 -0300] [Job 91] envp[23]="PRINTER=hp1020"
D [29/Apr/2008:16:52:33 -0300] [Job 91] envp[24]="FINAL_CONTENT_TYPE=printer/hp1020"
I [29/Apr/2008:16:52:33 -0300] [Job 91] Started filter /usr/lib/cups/filter/pstops (PID 6818)
I [29/Apr/2008:16:52:33 -0300] [Job 91] Started filter /usr/lib/cups/filter/foomatic-rip (PID 6819)
I [29/Apr/2008:16:52:33 -0300] [Job 91] Started backend /usr/lib/cups/backend/smb (PID 6820)
D [29/Apr/2008:16:52:33 -0300] Discarding unused job-state event...
D [29/Apr/2008:16:52:33 -0300] cupsdProcessIPPRequest: 13 status_code=0 (successful-ok)
D [29/Apr/2008:16:52:33 -0300] PID 6818 (/usr/lib/cups/filter/pstops) exited with no errors.
D [29/Apr/2008:16:52:33 -0300] cupsdAcceptClient: 14 from localhost (Domain)
D [29/Apr/2008:16:52:33 -0300] [Job 91] Page = 595x842; 11,11 to 584,831
D [29/Apr/2008:16:52:33 -0300] [Job 91] slow_collate=0, slow_duplex=0, slow_order=0
D [29/Apr/2008:16:52:33 -0300] [Job 91] Before copy_comments - %!PS-Adobe-3.0
D [29/Apr/2008:16:52:33 -0300] [Job 91] %!PS-Adobe-3.0
D [29/Apr/2008:16:52:33 -0300] [Job 91] %%BoundingBox: 0 0 612 792
D [29/Apr/2008:16:52:33 -0300] [Job 91] %%Pages: 1
D [29/Apr/2008:16:52:33 -0300] [Job 91] %%LanguageLevel: 1
D [29/Apr/2008:16:52:33 -0300] [Job 91] %%DocumentData: Clean7Bit
D [29/Apr/2008:16:52:33 -0300] [Job 91] %%DocumentSuppliedResources: procset testprint/1.3
D [29/Apr/2008:16:52:33 -0300] [Job 91] %%DocumentNeededResources: font Helvetica Helvetica-Bold Times-Roman
D [29/Apr/2008:16:52:33 -0300] [Job 91] %%Creator: Michael Sweet, Apple Inc.
D [29/Apr/2008:16:52:33 -0300] [Job 91] %%CreationDate: D:20070606214000+0500
D [29/Apr/2008:16:52:33 -0300] [Job 91] %%Title: Test Page
D [29/Apr/2008:16:52:33 -0300] [Job 91] %%EndComments
D [29/Apr/2008:16:52:33 -0300] [Job 91] Before copy_prolog - %%BeginProlog
D [29/Apr/2008:16:52:33 -0300] [Job 91] Before copy_setup - %%Page: 1 1
D [29/Apr/2008:16:52:33 -0300] [Job 91] Before page loop - %%Page: 1 1
D [29/Apr/2008:16:52:33 -0300] [Job 91] Copying page 1...
D [29/Apr/2008:16:52:33 -0300] [Job 91] pagew = 572.3, pagel = 819.3
D [29/Apr/2008:16:52:33 -0300] [Job 91] bboxw = 595, bboxl = 842
D [29/Apr/2008:16:52:33 -0300] [Job 91] PageLeft = 11.3, PageRight = 583.7
D [29/Apr/2008:16:52:33 -0300] [Job 91] PageTop = 830.7, PageBottom = 11.3
D [29/Apr/2008:16:52:33 -0300] [Job 91] PageWidth = 595.0, PageLength = 842.0
D [29/Apr/2008:16:52:33 -0300] [Job 91] Wrote 1 pages...
D [29/Apr/2008:16:52:33 -0300] cupsdReadClient: 14 POST / HTTP/1.1
D [29/Apr/2008:16:52:33 -0300] cupsdAuthorize: No authentication data provided.
D [29/Apr/2008:16:52:33 -0300] Get-Jobs ipp://localhost/jobs/
D [29/Apr/2008:16:52:33 -0300] cupsdProcessIPPRequest: 14 status_code=0 (successful-ok)
D [29/Apr/2008:16:52:33 -0300] cupsdReadClient: 14 POST / HTTP/1.1
D [29/Apr/2008:16:52:33 -0300] cupsdAuthorize: No authentication data provided.
D [29/Apr/2008:16:52:33 -0300] CUPS-Get-Printers
D [29/Apr/2008:16:52:33 -0300] cupsdProcessIPPRequest: 14 status_code=0 (successful-ok)
D [29/Apr/2008:16:52:33 -0300] cupsdCloseClient: 14
D [29/Apr/2008:16:52:33 -0300] [Job 91] perl: warning: Setting locale failed.
D [29/Apr/2008:16:52:33 -0300] [Job 91] perl: warning: Please check that your locale settings:
D [29/Apr/2008:16:52:33 -0300] [Job 91] LANGUAGE = (unset),
D [29/Apr/2008:16:52:33 -0300] [Job 91] LC_ALL = (unset),
D [29/Apr/2008:16:52:33 -0300] [Job 91] LANG = "en_US"
D [29/Apr/2008:16:52:33 -0300] [Job 91] are supported and installed on your system.
D [29/Apr/2008:16:52:33 -0300] [Job 91] perl: warning: Falling back to the standard locale ("C").
D [29/Apr/2008:16:52:33 -0300] [CGI] lang="en_US.UTF-8", locale="/en_US"...
D [29/Apr/2008:16:52:33 -0300] cupsdCloseClient: 13
D [29/Apr/2008:16:52:33 -0300] PID 6817 (/usr/lib/cups/cgi-bin/printers.cgi) exited with no errors.
D [29/Apr/2008:16:52:34 -0300] [CGI] lang="en_US.UTF-8", locale="/en_US"...
D [29/Apr/2008:16:52:34 -0300] [CGI] lang="en_US.UTF-8", locale="/en_US"...
D [29/Apr/2008:16:52:35 -0300] cupsdAcceptClient: 11 from localhost (Domain)
D [29/Apr/2008:16:52:35 -0300] cupsdReadClient: 11 POST / HTTP/1.1
D [29/Apr/2008:16:52:35 -0300] cupsdAuthorize: No authentication data provided.
D [29/Apr/2008:16:52:35 -0300] Get-Jobs ipp://localhost/jobs/
D [29/Apr/2008:16:52:35 -0300] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)
D [29/Apr/2008:16:52:35 -0300] cupsdReadClient: 11 POST / HTTP/1.1
D [29/Apr/2008:16:52:35 -0300] cupsdAuthorize: No authentication data provided.
D [29/Apr/2008:16:52:35 -0300] CUPS-Get-Printers
D [29/Apr/2008:16:52:35 -0300] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)
D [29/Apr/2008:16:52:35 -0300] cupsdCloseClient: 11
D [29/Apr/2008:16:52:36 -0300] [Job 91] foomatic-rip version $Revision$ running...
D [29/Apr/2008:16:52:36 -0300] [Job 91] Parsing PPD file ...
D [29/Apr/2008:16:52:36 -0300] [Job 91] *cupsFilter: "application/vnd.cups-postscript 0 foomatic-rip"
D [29/Apr/2008:16:52:36 -0300] [Job 91] Added option ColorSpace
D [29/Apr/2008:16:52:36 -0300] [Job 91] Added option PageSize
D [29/Apr/2008:16:52:36 -0300] [Job 91] Added option PageRegion
D [29/Apr/2008:16:52:36 -0300] [Job 91] Added option ImageableArea
D [29/Apr/2008:16:52:36 -0300] [Job 91] Added option PaperDimension
D [29/Apr/2008:16:52:36 -0300] [Job 91] Added option InputSlot
D [29/Apr/2008:16:52:36 -0300] [Job 91] Added option MediaType
D [29/Apr/2008:16:52:36 -0300] [Job 91] Added option Resolution
D [29/Apr/2008:16:52:36 -0300] [Job 91] Added option Quality
D [29/Apr/2008:16:52:36 -0300] [Job 91] Added option ColorMode
D [29/Apr/2008:16:52:36 -0300] [Job 91] Added option Copies
D [29/Apr/2008:16:52:36 -0300] [Job 91] Added option PrinterType
D [29/Apr/2008:16:52:36 -0300] [Job 91] Added option Nup
D [29/Apr/2008:16:52:36 -0300] [Job 91] Added option NupOrient
D [29/Apr/2008:16:52:36 -0300] [Job 91] Added option Font
D [29/Apr/2008:16:52:36 -0300] [Job 91] 
D [29/Apr/2008:16:52:36 -0300] [Job 91] Parameter Summary
D [29/Apr/2008:16:52:36 -0300] [Job 91] -----------------
D [29/Apr/2008:16:52:36 -0300] [Job 91] 
D [29/Apr/2008:16:52:36 -0300] [Job 91] Spooler: cups
D [29/Apr/2008:16:52:36 -0300] [Job 91] Printer: hp1020
D [29/Apr/2008:16:52:36 -0300] [Job 91] Shell: /bin/bash
D [29/Apr/2008:16:52:36 -0300] [Job 91] PPD file: /etc/cups/ppd/hp1020.ppd
D [29/Apr/2008:16:52:36 -0300] [Job 91] ATTR file: 
D [29/Apr/2008:16:52:36 -0300] [Job 91] Printer model: HP LaserJet 1020 Foomatic/foo2zjs (recommended)
D [29/Apr/2008:16:52:36 -0300] [Job 91] Job title: Test Page
D [29/Apr/2008:16:52:36 -0300] [Job 91] File(s) to be printed: 
D [29/Apr/2008:16:52:36 -0300] [Job 91] <STDIN>
D [29/Apr/2008:16:52:36 -0300] [Job 91] 
D [29/Apr/2008:16:52:36 -0300] [Job 91] GhostScript extra search path ('GS_LIB'): /usr/share/cups/fonts
D [29/Apr/2008:16:52:36 -0300] [Job 91] Pondering option 'job-uuid=urn:uuid:65ca67fe-b2b3-316f-617a-d270c64fc47f'
D [29/Apr/2008:16:52:36 -0300] [Job 91] Unknown option job-uuid=urn:uuid:65ca67fe-b2b3-316f-617a-d270c64fc47f.
D [29/Apr/2008:16:52:36 -0300] [Job 91] 
D [29/Apr/2008:16:52:36 -0300] [Job 91] ================================================
D [29/Apr/2008:16:52:36 -0300] [Job 91] 
D [29/Apr/2008:16:52:36 -0300] [Job 91] File: <STDIN>
D [29/Apr/2008:16:52:36 -0300] [Job 91] 
D [29/Apr/2008:16:52:36 -0300] [Job 91] ================================================
D [29/Apr/2008:16:52:36 -0300] [Job 91] 
D [29/Apr/2008:16:52:36 -0300] [Job 91] Reading PostScript input ...
D [29/Apr/2008:16:52:36 -0300] [Job 91] --> This document is DSC-conforming!
D [29/Apr/2008:16:52:36 -0300] [Job 91] 
D [29/Apr/2008:16:52:36 -0300] [Job 91] -----------
D [29/Apr/2008:16:52:36 -0300] [Job 91] Found: %%BeginProlog
D [29/Apr/2008:16:52:36 -0300] [Job 91] Found: %%EndProlog
D [29/Apr/2008:16:52:36 -0300] [Job 91] 
D [29/Apr/2008:16:52:36 -0300] [Job 91] -----------
D [29/Apr/2008:16:52:36 -0300] [Job 91] Found: %%BeginSetup
D [29/Apr/2008:16:52:36 -0300] [Job 91] Found: %%BeginFeature: *Quality normal
D [29/Apr/2008:16:52:36 -0300] [Job 91] Option: Quality=normal --> Setting option
D [29/Apr/2008:16:52:36 -0300] [Job 91] Found: %% FoomaticRIPOptionSetting: Quality=normal
D [29/Apr/2008:16:52:36 -0300] [Job 91] Option: Quality=normal --> Setting option
D [29/Apr/2008:16:52:36 -0300] [Job 91] Found: %%BeginFeature: *Resolution 1200x600dpi
D [29/Apr/2008:16:52:36 -0300] [Job 91] Option: Resolution=1200x600dpi --> Setting option
D [29/Apr/2008:16:52:36 -0300] [Job 91] Found: %% FoomaticRIPOptionSetting: Resolution=1200x600dpi
D [29/Apr/2008:16:52:36 -0300] [Job 91] Option: Resolution=1200x600dpi --> Setting option
D [29/Apr/2008:16:52:36 -0300] [Job 91] Found: %%BeginFeature: *PageRegion A4
D [29/Apr/2008:16:52:36 -0300] [Job 91] Option: PageRegion=A4 --> Option will be set by PostScript interpreter
D [29/Apr/2008:16:52:36 -0300] [Job 91] Found: %% FoomaticRIPOptionSetting: PageSize=A4
D [29/Apr/2008:16:52:36 -0300] [Job 91] Option: PageSize=A4 --> Setting option
D [29/Apr/2008:16:52:36 -0300] [Job 91] Found: %%BeginFeature: *InputSlot Auto
D [29/Apr/2008:16:52:36 -0300] [Job 91] Option: InputSlot=Auto --> Setting option
D [29/Apr/2008:16:52:36 -0300] [Job 91] Found: %% FoomaticRIPOptionSetting: InputSlot=Auto
D [29/Apr/2008:16:52:36 -0300] [Job 91] Option: InputSlot=Auto --> Setting option
D [29/Apr/2008:16:52:36 -0300] [Job 91] Found: %%BeginFeature: *MediaType Standard
D [29/Apr/2008:16:52:36 -0300] [Job 91] Option: MediaType=Standard --> Setting option
D [29/Apr/2008:16:52:36 -0300] [Job 91] Found: %% FoomaticRIPOptionSetting: MediaType=Standard
D [29/Apr/2008:16:52:36 -0300] [Job 91] Option: MediaType=Standard --> Setting option
D [29/Apr/2008:16:52:36 -0300] [Job 91] Found: %%BeginFeature: *Nup 1up
D [29/Apr/2008:16:52:36 -0300] [Job 91] Option: Nup=1up --> Setting option
D [29/Apr/2008:16:52:36 -0300] [Job 91] Found: %% FoomaticRIPOptionSetting: Nup=1up
D [29/Apr/2008:16:52:36 -0300] [Job 91] Option: Nup=1up --> Setting option
D [29/Apr/2008:16:52:36 -0300] [Job 91] Found: %%BeginFeature: *NupOrient port
D [29/Apr/2008:16:52:36 -0300] [Job 91] Option: NupOrient=port --> Setting option
D [29/Apr/2008:16:52:36 -0300] [Job 91] Found: %% FoomaticRIPOptionSetting: NupOrient=port
D [29/Apr/2008:16:52:36 -0300] [Job 91] Option: NupOrient=port --> Setting option
D [29/Apr/2008:16:52:36 -0300] [Job 91] Found: %%BeginFeature: *Copies 1
D [29/Apr/2008:16:52:36 -0300] [Job 91] Option: Copies=1 --> Setting option
D [29/Apr/2008:16:52:36 -0300] [Job 91] Found: %% FoomaticRIPOptionSetting: Copies=1
D [29/Apr/2008:16:52:36 -0300] [Job 91] Option: Copies=1 --> Setting option
D [29/Apr/2008:16:52:36 -0300] [Job 91] Found: %%EndSetup
D [29/Apr/2008:16:52:36 -0300] [Job 91] Inserting PostScript code for CUPS' page accounting
D [29/Apr/2008:16:52:36 -0300] [Job 91] 
D [29/Apr/2008:16:52:36 -0300] [Job 91] -----------
D [29/Apr/2008:16:52:36 -0300] [Job 91] New page:  1 1
D [29/Apr/2008:16:52:36 -0300] [Job 91] Inserting option code into "PageSetup" section.
D [29/Apr/2008:16:52:36 -0300] [Job 91] 
D [29/Apr/2008:16:52:36 -0300] [Job 91] Found: %%BeginPageSetup
D [29/Apr/2008:16:52:36 -0300] [Job 91] Found: %%EndPageSetup
D [29/Apr/2008:16:52:36 -0300] [Job 91] End of page header
D [29/Apr/2008:16:52:36 -0300] [Job 91] Stopping search for page header options
D [29/Apr/2008:16:52:36 -0300] [Job 91] Found:       lineto				% Move there...
D [29/Apr/2008:16:52:36 -0300] [Job 91] --> Output goes directly to the renderer now.
D [29/Apr/2008:16:52:36 -0300] [Job 91] 
D [29/Apr/2008:16:52:36 -0300] [Job 91] 
D [29/Apr/2008:16:52:36 -0300] [Job 91] Starting renderer
D [29/Apr/2008:16:52:36 -0300] [Job 91] Found: %%Trailer
D [29/Apr/2008:16:52:36 -0300] [Job 91] --> Continue DSC parsing now.
D [29/Apr/2008:16:52:36 -0300] [Job 91] 
D [29/Apr/2008:16:52:36 -0300] [Job 91] Found: %%Pages: 1
D [29/Apr/2008:16:52:36 -0300] [Job 91] --> Continue DSC parsing now.
D [29/Apr/2008:16:52:36 -0300] [Job 91] 
D [29/Apr/2008:16:52:36 -0300] [Job 91] Found: %%BoundingBox: 0 0 612 792
D [29/Apr/2008:16:52:36 -0300] [Job 91] --> Continue DSC parsing now.
D [29/Apr/2008:16:52:36 -0300] [Job 91] 
D [29/Apr/2008:16:52:36 -0300] [Job 91] Found: %%EOF
D [29/Apr/2008:16:52:36 -0300] [Job 91] --> Continue DSC parsing now.
D [29/Apr/2008:16:52:36 -0300] [Job 91] 
D [29/Apr/2008:16:52:36 -0300] [Job 91] 
D [29/Apr/2008:16:52:36 -0300] [Job 91] Closing renderer
D [29/Apr/2008:16:52:36 -0300] [Job 91] JCL: <job data> 
D [29/Apr/2008:16:52:36 -0300] [Job 91] 
D [29/Apr/2008:16:52:36 -0300] [Job 91] renderer PID kid4=6828
D [29/Apr/2008:16:52:36 -0300] [Job 91] renderer command: foo2zjs-wrapper   -P -z1 -L0  -r1200x600 -p9 -s7 -m1   -n1 
D [29/Apr/2008:16:52:36 -0300] [Job 91] /bin/bash: foo2zjs-wrapper: command not found
D [29/Apr/2008:16:52:36 -0300] [Job 91] renderer return value: 127
D [29/Apr/2008:16:52:36 -0300] [Job 91] renderer received signal: 127
D [29/Apr/2008:16:52:36 -0300] [Job 91] Process dying with "The renderer command line returned an unrecognized error code 127.", exit stat: 1
D [29/Apr/2008:16:52:36 -0300] [Job 91] error: Illegal seek (29)
D [29/Apr/2008:16:52:36 -0300] [Job 91] The renderer command line returned an unrecognized error code 127.
D [29/Apr/2008:16:52:36 -0300] [Job 91] tail process done writing data to STDOUT
D [29/Apr/2008:16:52:36 -0300] [Job 91] KID4 finished
D [29/Apr/2008:16:52:36 -0300] [Job 91] KID3 exited with status 1
D [29/Apr/2008:16:52:36 -0300] [Job 91] Renderer exit stat: 1
D [29/Apr/2008:16:52:36 -0300] [Job 91] Renderer process finished
D [29/Apr/2008:16:52:36 -0300] [Job 91] Killing process 6827 (KID3)
D [29/Apr/2008:16:52:36 -0300] [Job 91] Process dying with "Error closing renderer", exit stat: 1
D [29/Apr/2008:16:52:36 -0300] [Job 91] error: Illegal seek (29)
D [29/Apr/2008:16:52:36 -0300] [Job 91] Error closing renderer
E [29/Apr/2008:16:52:36 -0300] PID 6819 (/usr/lib/cups/filter/foomatic-rip) stopped with status 1!
D [29/Apr/2008:16:52:36 -0300] PID 6820 (/usr/lib/cups/backend/smb) exited with no errors.
D [29/Apr/2008:16:52:36 -0300] [Job 91] File 0 is complete.
E [29/Apr/2008:16:52:36 -0300] [Job 91] Job stopped due to filter errors.
D [29/Apr/2008:16:52:36 -0300] Discarding unused printer-state-changed event...
D [29/Apr/2008:16:52:36 -0300] Discarding unused job-stopped event...
D [29/Apr/2008:16:52:36 -0300] cupsdAcceptClient: 11 from localhost (Domain)
D [29/Apr/2008:16:52:36 -0300] cupsdReadClient: 11 POST / HTTP/1.1
D [29/Apr/2008:16:52:36 -0300] cupsdAuthorize: No authentication data provided.
D [29/Apr/2008:16:52:36 -0300] Get-Jobs ipp://localhost/jobs/
D [29/Apr/2008:16:52:36 -0300] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)
D [29/Apr/2008:16:52:36 -0300] cupsdReadClient: 11 POST / HTTP/1.1
D [29/Apr/2008:16:52:36 -0300] cupsdAuthorize: No authentication data provided.
D [29/Apr/2008:16:52:36 -0300] CUPS-Get-Printers
D [29/Apr/2008:16:52:36 -0300] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)
D [29/Apr/2008:16:52:36 -0300] cupsdCloseClient: 11
D [29/Apr/2008:16:52:36 -0300] cupsdReadClient: 9 GET /printers/hp1020 HTTP/1.1
D [29/Apr/2008:16:52:36 -0300] cupsdAuthorize: Authorized as jochoa using Basic
D [29/Apr/2008:16:52:36 -0300] [CGI] /usr/lib/cups/cgi-bin/printers.cgi started - PID = 6830
I [29/Apr/2008:16:52:36 -0300] Started "/usr/lib/cups/cgi-bin/printers.cgi" (pid=6830)
D [29/Apr/2008:16:52:36 -0300] cupsdSendCommand: 9 file=11
D [29/Apr/2008:16:52:36 -0300] cupsdAcceptClient: 13 from localhost (Domain)
D [29/Apr/2008:16:52:36 -0300] cupsdReadClient: 13 POST / HTTP/1.1
D [29/Apr/2008:16:52:36 -0300] cupsdAuthorize: No authentication data provided.
D [29/Apr/2008:16:52:36 -0300] CUPS-Get-Default
D [29/Apr/2008:16:52:36 -0300] cupsdProcessIPPRequest: 13 status_code=0 (successful-ok)
D [29/Apr/2008:16:52:36 -0300] [CGI] show_printer(http=0x80761d0, printer="hp1020")
D [29/Apr/2008:16:52:36 -0300] cupsdReadClient: 13 POST / HTTP/1.1
D [29/Apr/2008:16:52:36 -0300] cupsdAuthorize: No authentication data provided.
D [29/Apr/2008:16:52:36 -0300] Get-Printer-Attributes ipp://localhost/printers/hp1020
D [29/Apr/2008:16:52:36 -0300] cupsdProcessIPPRequest: 13 status_code=0 (successful-ok)
D [29/Apr/2008:16:52:36 -0300] [CGI] lang="en_US.UTF-8", locale="/en_US"...
D [29/Apr/2008:16:52:36 -0300] cupsdReadClient: 13 POST / HTTP/1.1
D [29/Apr/2008:16:52:36 -0300] cupsdAuthorize: No authentication data provided.
D [29/Apr/2008:16:52:36 -0300] Get-Jobs ipp://localhost:631/printers/hp1020
D [29/Apr/2008:16:52:36 -0300] cupsdProcessIPPRequest: 13 status_code=0 (successful-ok)
D [29/Apr/2008:16:52:36 -0300] [CGI] lang="en_US.UTF-8", locale="/en_US"...
D [29/Apr/2008:16:52:36 -0300] [CGI] lang="en_US.UTF-8", locale="/en_US"...
D [29/Apr/2008:16:52:36 -0300] [CGI] lang="en_US.UTF-8", locale="/en_US"...
D [29/Apr/2008:16:52:36 -0300] cupsdCloseClient: 13
D [29/Apr/2008:16:52:36 -0300] PID 6830 (/usr/lib/cups/cgi-bin/printers.cgi) exited with no errors.
D [29/Apr/2008:16:52:36 -0300] [CGI] lang="en_US.UTF-8", locale="/en_US"...
D [29/Apr/2008:16:52:36 -0300] [CGI] lang="en_US.UTF-8", locale="/en_US"...
D [29/Apr/2008:16:52:36 -0300] [CGI] lang="en_US.UTF-8", locale="/en_US"...
D [29/Apr/2008:16:52:36 -0300] [CGI] lang="en_US.UTF-8", locale="/en_US"...
D [29/Apr/2008:16:52:36 -0300] [CGI] lang="en_US.UTF-8", locale="/en_US"...
D [29/Apr/2008:16:52:37 -0300] [Job 91] Unloading...
D [29/Apr/2008:16:52:52 -0300] cupsdReadClient: 9 GET /admin HTTP/1.1
D [29/Apr/2008:16:52:52 -0300] cupsdAuthorize: Authorized as jochoa using Basic
D [29/Apr/2008:16:52:52 -0300] [CGI] /usr/lib/cups/cgi-bin/admin.cgi started - PID = 6831
I [29/Apr/2008:16:52:52 -0300] Started "/usr/lib/cups/cgi-bin/admin.cgi" (pid=6831)
D [29/Apr/2008:16:52:52 -0300] cupsdSendCommand: 9 file=11
D [29/Apr/2008:16:52:52 -0300] [CGI] admin.cgi started...
D [29/Apr/2008:16:52:52 -0300] [CGI] http=0x80790d0
D [29/Apr/2008:16:52:52 -0300] cupsdAcceptClient: 13 from localhost (Domain)
D [29/Apr/2008:16:52:52 -0300] [CGI] No form data, showing main menu...
D [29/Apr/2008:16:52:52 -0300] [CGI] /usr/share/cups/drivers/pscript5.dll: No such file or directory
D [29/Apr/2008:16:52:52 -0300] cupsdReadClient: 13 POST / HTTP/1.1
D [29/Apr/2008:16:52:52 -0300] cupsdAuthorize: No authentication data provided.
D [29/Apr/2008:16:52:52 -0300] Get-Subscriptions ipp://localhost/
D [29/Apr/2008:16:52:52 -0300] Get-Subscriptions client-error-not-found: No subscriptions found.
D [29/Apr/2008:16:52:52 -0300] cupsdProcessIPPRequest: 13 status_code=406 (client-error-not-found)
D [29/Apr/2008:16:52:52 -0300] [CGI] lang="en_US.UTF-8", locale="/en_US"...
D [29/Apr/2008:16:52:52 -0300] [CGI] lang="en_US.UTF-8", locale="/en_US"...
D [29/Apr/2008:16:52:52 -0300] [CGI] lang="en_US.UTF-8", locale="/en_US"...
D [29/Apr/2008:16:52:52 -0300] cupsdCloseClient: 13
D [29/Apr/2008:16:52:52 -0300] PID 6831 (/usr/lib/cups/cgi-bin/admin.cgi) exited with no errors.
D [29/Apr/2008:16:52:58 -0300] cupsdReadClient: 9 GET /admin/log/page_log HTTP/1.1
D [29/Apr/2008:16:52:58 -0300] cupsdAuthorize: Authorized as jochoa using Basic
D [29/Apr/2008:16:53:08 -0300] cupsdReadClient: 9 GET /admin/log/error_log HTTP/1.1
D [29/Apr/2008:16:53:08 -0300] cupsdAuthorize: Authorized as jochoa using Basic

---

