---
title: "Evolution not starting"
date: 2007-10-21
forum: General Help
---

### Post by rich86 on 2007-10-21
My Evolution is dead. when running it from the terminal i get this:
$ evolution
CalDAV Eplugin starting up ...

(evolution-2.10:7222): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `EImportHook'

(evolution-2.10:7222): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(evolution-2.10:7222): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `(null)'

(evolution-2.10:7222): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion`G_TYPE_CHECK_INSTANCE (instance)' failed

(evolution-2.10:7222): GLib-GObject-WARNING **: invalid uninstantiatable type `(null)' in cast to `ESourceGroup'

(evolution-2.10:7222): e-data-server-CRITICAL **: e_source_group_peek_base_uri: assertion 'E_IS_SOURCE_GROUP (group)' failed
Segmentation fault (core dumped)

i have found the log file in /var/crash buts its very big and nearly crashes gedit when trying to load it.
So far i have tried running evolution from another user account and it seems fine, it has the wizard for setting it up i can then run it and it works. I tried removing the .evolution folder in my home and it still didn't start. I apt-get removed it and then re-installed it. None of these have worked so far.

Any ideas please, i want my emails back!

Thanks in advance,
Rich

---

### Post by por100pre1 on 2007-10-21
Try renaming the ~/.gconf/apps/evolution folder.

---

### Post by rich86 on 2007-10-21
No change still getting the same error messages

---

### Post by rich86 on 2007-10-21
I've also noticed on the process list evolution-data-server-1.10 seems to be running in the background, don't know if that helps at all if that part is running?

---

### Post by rich86 on 2007-10-21
I've tried restoring and old backup and have done a complete removal and reinstall but its still not working on my account. Here is the dump that it makes: (i haven't included the core dump)
```
ProblemType: Crash
Architecture: i386
Date: Sun Oct 21 16:28:52 2007
DistroRelease: Ubuntu 7.04
ExecutablePath: /usr/bin/evolution-2.10
ProcCmdline: evolution
ProcCwd: /home/richard
ProcEnviron:
 SHELL=/bin/bash
 PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
 LANG=en_GB.UTF-8
ProcMaps:
 08048000-08065000 r-xp 00000000 08:15 1409288    /usr/bin/evolution-2.10
 08065000-08067000 rw-p 0001d000 08:15 1409288    /usr/bin/evolution-2.10
 08067000-08184000 rw-p 08067000 00:00 0          [heap]
 b58b4000-b58ca000 r-xp 00000000 08:15 1411195    /usr/lib/libsasl2.so.2.0.22
 b58ca000-b58cb000 rw-p 00015000 08:15 1411195    /usr/lib/libsasl2.so.2.0.22
 b58cb000-b58d0000 r-xp 00000000 08:15 1215720    /lib/tls/i686/cmov/libcrypt-2.5.so
 b58d0000-b58d2000 rw-p 00004000 08:15 1215720    /lib/tls/i686/cmov/libcrypt-2.5.so
 b58d2000-b58f9000 rw-p b58d2000 00:00 0 
 b58f9000-b5905000 r-xp 00000000 08:15 1411041    /usr/lib/liblber.so.2.0.130
 b5905000-b5906000 rw-p 0000b000 08:15 1411041    /usr/lib/liblber.so.2.0.130
 b5906000-b593b000 r-xp 00000000 08:15 1411047    /usr/lib/libldap_r.so.2.0.130
 b593b000-b593c000 rw-p 00035000 08:15 1411047    /usr/lib/libldap_r.so.2.0.130
 b594b000-b5953000 r-xp 00000000 08:15 2180934    /usr/lib/evolution/2.10/libevolution-addressbook-importers.so.0.0.0
 b5953000-b5954000 rw-p 00008000 08:15 2180934    /usr/lib/evolution/2.10/libevolution-addressbook-importers.so.0.0.0
 b5954000-b5958000 r-xp 00000000 08:15 2180933    /usr/lib/evolution/2.10/libevolution-addressbook-a11y.so.0.0.0
 b5958000-b5959000 rw-p 00004000 08:15 2180933    /usr/lib/evolution/2.10/libevolution-addressbook-a11y.so.0.0.0
 b5959000-b5996000 r-xp 00000000 08:15 2180943    /usr/lib/evolution/2.10/components/libevolution-addressbook.so
 b5996000-b5999000 rw-p 0003d000 08:15 2180943    /usr/lib/evolution/2.10/components/libevolution-addressbook.so
 b5999000-b59d3000 r-xp 00000000 08:15 1413243    /usr/lib/firefox/libnssckbi.so
 b59d3000-b59dd000 rw-p 0003a000 08:15 1413243    /usr/lib/firefox/libnssckbi.so
 b59dd000-b5a1c000 r-xp 00000000 08:15 1413249    /usr/lib/libfreebl3.so
 b5a1c000-b5a1d000 rw-p 0003f000 08:15 1413249    /usr/lib/libfreebl3.so
 b5a1d000-b5a26000 r-xp 00000000 08:15 2180938    /usr/lib/evolution/2.10/libevolution-smime.so.0.0.0
 b5a26000-b5a27000 rw-p 00008000 08:15 2180938    /usr/lib/evolution/2.10/libevolution-smime.so.0.0.0
 b5a27000-b5a32000 r-xp 00000000 08:15 2180927    /usr/lib/evolution/2.10/libessmime.so.0.0.0
 b5a32000-b5a33000 rw-p 0000a000 08:15 2180927    /usr/lib/evolution/2.10/libessmime.so.0.0.0
 b5a33000-b5a39000 r-xp 00000000 08:15 2180937    /usr/lib/evolution/2.10/libevolution-mail-importers.so.0.0.0
 b5a39000-b5a3a000 rw-p 00006000 08:15 2180937    /usr/lib/evolution/2.10/libevolution-mail-importers.so.0.0.0
 b5a3a000-b5a42000 r-xp 00000000 08:15 2180923    /usr/lib/evolution/2.10/libecontactlisteditor.so.0.0.0
 b5a42000-b5a43000 rw-p 00007000 08:15 2180923    /usr/lib/evolution/2.10/libecontactlisteditor.so.0.0.0
 b5a43000-b5a59000 r-xp 00000000 08:15 2180922    /usr/lib/evolution/2.10/libecontacteditor.so.0.0.0
 b5a59000-b5a5b000 rw-p 00015000 08:15 2180922    /usr/lib/evolution/2.10/libecontacteditor.so.0.0.0
 b5a5b000-b5a60000 r-xp 00000000 08:15 2180924    /usr/lib/evolution/2.10/libefilterbar.so.0.0.0
 b5a60000-b5a61000 rw-p 00005000 08:15 2180924    /usr/lib/evolution/2.10/libefilterbar.so.0.0.0
 b5a61000-b5b20000 r-xp 00000000 08:15 2180945    /usr/lib/evolution/2.10/components/libevolution-mail.so
 b5b20000-b5b28000 rw-p 000bf000 08:15 2180945    /usr/lib/evolution/2.10/components/libevolution-mail.so
 b5b28000-b5b29000 rw-p b5b28000 00:00 0 
 b5b29000-b5b2d000 r-xp 00000000 08:15 1474610    /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
 b5b2d000-b5b2e000 rw-p 00003000 08:15 1474610    /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
 b5b2f000-b5da9000 r--p 00000000 08:15 1738083    /usr/share/icons/hicolor/icon-theme.cache
 b5da9000-b6450000 r--p 00000000 08:15 1738473    /usr/share/icons/gnome/icon-theme.cache
 b6450000-b647b000 r-xp 00000000 08:15 1411226    /usr/lib/libsoup-2.2.so.8.5.0
 b647b000-b647c000 rw-p 0002b000 08:15 1411226    /usr/lib/libsoup-2.2.so.8.5.0
 b6480000-b648b000 r--p 00000000 08:15 1740856    /usr/share/icons/Mist/icon-theme.cache
 b648b000-b649c000 r-xp 00000000 08:15 2180935    /usr/lib/evolution/2.10/libevolution-calendar-a11y.so.0.0.0
 b649c000-b649d000 rw-p 00010000 08:15 2180935    /usr/lib/evolution/2.10/libevolution-calendar-a11y.so.0.0.0
 b649d000-b64a2000 r-xp 00000000 08:15 2180936    /usr/lib/evolution/2.10/libevolution-calendar-importers.so.0.0.0
 b64a2000-b64a3000 rw-p 00004000 08:15 2180936    /usr/lib/evolution/2.10/libevolution-calendar-importers.so.0.0.0
 b64a3000-b64a5000 r-xp 00000000 08:15 2180920    /usr/lib/evolution/2.10/libeabutil.so.0.0.0
 b64a5000-b64a6000 rw-p 00002000 08:15 2180920    /usr/lib/evolution/2.10/libeabutil.so.0.0.0
 b64a6000-b64b4000 r-xp 00000000 08:15 2180941    /usr/lib/evolution/2.10/libmenus.so.0.0.0
 b64b4000-b64b5000 rw-p 0000e000 08:15 2180941    /usr/lib/evolution/2.10/libmenus.so.0.0.0
 b64b5000-b65be000 r-xp 00000000 08:15 2180944    /usr/lib/evolution/2.10/components/libevolution-calendar.so
 b65be000-b65c6000 rw-p 00108000 08:15 2180944    /usr/lib/evolution/2.10/components/libevolution-calendar.so
 b65c6000-b65c7000 rw-p b65c6000 00:00 0 
 b65c7000-b65d2000 r-xp 00000000 08:15 1474579    /usr/lib/gtk-2.0/2.10.0/engines/libindustrial.so
 b65d2000-b65d3000 rw-p 0000b000 08:15 1474579    /usr/lib/gtk-2.0/2.10.0/engines/libindustrial.so
 b65d3000-b65d8000 r--p 00000000 08:15 1820571    /usr/share/locale-langpack/en_GB/LC_MESSAGES/glib20.mo
 b65d8000-b65d9000 rw-p b65d8000 00:00 0 
 b65d9000-b65db000 r-xp 00000000 08:15 2180993    /usr/lib/evolution/2.10/plugins/liborg-gnome-evolution-caldav.so
 b65db000-b65dc000 rw-p 00002000 08:15 2180993    /usr/lib/evolution/2.10/plugins/liborg-gnome-evolution-caldav.so
 b65dc000-b65ef000 r-xp 00000000 08:15 2180940    /usr/lib/evolution/2.10/libfilter.so.0.0.0
 b65ef000-b65f0000 rw-p 00012000 08:15 2180940    /usr/lib/evolution/2.10/libfilter.so.0.0.0
 b65f0000-b65f3000 r-xp 00000000 08:15 2180985    /usr/lib/evolution/2.10/plugins/liborg-gnome-evolution-hula-account-setup.so
 b65f3000-b65f4000 rw-p 00003000 08:15 2180985    /usr/lib/evolution/2.10/plugins/liborg-gnome-evolution-hula-account-setup.so
 b65f4000-b6613000 r--p 00000000 08:15 1820646    /usr/share/locale-langpack/en_GB/LC_MESSAGES/libc.mo
 b6613000-b6619000 r-xp 00000000 08:15 1474617    /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-xpm.so
 b6619000-b661a000 rw-p 00005000 08:15 1474617    /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-xpm.so
 b661a000-b666f000 r--p 00000000 08:15 1820503    /usr/share/locale-langpack/en_GB/LC_MESSAGES/evolution-2.10.mo
 b666f000-b6670000 r-xp 00000000 08:15 1412676    /usr/lib/gconv/ISO8859-1.so
 b6670000-b6672000 rw-p 00000000 08:15 1412676    /usr/lib/gconv/ISO8859-1.so
 b6672000-b6692000 r--p 00000000 08:15 1820861    /usr/share/locale-langpack/en_GB/LC_MESSAGES/gtk20-properties.mo
 b6692000-b66a1000 r--p 00000000 08:15 1820814    /usr/share/locale-langpack/en_GB/LC_MESSAGES/gtk20.mo
 b66a1000-b66dc000 r--p 00000000 08:15 1475490    /usr/lib/locale/en_GB.utf8/LC_CTYPE
 b66dc000-b66dd000 r--p 00000000 08:15 1475495    /usr/lib/locale/en_GB.utf8/LC_NUMERIC
 b66dd000-b66de000 r--p 00000000 08:15 1475498    /usr/lib/locale/en_GB.utf8/LC_TIME
 b66de000-b67b5000 r--p 00000000 08:15 1475489    /usr/lib/locale/en_GB.utf8/LC_COLLATE
 b67b5000-b67be000 r-xp 00000000 08:15 1215733    /lib/tls/i686/cmov/libnss_files-2.5.so
 b67be000-b67c0000 rw-p 00008000 08:15 1215733    /lib/tls/i686/cmov/libnss_files-2.5.so
 b67c0000-b67c8000 r-xp 00000000 08:15 1215737    /lib/tls/i686/cmov/libnss_nis-2.5.so
 b67c8000-b67ca000 rw-p 00007000 08:15 1215737    /lib/tls/i686/cmov/libnss_nis-2.5.so
 b67ca000-b67d1000 r-xp 00000000 08:15 1215729    /lib/tls/i686/cmov/libnss_compat-2.5.so
 b67d1000-b67d3000 rw-p 00006000 08:15 1215729    /lib/tls/i686/cmov/libnss_compat-2.5.so
 b67d3000-b67d8000 rw-p b67d3000 00:00 0 
 b67d8000-b67db000 r-xp 00000000 08:15 1413235    /usr/lib/libkrb5support.so.0.0
 b67db000-b67dc000 rw-p 00003000 08:15 1413235    /usr/lib/libkrb5support.so.0.0
 b67dc000-b689c000 r-xp 00000000 08:15 1410614    /usr/lib/libasound.so.2.0.0
 b689c000-b68a1000 rw-p 000bf000 08:15 1410614    /usr/lib/libasound.so.2.0.0
 b68a1000-b68d7000 r-xp 00000000 08:15 1212534    /lib/libsepol.so.1
 b68d7000-b68d8000 rw-p 00035000 08:15 1212534    /lib/libsepol.so.1
 b68d8000-b68e3000 rw-p b68d8000 00:00 0 
 b68e3000-b68e6000 r-xp 00000000 08:15 1410902    /usr/lib/libgpg-error.so.0.3.0
 b68e6000-b68e7000 rw-p 00002000 08:15 1410902    /usr/lib/libgpg-error.so.0.3.0
 b68e7000-b6936000 r-xp 00000000 08:15 1410790    /usr/lib/libgcrypt.so.11.2.2
 b6936000-b6938000 rw-p 0004e000 08:15 1410790    /usr/lib/libgcrypt.so.11.2.2
 b6938000-b694c000 r-xp 00000000 08:15 1411246    /usr/lib/libtasn1.so.3.0.6
 b694c000-b694d000 rw-p 00013000 08:15 1411246    /usr/lib/libtasn1.so.3.0.6
 b694d000-b694e000 rw-p b694d000 00:00 0 
 b694e000-b6952000 r-xp 00000000 08:15 1410560    /usr/lib/libXdmcp.so.6.0.0
 b6952000-b6953000 rw-p 00003000 08:15 1410560    /usr/lib/libXdmcp.so.6.0.0
 b6953000-b6971000 r-xp 00000000 08:15 1410745    /usr/lib/libexpat.so.1.0.0
 b6971000-b6973000 rw-p 0001d000 08:15 1410745    /usr/lib/libexpat.so.1.0.0
 b6973000-b6975000 r-xp 00000000 08:15 1410549    /usr/lib/libXau.so.6.0.0
 b6975000-b6976000 rw-p 00001000 08:15 1410549    /usr/lib/libXau.so.6.0.0
 b6976000-b6a71000 r-xp 00000000 08:15 1410685    /usr/lib/libdb-4.4.so
 b6a71000-b6a74000 rw-p 000fb000 08:15 1410685    /usr/lib/libdb-4.4.so
 b6a74000-b6a75000 rw-p b6a74000 00:00 0 
 b6a75000-b6a90000 r-xp 00000000 08:15 1411741    /usr/lib/libgssapi_krb5.so.2.2
 b6a90000-b6a91000 rw-p 0001b000 08:15 1411741    /usr/lib/libgssapi_krb5.so.2.2
 b6a91000-b6a93000 r-xp 00000000 08:15 1212464    /lib/libcom_err.so.2.1
 b6a93000-b6a94000 rw-p 00001000 08:15 1212464    /lib/libcom_err.so.2.1
 b6a94000-b6ab8000 r-xp 00000000 08:15 1413231    /usr/lib/libk5crypto.so.3.0
 b6ab8000-b6ab9000 rw-p 00024000 08:15 1413231    /usr/lib/libk5crypto.so.3.0
 b6ab9000-b6b34000 r-xp 00000000 08:15 1413234    /usr/lib/libkrb5.so.3.2
 b6b34000-b6b36000 rw-p 0007b000 08:15 1413234    /usr/lib/libkrb5.so.3.2
 b6b36000-b6b81000 r-xp 00000000 08:15 1413247    /usr/lib/libsoftokn3.so
 b6b81000-b6b85000 rw-p 0004b000 08:15 1413247    /usr/lib/libsoftokn3.so
 b6b85000-b6b86000 rw-p b6b85000 00:00 0 
 b6b86000-b6bae000 r-xp 00000000 08:15 1413248    /usr/lib/libssl3.so
 b6bae000-b6bb0000 rw-p 00027000 08:15 1413248    /usr/lib/libssl3.so
 b6bb0000-b6bd2000 r-xp 00000000 08:15 1413246    /usr/lib/libsmime3.so
 b6bd2000-b6bd4000 rw-p 00022000 08:15 1413246    /usr/lib/libsmime3.so
 b6bd4000-b6c41000 r-xp 00000000 08:15 1413245    /usr/lib/libnss3.so
 b6c41000-b6c46000 rw-p 0006d000 08:15 1413245    /usr/lib/libnss3.so
 b6c46000-b6c59000 r-xp 00000000 08:15 1215727    /lib/tls/i686/cmov/libnsl-2.5.so
 b6c59000-b6c5b000 rw-p 00012000 08:15 1215727    /lib/tls/i686/cmov/libnsl-2.5.so
 b6c5b000-b6c5d000 rw-p b6c5b000 00:00 0 
 b6c5d000-b6c63000 r-xp 00000000 08:15 1410771    /usr/lib/libgailutil.so.18.0.1
 b6c63000-b6c64000 rw-p 00006000 08:15 1410771    /usr/lib/libgailutil.so.18.0.1
 b6c64000-b6c65000 rw-p b6c64000 00:00 0 
 b6c65000-b6c69000 r-xp 00000000 08:15 1410535    /usr/lib/libORBitCosNaming-2.so.0.1.0
 b6c69000-b6c6a000 rw-p 00003000 08:15 1410535    /usr/lib/libORBitCosNaming-2.so.0.1.0
 b6c6a000-b6cd2000 r-xp 00000000 08:15 1410677    /usr/lib/libfreetype.so.6.3.10
 b6cd2000-b6cd5000 rw-p 00068000 08:15 1410677    /usr/lib/libfreetype.so.6.3.10
 b6cd5000-b6cf5000 r-xp 00000000 08:15 1410626    /usr/lib/libaudiofile.so.0.0.2
 b6cf5000-b6cf7000 rw-p 00020000 08:15 1410626    /usr/lib/libaudiofile.so.0.0.2
 b6cf7000-b6cf8000 rw-p b6cf7000 00:00 0 
 b6cf8000-b6d01000 r-xp 00000000 08:15 1410736    /usr/lib/libesd.so.0.2.36
 b6d01000-b6d02000 rw-p 00009000 08:15 1410736    /usr/lib/libesd.so.0.2.36
 b6d02000-b6d04000 r-xp 00000000 08:15 1215750    /lib/tls/i686/cmov/libutil-2.5.so
 b6d04000-b6d06000 rw-p 00001000 08:15 1215750    /lib/tls/i686/cmov/libutil-2.5.so
 b6d06000-b6d1a000 r-xp 00000000 08:15 1212533    /lib/libselinux.so.1
 b6d1a000-b6d1c000 rw-p 00013000 08:15 1212533    /lib/libselinux.so.1
 b6d1c000-b6d2b000 r-xp 00000000 08:15 1215744    /lib/tls/i686/cmov/libresolv-2.5.so
 b6d2b000-b6d2d000 rw-p 0000f000 08:15 1215744    /lib/tls/i686/cmov/libresolv-2.5.so
 b6d2d000-b6d2f000 rw-p b6d2d000 00:00 0 
 b6d2f000-b6d3d000 r-xp 00000000 08:15 1410628    /usr/lib/libavahi-client.so.3.2.2
 b6d3d000-b6d3e000 rw-p 0000e000 08:15 1410628    /usr/lib/libavahi-client.so.3.2.2
 b6d3e000-b6d3f000 rw-p b6d3e000 00:00 0 
 b6d3f000-b6d49000 r-xp 00000000 08:15 1410630    /usr/lib/libavahi-common.so.3.4.3
 b6d49000-b6d4a000 rw-p 00009000 08:15 1410630    /usr/lib/libavahi-common.so.3.4.3
 b6d4a000-b6d4c000 r-xp 00000000 08:15 1410634    /usr/lib/libavahi-glib.so.1.0.1
 b6d4c000-b6d4d000 rw-p 00001000 08:15 1410634    /usr/lib/libavahi-glib.so.1.0.1
 b6d4d000-b6db7000 r-xp 00000000 08:15 1410898    /usr/lib/libgnutls.so.13.0.9
 b6db7000-b6dbd000 rw-p 0006a000 08:15 1410898    /usr/lib/libgnutls.so.13.0.9
 b6dbd000-b6ddb000 r-xp 00000000 08:15 1411027    /usr/lib/libjpeg.so.62.0.0
 b6ddb000-b6ddc000 rw-p 0001d000 08:15 1411027    /usr/lib/libjpeg.so.62.0.0
 b6ddc000-b6ddd000 rw-p b6ddc000 00:00 0 
 b6ddd000-b6df0000 r-xp 00000000 08:15 2180932    /usr/lib/evolution/2.10/libevolution-a11y.so.0.0.0
 b6df0000-b6df1000 rw-p 00012000 08:15 2180932    /usr/lib/evolution/2.10/libevolution-a11y.so.0.0.0
 b6df1000-b6df9000 r-xp 00000000 08:15 2180939    /usr/lib/evolution/2.10/libevolution-widgets-a11y.so.0.0.0
 b6df9000-b6dfa000 rw-p 00007000 08:15 2180939    /usr/lib/evolution/2.10/libevolution-widgets-a11y.so.0.0.0
 b6dfa000-b6e14000 r-xp 00000000 08:15 2180929    /usr/lib/evolution/2.10/libetext.so.0.0.0
 b6e14000-b6e15000 rw-p 0001a000 08:15 2180929    /usr/lib/evolution/2.10/libetext.so.0.0.0
 b6e15000-b6e84000 r-xp 00000000 08:15 2180928    /usr/lib/evolution/2.10/libetable.so.0.0.0
 b6e84000-b6e87000 rw-p 0006e000 08:15 2180928    /usr/lib/evolution/2.10/libetable.so.0.0.0
 b6e87000-b6e88000 rw-p b6e87000 00:00 0 
 b6e88000-b6e8e000 r-xp 00000000 08:15 1411106    /usr/lib/libnotify.so.1.1.1
 b6e8e000-b6e8f000 rw-p 00006000 08:15 1411106    /usr/lib/libnotify.so.1.1.1
 b6e8f000-b6e9a000 r-xp 00000000 08:15 1409432    /usr/lib/libhal.so.1.0.0
 b6e9a000-b6e9b000 rw-p 0000b000 08:15 1409432    /usr/lib/libhal.so.1.0.0
 b6e9b000-b6e9d000 r-xp 00000000 08:15 1215722    /lib/tls/i686/cmov/libdl-2.5.so
 b6e9d000-b6e9f000 rw-p 00001000 08:15 1215722    /lib/tls/i686/cmov/libdl-2.5.so
 b6e9f000-b6ec4000 r-xp 00000000 08:15 1215724    /lib/tls/i686/cmov/libm-2.5.so
 b6ec4000-b6ec6000 rw-p 00024000 08:15 1215724    /lib/tls/i686/cmov/libm-2.5.so
 b6ec6000-b6ec7000 rw-p b6ec6000 00:00 0 
 b6ec7000-b6fb4000 r-xp 00000000 08:15 1410543    /usr/lib/libX11.so.6.2.0
 b6fb4000-b6fb8000 rw-p 000ed000 08:15 1410543    /usr/lib/libX11.so.6.2.0
 b6fb8000-b6fbf000 r-xp 00000000 08:15 1410586    /usr/lib/libXrender.so.1.3.0
 b6fbf000-b6fc0000 rw-p 00006000 08:15 1410586    /usr/lib/libXrender.so.1.3.0
 b6fc0000-b6fe2000 r-xp 00000000 08:15 1410822    /usr/lib/libpng12.so.0.15.0
 b6fe2000-b6fe3000 rw-p 00021000 08:15 1410822    /usr/lib/libpng12.so.0.15.0
 b6fe3000-b7006000 r-xp 00000000 08:15 1410751    /usr/lib/libfontconfig.so.1.2.0
 b7006000-b700e000 rw-p 00023000 08:15 1410751    /usr/lib/libfontconfig.so.1.2.0
 b700e000-b7021000 r-xp 00000000 08:15 1411304    /usr/lib/libz.so.1.2.3
 b7021000-b7022000 rw-p 00012000 08:15 1411304    /usr/lib/libz.so.1.2.3
 b7022000-b7026000 r-xp 00000000 08:15 1410566    /usr/lib/libXfixes.so.3.1.0
 b7026000-b7027000 rw-p 00003000 08:15 1410566    /usr/lib/libXfixes.so.3.1.0
 b7027000-b7028000 rw-p b7027000 00:00 0 
 b7028000-b7030000 r-xp 00000000 08:15 1410556    /usr/lib/libXcursor.so.1.0.2
 b7030000-b7031000 rw-p 00007000 08:15 1410556    /usr/lib/libXcursor.so.1.0.2
 b7031000-b7036000 r-xp 00000000 08:15 1410584    /usr/lib/libXrandr.so.2.1.0
 b7036000-b7037000 rw-p 00005000 08:15 1410584    /usr/lib/libXrandr.so.2.1.0
 b7037000-b703e000 r-xp 00000000 08:15 1410572    /usr/lib/libXi.so.6.0.0
 b703e000-b703f000 rw-p 00006000 08:15 1410572    /usr/lib/libXi.so.6.0.0
 b703f000-b7041000 r-xp 00000000 08:15 1410574    /usr/lib/libXinerama.so.1.0.0
 b7041000-b7042000 rw-p 00001000 08:15 1410574    /usr/lib/libXinerama.so.1.0.0
 b7042000-b704f000 r-xp 00000000 08:15 1410564    /usr/lib/libXext.so.6.4.0
 b704f000-b7050000 rw-p 0000d000 08:15 1410564    /usr/lib/libXext.so.6.4.0
 b7050000-b7057000 r-xp 00000000 08:15 1215746    /lib/tls/i686/cmov/librt-2.5.so
 b7057000-b7059000 rw-p 00006000 08:15 1215746    /lib/tls/i686/cmov/librt-2.5.so
 b7059000-b705a000 rw-p b7059000 00:00 0 
 b705a000-b706d000 r-xp 00000000 08:15 1215742    /lib/tls/i686/cmov/libpthread-2.5.so
 b706d000-b706f000 rw-p 00013000 08:15 1215742    /lib/tls/i686/cmov/libpthread-2.5.so
 b706f000-b7071000 rw-p b706f000 00:00 0 
 b7071000-b71ac000 r-xp 00000000 08:15 1215716    /lib/tls/i686/cmov/libc-2.5.so
 b71ac000-b71ad000 r--p 0013b000 08:15 1215716    /lib/tls/i686/cmov/libc-2.5.so
 b71ad000-b71af000 rw-p 0013c000 08:15 1215716    /lib/tls/i686/cmov/libc-2.5.so
 b71af000-b71b2000 rw-p b71af000 00:00 0 
 b71b2000-b71e1000 r-xp 00000000 08:15 1409205    /usr/lib/libnspr4.so
 b71e1000-b71e2000 rw-p 0002f000 08:15 1409205    /usr/lib/libnspr4.so
 b71e2000-b71e4000 rw-p b71e2000 00:00 0 
 b71e4000-b71e8000 r-xp 00000000 08:15 1410720    /usr/lib/libplc4.so
 b71e8000-b71e9000 rw-p 00003000 08:15 1410720    /usr/lib/libplc4.so
 b71e9000-b71eb000 r-xp 00000000 08:15 1413242    /usr/lib/libplds4.so
 b71eb000-b71ec000 rw-p 00001000 08:15 1413242    /usr/lib/libplds4.so
 b71ec000-b720f000 r-xp 00000000 08:15 1409203    /usr/lib/libedataserver-1.2.so.9.0.0
 b720f000-b7210000 rw-p 00023000 08:15 1409203    /usr/lib/libedataserver-1.2.so.9.0.0
 b7210000-b7211000 rw-p b7210000 00:00 0 
 b7211000-b7240000 r-xp 00000000 08:15 1410658    /usr/lib/libebook-1.2.so.9.0.1
 b7240000-b7244000 rw-p 0002e000 08:15 1410658    /usr/lib/libebook-1.2.so.9.0.1
 b7244000-b726a000 r-xp 00000000 08:15 1409430    /usr/lib/libedataserverui-1.2.so.8.0.1
 b726a000-b726b000 rw-p 00025000 08:15 1409430    /usr/lib/libedataserverui-1.2.so.8.0.1
 b726b000-b72d1000 r-xp 00000000 08:15 1410882    /usr/lib/libgnomeprint-2-2.so.0.1.0
 b72d1000-b72d3000 rw-p 00065000 08:15 1410882    /usr/lib/libgnomeprint-2-2.so.0.1.0
 b72d3000-b7311000 r-xp 00000000 08:15 1410884    /usr/lib/libgnomeprintui-2-2.so.0.1.0
 b7311000-b7313000 rw-p 0003d000 08:15 1410884    /usr/lib/libgnomeprintui-2-2.so.0.1.0
 b7313000-b7328000 r-xp 00000000 08:15 1410521    /usr/lib/libICE.so.6.3.0
 b7328000-b732a000 rw-p 00014000 08:15 1410521    /usr/lib/libICE.so.6.3.0
 b732a000-b732b000 rw-p b732a000 00:00 0 
 b732b000-b7333000 r-xp 00000000 08:15 1410539    /usr/lib/libSM.so.6.0.0
 b7333000-b7334000 rw-p 00007000 08:15 1410539    /usr/lib/libSM.so.6.0.0
 b7334000-b7335000 rw-p b7334000 00:00 0 
 b7335000-b737d000 r-xp 00000000 08:15 1410758    /usr/lib/libcamel-1.2.so.10.0.0
 b737d000-b7380000 rw-p 00048000 08:15 1410758    /usr/lib/libcamel-1.2.so.10.0.0
 b7380000-b73ce000 r-xp 00000000 08:15 1411223    /usr/lib/libcamel-provider-1.2.so.10.0.0
 b73ce000-b73d0000 rw-p 0004d000 08:15 1411223    /usr/lib/libcamel-provider-1.2.so.10.0.0
 b73d0000-b7402000 r-xp 00000000 08:15 1409769    /usr/lib/libdbus-1.so.3.2.0
 b7402000-b7403000 rw-p 00031000 08:15 1409769    /usr/lib/libdbus-1.so.3.2.0
 b7403000-b741d000 r-xp 00000000 08:15 1410689    /usr/lib/libdbus-glib-1.so.2.1.0
 b741d000-b741e000 rw-p 0001a000 08:15 1410689    /usr/lib/libdbus-glib-1.so.2.1.0
 b741e000-b74af000 r-xp 00000000 08:15 1410712    /usr/lib/libecal-1.2.so.7.0.1
 b74af000-b74be000 rw-p 00090000 08:15 1410712    /usr/lib/libecal-1.2.so.7.0.1
 b74be000-b74c2000 rw-p b74be000 00:00 0 
 b74c2000-b755f000 r-xp 00000000 08:15 1410961    /usr/lib/libgtkhtml-3.14.so.19.0.0
 b755f000-b7563000 rw-p 0009c000 08:15 1410961    /usr/lib/libgtkhtml-3.14.so.19.0.0
 b7563000-b7565000 rw-p b7563000 00:00 0 
 b7565000-b7569000 r-xp 00000000 08:15 1411104    /usr/lib/libnm_glib.so.0.0.0
 b7569000-b756a000 rw-p 00004000 08:15 1411104    /usr/lib/libnm_glib.so.0.0.0
 b756a000-b75fe000 r-xp 00000000 08:15 1410846    /usr/lib/libglib-2.0.so.0.1200.11
 b75fe000-b75ff000 rw-p 00093000 08:15 1410846    /usr/lib/libglib-2.0.so.0.1200.11
 b75ff000-b7638000 r-xp 00000000 08:15 1410900    /usr/lib/libgobject-2.0.so.0.1200.11
 b7638000-b7639000 rw-p 00039000 08:15 1410900    /usr/lib/libgobject-2.0.so.0.1200.11
 b7639000-b763b000 r-xp 00000000 08:15 1410856    /usr/lib/libgmodule-2.0.so.0.1200.11
 b763b000-b763c000 rw-p 00002000 08:15 1410856    /usr/lib/libgmodule-2.0.so.0.1200.11
 b763c000-b76aa000 r-xp 00000000 08:15 1410653    /usr/lib/libcairo.so.2.11.1
 b76aa000-b76ac000 rw-p 0006d000 08:15 1410653    /usr/lib/libcairo.so.2.11.1
 b76ac000-b76ad000 rw-p b76ac000 00:00 0 
 b76ad000-b76e9000 r-xp 00000000 08:15 1411133    /usr/lib/libpango-1.0.so.0.1600.2
 b76e9000-b76eb000 rw-p 0003b000 08:15 1411133    /usr/lib/libpango-1.0.so.0.1600.2
 b76eb000-b76f2000 r-xp 00000000 08:15 1411135    /usr/lib/libpangocairo-1.0.so.0.1600.2
 b76f2000-b76f3000 rw-p 00007000 08:15 1411135    /usr/lib/libpangocairo-1.0.so.0.1600.2
 b76f3000-b7709000 r-xp 00000000 08:15 1410810    /usr/lib/libgdk_pixbuf-2.0.so.0.1000.11
 b7709000-b770a000 rw-p 00015000 08:15 1410810    /usr/lib/libgdk_pixbuf-2.0.so.0.1000.11
 b770a000-b7723000 r-xp 00000000 08:15 1410620    /usr/lib/libatk-1.0.so.0.1809.1
 b7723000-b7725000 rw-p 00018000 08:15 1410620    /usr/lib/libatk-1.0.so.0.1809.1
 b7725000-b77a8000 r-xp 00000000 08:15 1410808    /usr/lib/libgdk-x11-2.0.so.0.1000.11
 b77a8000-b77ab000 rw-p 00083000 08:15 1410808    /usr/lib/libgdk-x11-2.0.so.0.1000.11
 b77ab000-b78c2000 r-xp 00000000 08:15 1411298    /usr/lib/libxml2.so.2.6.27
 b78c2000-b78c8000 rw-p 00116000 08:15 1411298    /usr/lib/libxml2.so.2.6.27
 b78c8000-b78c9000 rw-p b78c8000 00:00 0 
 b78c9000-b7c1a000 r-xp 00000000 08:15 1410957    /usr/lib/libgtk-x11-2.0.so.0.1000.11
 b7c1a000-b7c20000 rw-p 00351000 08:15 1410957    /usr/lib/libgtk-x11-2.0.so.0.1000.11
 b7c20000-b7c21000 rw-p b7c20000 00:00 0 
 b7c21000-b7c25000 r-xp 00000000 08:15 1410954    /usr/lib/libgthread-2.0.so.0.1200.11
 b7c25000-b7c26000 rw-p 00003000 08:15 1410954    /usr/lib/libgthread-2.0.so.0.1200.11
 b7c26000-b7c6f000 r-xp 00000000 08:15 1410531    /usr/lib/libORBit-2.so.0.1.0
 b7c6f000-b7c79000 rw-p 00048000 08:15 1410531    /usr/lib/libORBit-2.so.0.1.0
 b7c79000-b7ca8000 r-xp 00000000 08:15 1410788    /usr/lib/libgconf-2.so.4.1.2
 b7ca8000-b7cab000 rw-p 0002e000 08:15 1410788    /usr/lib/libgconf-2.so.4.1.2
 b7cab000-b7cbe000 r-xp 00000000 08:15 1410647    /usr/lib/libbonobo-activation.so.4.0.0
 b7cbe000-b7cc0000 rw-p 00013000 08:15 1410647    /usr/lib/libbonobo-activation.so.4.0.0
 b7cc0000-b7d12000 r-xp 00000000 08:15 1410645    /usr/lib/libbonobo-2.so.0.0.0
 b7d12000-b7d1c000 rw-p 00051000 08:15 1410645    /usr/lib/libbonobo-2.so.0.0.0
 b7d1c000-b7d1d000 rw-p b7d1c000 00:00 0 
 b7d1d000-b7d47000 r-xp 00000000 08:15 1411137    /usr/lib/libpangoft2-1.0.so.0.1600.2
 b7d47000-b7d48000 rw-p 0002a000 08:15 1411137    /usr/lib/libpangoft2-1.0.so.0.1600.2
 b7d48000-b7d5c000 r-xp 00000000 08:15 1410612    /usr/lib/libart_lgpl_2.so.2.3.17
 b7d5c000-b7d5d000 rw-p 00013000 08:15 1410612    /usr/lib/libart_lgpl_2.so.2.3.17
 b7d5d000-b7d64000 r-xp 00000000 08:15 1212523    /lib/libpopt.so.0.0.0
 b7d64000-b7d65000 rw-p 00006000 08:15 1212523    /lib/libpopt.so.0.0.0
 b7d65000-b7d79000 r-xp 00000000 08:15 1410858    /usr/lib/libgnome-2.so.0.1800.0
 b7d79000-b7d7a000 rw-p 00014000 08:15 1410858    /usr/lib/libgnome-2.so.0.1800.0
 b7d7a000-b7da3000 r-xp 00000000 08:15 1410872    /usr/lib/libgnomecanvas-2.so.0.1400.0
 b7da3000-b7da4000 rw-p 00029000 08:15 1410872    /usr/lib/libgnomecanvas-2.so.0.1400.0
 b7da4000-b7db0000 r-xp 00000000 08:15 1410862    /usr/lib/libgnome-keyring.so.0.0.1
 b7db0000-b7db1000 rw-p 0000b000 08:15 1410862    /usr/lib/libgnome-keyring.so.0.0.1
 b7db1000-b7db2000 rw-p b7db1000 00:00 0 
 b7db2000-b7e08000 r-xp 00000000 08:15 1410890    /usr/lib/libgnomevfs-2.so.0.1800.1
 b7e08000-b7e0b000 rw-p 00055000 08:15 1410890    /usr/lib/libgnomevfs-2.so.0.1800.1
 b7e0b000-b7e66000 r-xp 00000000 08:15 1410649    /usr/lib/libbonoboui-2.so.0.0.0
 b7e66000-b7e69000 rw-p 0005a000 08:15 1410649    /usr/lib/libbonoboui-2.so.0.0.0
 b7e69000-b7e80000 r-xp 00000000 08:15 1410844    /usr/lib/libglade-2.0.so.0.0.7
 b7e80000-b7e81000 rw-p 00016000 08:15 1410844    /usr/lib/libglade-2.0.so.0.0.7
 b7e81000-b7f0b000 r-xp 00000000 08:15 1410888    /usr/lib/libgnomeui-2.so.0.1788.4
 b7f0b000-b7f0f000 rw-p 00089000 08:15 1410888    /usr/lib/libgnomeui-2.so.0.1788.4
 b7f0f000-b7f12000 r-xp 00000000 08:15 1411039    /usr/lib/liblaunchpad-integration.so.0.0.0
 b7f12000-b7f13000 rw-p 00002000 08:15 1411039    /usr/lib/liblaunchpad-integration.so.0.0.0
 b7f13000-b7f14000 rw-p b7f13000 00:00 0 
 b7f14000-b7f16000 r-xp 00000000 08:15 1411054    /usr/lib/liblpint-bonobo.so.0.0.0
 b7f16000-b7f17000 rw-p 00001000 08:15 1411054    /usr/lib/liblpint-bonobo.so.0.0.0
 b7f17000-b7f18000 r--p 00000000 08:15 1475493    /usr/lib/locale/en_GB.utf8/LC_MONETARY
 b7f18000-b7f19000 r--p 00000000 08:15 1475499    /usr/lib/locale/en_GB.utf8/LC_MESSAGES/SYS_LC_MESSAGES
 b7f19000-b7f1a000 r--p 00000000 08:15 1475496    /usr/lib/locale/en_GB.utf8/LC_PAPER
 b7f1a000-b7f1b000 r--p 00000000 08:15 1475494    /usr/lib/locale/en_GB.utf8/LC_NAME
 b7f1b000-b7f1c000 r--p 00000000 08:15 1475488    /usr/lib/locale/en_GB.utf8/LC_ADDRESS
 b7f1c000-b7f1d000 r--p 00000000 08:15 1475497    /usr/lib/locale/en_GB.utf8/LC_TELEPHONE
 b7f1d000-b7f1e000 r--p 00000000 08:15 1475492    /usr/lib/locale/en_GB.utf8/LC_MEASUREMENT
 b7f1e000-b7f25000 r--s 00000000 08:15 1412729    /usr/lib/gconv/gconv-modules.cache
 b7f25000-b7f26000 r--p 00000000 08:15 1475491    /usr/lib/locale/en_GB.utf8/LC_IDENTIFICATION
 b7f26000-b7f54000 r-xp 00000000 08:15 2180931    /usr/lib/evolution/2.10/libeutil.so.0.0.0
 b7f54000-b7f56000 rw-p 0002e000 08:15 2180931    /usr/lib/evolution/2.10/libeutil.so.0.0.0
 b7f56000-b7faf000 r-xp 00000000 08:15 2180925    /usr/lib/evolution/2.10/libemiscwidgets.so.0.0.0
 b7faf000-b7fb4000 rw-p 00058000 08:15 2180925    /usr/lib/evolution/2.10/libemiscwidgets.so.0.0.0
 b7fb4000-b7fb8000 r-xp 00000000 08:15 2180930    /usr/lib/evolution/2.10/libetimezonedialog.so.0.0.0
 b7fb8000-b7fb9000 rw-p 00003000 08:15 2180930    /usr/lib/evolution/2.10/libetimezonedialog.so.0.0.0
 b7fb9000-b7fc6000 r-xp 00000000 08:15 2180926    /usr/lib/evolution/2.10/libeshell.so.0.0.0
 b7fc6000-b7fc8000 rw-p 0000c000 08:15 2180926    /usr/lib/evolution/2.10/libeshell.so.0.0.0
 b7fc8000-b7fca000 rw-p b7fc8000 00:00 0 
 b7fca000-b7fe3000 r-xp 00000000 08:15 1212437    /lib/ld-2.5.so
 b7fe3000-b7fe5000 rw-p 00019000 08:15 1212437    /lib/ld-2.5.so
 bfaee000-bfb04000 rw-p bfaee000 00:00 0          [stack]
 ffffe000-fffff000 r-xp 00000000 00:00 0          [vdso]
ProcStatus:
 Name:	evolution
 State:	S (sleeping)
 SleepAVG:	68%
 Tgid:	20029
 Pid:	20029
 PPid:	7200
 TracerPid:	0
 Uid:	1000	1000	1000	1000
 Gid:	1000	1000	1000	1000
 FDSize:	256
 Groups:	4 20 24 25 29 30 44 46 104 112 113 115 117 1000 
 VmPeak:	   41464 kB
 VmSize:	   41404 kB
 VmLck:	       0 kB
 VmHWM:	   13132 kB
 VmRSS:	   13132 kB
 VmData:	    1528 kB
 VmStk:	      88 kB
 VmExe:	     116 kB
 VmLib:	   27272 kB
 VmPTE:	      48 kB
 Threads:	1
 SigQ:	0/4294967295
 SigPnd:	0000000000000000
 ShdPnd:	0000000000000000
 SigBlk:	0000000000000000
 SigIgn:	0000000000001000
 SigCgt:	0000000180000000
 CapInh:	0000000000000000
 CapPrm:	0000000000000000
 CapEff:	0000000000000000
 Cpus_allowed:	01
 Mems_allowed:	1
Signal: 11
Uname: Linux richards 2.6.20-16-generic #2 SMP Sun Sep 23 19:50:39 UTC 2007 i686 GNU/Linux
UserGroups: adm admin audio cdrom dialout dip floppy lpadmin netdev plugdev powerdev scanner video
CoreDump: base64
```

Please help, any one got any ideas?

---

### Post by rich86 on 2007-10-21
*bump*

---

### Post by rich86 on 2007-10-21
please help someone, i have an update though i found a log of the error i wrote in the first post in the ".xsession-errors" file in my home folder so i guess there is something wrong with X causing evolution to crash.
Any one any ideas down that path?
Here is the bug trace
```

 gdb evolution
GNU gdb 6.6-debian
Copyright (C) 2006 Free Software Foundation, Inc.
GDB is free software, covered by the GNU General Public License, and you are
welcome to change it and/or distribute copies of it under certain conditions.
Type "show copying" to see the conditions.
There is absolutely no warranty for GDB.  Type "show warranty" for details.
This GDB was configured as "i486-linux-gnu"...
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
(gdb) run
Starting program: /usr/bin/evolution 
[Thread debugging using libthread_db enabled]
[New Thread -1233996096 (LWP 22804)]
CalDAV Eplugin starting up ...

(evolution-2.10:22804): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `EImportHook'

(evolution-2.10:22804): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(evolution-2.10:22804): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `(null)'

(evolution-2.10:22804): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(evolution-2.10:22804): GLib-GObject-WARNING **: invalid uninstantiatable type `(null)' in cast to `ESourceGroup'

(evolution-2.10:22804): e-data-server-CRITICAL **: e_source_group_peek_base_uri: assertion `E_IS_SOURCE_GROUP (group)' failed

Program received signal SIGSEGV, Segmentation fault.
[Switching to Thread -1233996096 (LWP 22804)]
0xb644ecb0 in calendar_component_init (component=0x80ed3b0) at calendar-component.c:199
199     calendar-component.c: No such file or directory.
        in calendar-component.c
(gdb) 
(gdb) 
(gdb) thread apply all bt

Thread 1 (Thread -1233996096 (LWP 22804)):
#0  0xb644ecb0 in calendar_component_init (component=0x80ed3b0) at calendar-component.c:199
#1  0xb7581759 in g_type_create_instance () from /usr/lib/libgobject-2.0.so.0
#2  0xb7568802 in ?? () from /usr/lib/libgobject-2.0.so.0
#3  0x080d5498 in ?? ()
#4  0xb7033e30 in free () from /lib/tls/i686/cmov/libc.so.6
#5  0xb7c3e741 in ?? () from /usr/lib/libbonobo-2.so.0
#6  0x080d5498 in ?? ()
#7  0x00000001 in ?? ()
#8  0x080d54c8 in ?? ()
#9  0x00000010 in ?? ()
#10 0x080679b8 in ?? ()
#11 0x00000001 in ?? ()
#12 0x00000002 in ?? ()
#13 0x08067dc0 in ?? ()
#14 0x00000008 in ?? ()
#15 0x080c2080 in ?? ()
#16 0xbf8124a8 in ?? ()
#17 0xb7590670 in ?? () from /usr/lib/libgobject-2.0.so.0
#18 0x0806d6f0 in ?? ()
#19 0x080c206c in ?? ()
#20 0xbf8124a8 in ?? ()
#21 0xb7590670 in ?? () from /usr/lib/libgobject-2.0.so.0
#22 0x0806d6f0 in ?? ()
#23 0x080c206c in ?? ()
#24 0xbf8125c8 in ?? ()
#25 0xb7566a7b in g_object_newv () from /usr/lib/libgobject-2.0.so.0
Backtrace stopped: frame did not save the PC
(gdb) 

```

---

