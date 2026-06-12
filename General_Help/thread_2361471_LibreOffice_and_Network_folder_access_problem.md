---
title: "LibreOffice and Network folder access problem"
date: 2017-05-17
forum: General Help
---

### Post by leoneluqueio on 2017-05-17
I recently can't open my documents with libreoffice, when I double click calc or write on my libreoffice only try to open the app and nothing happens. Same problem happens when I try for example to call a shared network folder like smb://192.168.20.4 and nothing happens.

Thanks

---

### Post by ajgreeny on 2017-05-17
Try opening LO Writer from terminal with command **libreoffice --writer**.

You may see output with some errors that might help diagnose the problem, so copy any output you get back here.

Please use **Code-Tags** for terminal output. See my signature below for a **How-to**

---

### Post by ajgreeny on 2017-05-17
*Thread moved to **General Help**.* which is more appropriate and a better fit.

---

### Post by leoneluqueio on 2017-05-18
Caríssimo

Following your recommendations I had the following resolts:
```
leoneluqueio@CCSIBNELP0050:~$ libreoffice --writer
/usr/lib/libreoffice/program/soffice.bin: error while loading shared libraries: libgssapi.so.3: cannot open shared object file: No such file or directory
leoneluqueio@CCSIBNELP0050:~$ 

```
Thank you very much for your attention

---

### Post by ajgreeny on 2017-05-18
That missing library **libgssapi.so.3** is supplied by the **libgssapi3-heimdal** package so see if installing that with ```
sudo apt install libgssapi3-heimdal
```does the trick for you.

I can't help with the shared network folder problem, never having needed or used samba.

---

### Post by leoneluqueio on 2017-05-23
Thanks for your help.

When I try to do any installation I found this error:
```
Setting up samba (2:4.3.11+dfsg-0ubuntu0.16.04.6) ...
Job for smbd.service failed because the control process exited with error code. See "systemctl status smbd.service" and "journalctl -xe" for details.
invoke-rc.d: initscript smbd, action "start" failed.
&#9679; smbd.service - LSB: start Samba SMB/CIFS daemon (smbd)
   Loaded: loaded (/etc/init.d/smbd; bad; vendor preset: enabled)
   Active: failed (Result: exit-code) since Tue 2017-05-23 19:22:22 CAT; 8ms ago
     Docs: man:systemd-sysv-generator(8)
  Process: 9335 ExecStart=/etc/init.d/smbd start (code=exited, status=1/FAILURE)

May 23 19:22:21 CCSIBNELP0050 systemd[1]: Starting LSB: start Samba SMB/CIFS....
May 23 19:22:22 CCSIBNELP0050 smbd[9335]:  * Starting SMB/CIFS daemon smbd
May 23 19:22:22 CCSIBNELP0050 smbd[9335]: /usr/sbin/smbd: error while loadin...y
May 23 19:22:22 CCSIBNELP0050 smbd[9335]:    ...fail!
May 23 19:22:22 CCSIBNELP0050 systemd[1]: smbd.service: Control process exit...1
May 23 19:22:22 CCSIBNELP0050 systemd[1]: Failed to start LSB: start Samba S....
May 23 19:22:22 CCSIBNELP0050 systemd[1]: smbd.service: Unit entered failed ....
May 23 19:22:22 CCSIBNELP0050 systemd[1]: smbd.service: Failed with result '....
Hint: Some lines were ellipsized, use -l to show in full.
dpkg: error processing package samba (--configure):
 subprocess installed post-installation script returned error exit status 1
Processing triggers for libc-bin (2.23-0ubuntu7) ...
Errors were encountered while processing:
 samba
E: Sub-process /usr/bin/dpkg returned an error code (1)
leoneluqueio@CCSIBNELP0050:~$ sudo apt-get remove --purge libreoffice*


```

---

