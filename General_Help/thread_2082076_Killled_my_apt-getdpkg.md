---
title: "Killled my apt-get/dpkg"
date: 2012-11-08
forum: General Help
---

### Post by svarogg on 2012-11-08
It all started when for some reason, whenever I installed anything via apt-get, this message appeared:
```
dpkg: warning: files list file for package '...' missing; assuming package has no files currently installed
```For each and every package I had installed.

Somewhere on some forum somebody suggested to apt-get install --reinstall all packages, and although it looked like a good idea back in the time, it backfired.

Now, whenever I try to install anything I get next message:
```
Setting up foomatic-filters (4.0.17-1) ...
dpkg: error processing foomatic-filters (--configure):
 subprocess installed post-installation script returned error exit status 10
dpkg: dependency problems prevent configuration of foomatic-db-engine:
 foomatic-db-engine depends on foomatic-filters (>= 4.0); however:
  Package foomatic-filters is not configured yet.

dpkg: error processing foomatic-db-engine (--configure):
 dependency problems - leaving unconfigured
Setting up libpaper1:amd64 (1.1.24+nmu2) ...
No apport report written because the error message indicates its a followup error from a previous failure.
       dpkg: error processing libpaper1:amd64 (--configure):
 subprocess installed post-installation script returned error exit status 10
dpkg: dependency problems prevent configuration of cups:
 cups depends on libpaper1; however:
  Package libpaper1:amd64 is not configured yet.

dpkg: error processing cups (--configure):
 dependency problems - leaving unconfigured
Setting up samba-common (2:3.6.6-3ubuntu5) ...
No apport report written because the error message indicates its a followup error from a previous failure.
       dpkg: error processing samba-common (--configure):
 subprocess installed post-installation script returned error exit status 10
dpkg: dependency problems prevent configuration of samba-common-bin:
 samba-common-bin depends on samba-common (>= 2:3.4.0~pre1-2); however:
  Package samba-common is not configured yet.

dpkg: error processing samba-common-bin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of nautilus-share:
 nautilus-share depends on samba-common (>= 3.0.27a); however:
  Package samba-common is not configured yet.
 nautilus-share depends on samba-common-bin | samba-common (<< 2:3.4.0~pre2-1~0); however:
  Package samba-common-bin is not configured yet.
  Version of samba-common on system is 2:3.6.6-3ubuntu5.

dpkg: error processing nautilus-share (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of winbind:
 winbind depends on samba-common (= 2:3.6.6-3ubuntu5); howeNo apport report written because MaxReports is reached already
                      No apport report written because MaxReports is reached already
                                                                                    No apport report written because MaxReports is reached already
                                               No apport report written because MaxReports is reached already
          No apport report written because MaxReports is reached already
                                                                        ver:
  Package samba-common is not configured yet.

dpkg: error processing winbind (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libnss-winbind:amd64:
 libnss-winbind:amd64 depends on winbind (= 2:3.6.6-3ubuntu5); however:
  Package winbind is not configured yet.
 libnss-winbind:amd64 depends on samba-common (= 2:3.6.6-3ubuntu5); however:
  Package samba-common is not configured yet.

dpkg: error processing libnss-winbind:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libpam-winbind:amd64:
 libpam-winbind:amd64 depends on winbind (= 2:3.6.6-3ubuntu5); however:
  Package winbind is not configured yet.
 libpam-winbind:amd64 depends on samba-common (= 2:3.6.6-3ubuntu5); however:
  Package samba-common is not configured yet.

dpkg: error processing libpam-winbind:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of smbclient:
 smbclient depends on samba-common (= 2:3.6.6-3ubuntu5); however:
  Package samba-common is not configured yet.

dpkg: error processing smbclient (--configure):
 dependency problems - leaving unconfigured
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 foomatic-filters
 foomatic-db-engine
 libpaper1:amd64
 cups
 samba-common
 samba-common-bin
 nautilus-share
 winbind
 libnss-winbind:amd64
 libpam-winbind:amd64
 smbclient

```Any help please?

---

### Post by svarogg on 2012-11-08
I think I've traced the error down to this:
```

> sudo dpkg -i libpaper1_1.1.24+nmu2_amd64.deb
Preparing to replace libpaper1:amd64 1.1.24+nmu2 (using libpaper1_1.1.24+nmu2_amd64.deb) ...
Unpacking replacement libpaper1:amd64 ...
Setting up libpaper1:amd64 (1.1.24+nmu2) ...
dpkg: error processing libpaper1:amd64 (--install):
 subprocess installed post-installation script returned error exit status 10
Processing triggers for man-db ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 libpaper1:amd64

```There's some error when installing libpaper1 but where can I see the error?

---

