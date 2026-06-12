---
title: "Cannot use nx cups backend - lpadmin bad device-uri"
date: 2008-05-27
forum: General Help
---

### Post by gracedman on 2008-05-27
I have NoMachine's NX client printing perfectly fine in CentOS 5.1 but it is failing in Ubuntu 8.0.4 (fully patched 64 bit).  The NX client attempts to connect the virtual desktop to a printer on the physical desktop via printer sharing using the nx backend.

I keep getting an error:
Printer 'printername' couldn't be attached.  Error is: '1,' 'lpadmin: Bad device-uri "nx://name:passwd@device:4035/cifs/printername"'

The nx backend does exist in /usr/lib/cups/backend although it is a symbolic link

denise@denisedell:/usr/lib/cups$ ls -l backend
total 332
-rwxr-xr-x 1 root root  7200 2008-04-24 09:49 beh
-rwxr-xr-x 1 root root 37012 2008-04-21 03:36 bluetooth
-rwxr-xr-x 1 root root 15428 2008-01-24 06:55 canon
-rwx------ 1 root root 24044 2008-01-24 07:47 cups-pdf
-rwxr-xr-x 2 root root  8724 2008-04-21 16:15 dnssd
-rwxr-xr-x 1 root root 16052 2008-01-24 06:55 epson
-rwxr-xr-x 1 root root  9028 2008-04-09 16:32 hal
-rwxr-xr-x 1 root root 12200 2008-04-15 12:44 hp
-rwxr-xr-x 1 root root  8228 2008-04-15 12:44 hpfax
-rwxr-xr-x 3 root root 24040 2008-04-21 16:18 http
-rwxr-xr-x 3 root root 24040 2008-04-21 16:18 ipp
-rwx------ 2 root root 19220 2008-04-21 16:18 lpd
lrwxrwxrwx 1 root root    19 2008-04-29 10:26 nx -> /usr/NX/bin/nxspool
-rwxr-xr-x 2 root root 15472 2008-04-21 16:18 parallel
-rwxr-xr-x 1 root root  5455 2007-11-04 10:52 ptal
-rwxr-xr-x 2 root root  6648 2008-04-21 16:18 scsi
-rwxr-xr-x 2 root root 14528 2008-04-21 16:18 serial
lrwxrwxrwx 1 root root    21 2008-04-27 14:24 smb -> ../../../bin/smbspool
-rwxr-xr-x 2 root root 26604 2008-04-21 16:18 snmp
-rwxr-xr-x 2 root root 12828 2008-04-21 16:18 socket
-rwxr-xr-x 2 root root 16828 2008-04-21 16:18 usb

Here are the rights and ownership of nxspool:
-rwxr-xr-x 1 root root   823784 2008-04-02 11:08 nxspool

If I change the exact same uri to smb:// instead of nx://, it works fine.  Why does cups on Hardy refuse to use the nx backend? I've been stuck on this for days.  Any help will be greatly appreciated.  Thanks - John

---

### Post by gracedman on 2008-05-29
The problem turned out to be AppArmor.  As described, /usr/lib/cups/backend/nx is a symbolic link to /usr/NX/bin/nxspool.  When cupsd attempts to execute nxspool, it is not allowed.  I added the line below to /etc/apparmor.d/usr.sbin.cupsd and it all worked:

  /usr/NX/bin/nxspool Ux,

I'm not an AppArmor expert at all so, if someone knows of a better way, please correct me.  Thanks - John

---

