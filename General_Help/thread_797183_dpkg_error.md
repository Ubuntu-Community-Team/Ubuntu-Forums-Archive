---
title: "dpkg error"
date: 2008-05-17
forum: General Help
---

### Post by natibo on 2008-05-17
I tried to get GnuCash aqbanking thing to work.  In the process I felt I needed to install libchipcard3.  I found only am rpm package and converted it to a deb using alien.  It would not install properly.

However, I cannot remove it at all.  Update manager gives me the following error:

Package in inconsistent state

[INDENT]The package 'libchipcard3' is in a inconsistent state and needs to be reinstalled, but no archive can be found for it. Please reinstall the package manually or remove it from the system.[/INDENT]

I tried the following and it did not work:

[INDENT]natibo@natibo:~$ dpkg --force-all -r libchipcard3
dpkg: operation requires read/write access to dpkg status area
natibo@natibo:~$ sudo dpkg --force-all -r libchipcard3
dpkg - warning, overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 157165 files and directories currently installed.)
Removing libchipcard3 ...
test: 12: Illegal number: remove
/var/lib/dpkg/info/libchipcard3.postrm: 15: sbin/insserv: not found
dpkg: error processing libchipcard3 (--remove):
 subprocess post-removal script returned error exit status 127
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 libchipcard3
natibo@natibo:~$ [/INDENT]

If I try to reinstall I get this:

[INDENT]natibo@natibo:~$  dpkg -i libchipcard3_3.0.3-28_amd64.deb
dpkg: requested operation requires superuser privilege
natibo@natibo:~$ sudo dpkg -i libchipcard3_3.0.3-28_amd64.deb
Selecting previously deselected package libchipcard3.
(Reading database ... 157166 files and directories currently installed.)
Preparing to replace libchipcard3 3.0.3-28 (using libchipcard3_3.0.3-28_amd64.deb) ...
Unpacking replacement libchipcard3 ...
test: 12: Illegal number: upgrade
/var/lib/dpkg/info/libchipcard3.postrm: 15: sbin/insserv: not found
dpkg: warning - old post-removal script returned error exit status 127
dpkg - trying script from the new package instead ...
test: 12: Illegal number: failed-upgrade
/var/lib/dpkg/tmp.ci/postrm: 15: sbin/insserv: not found
dpkg: error processing libchipcard3_3.0.3-28_amd64.deb (--install):
 subprocess new post-removal script returned error exit status 127
test: 12: Illegal number: abort-upgrade
/var/lib/dpkg/tmp.ci/postrm: 15: sbin/insserv: not found
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 127
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 libchipcard3_3.0.3-28_amd64.deb
natibo@natibo:~$ [/INDENT]

---

### Post by forestpixie on 2008-05-17
Try this to remove it

```
dpkg --remove --force-remove-reinstreq libchipcard3
```

---

### Post by ramjet_1953 on 2008-05-17
This will remove the listing from the /var/lib dpkg/status file.

1. open nautilus in super user mode. ie In a terminal type this in: [COLOR="Red"]gksu nautilus[/COLOR]. It will ask you for your password.

2. When Nautilus opens, navigate to [COLOR="Blue"]/var/lib/dpkg/status[/COLOR]

3. Right click on the status file and open it in text editor.

4. Carefully search through the listings and locate [COLOR="Blue"]libchipcard3[/COLOR] and delete every reference to it.

5. Save the file and re-start.

6. The error should now be gone.

7. As a precaution I would back-up the ststus file, before altering it.

Regards,
Roger :cool:

---

### Post by Xiong Chiamiov on 2008-05-17
As a side note, was there a source package for libchipcard3?  I'd recommend compiling (especially with checkinstall) over using alien any day of the week.

---

