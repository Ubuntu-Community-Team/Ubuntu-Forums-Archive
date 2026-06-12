---
title: "Extra /lib directories in /?"
date: 2013-07-06
forum: General Help
---

### Post by Stonecold1995 on 2013-07-06
A few new directories are now present in / that I don't remember before.  I have /lib, /lib32, /lib64, and /libx32.  I don't remember ever having /libx32...  And I don't remember /lib32 either (I thought that was just /lib).  Are these suppose to be there?  If now, what added them?

```
alex@kubuntu:~$ ls /bin  boot  dead.letter  dev  etc  home  initrd.img  initrd.img.old  lib  lib32  lib64  libx32  lost+found  media  mnt  opt  proc  root  run  sbin  selinux  srv  sys  tmp  usr  var  vmlinuz  vmlinuz.old
alex@kubuntu:~$ ls /lib*
/lib:
apparmor    firmware        klibc-mYFhANOtcdgrJ6uSmDbFyxKe3NQ.so  libdmraid.so.1.0.0.rc16  libip4tc.so.0      libip6tc.so.0.0.0  libnss_mdns4_minimal.so.2  libnss_mdns_minimal.so.2  libxtables.so.7.0.0  modules     recovery-mode  udev
cpp         hdparm          ld-linux.so.2                         libhandle.so.1           libip4tc.so.0.0.0  libiptc.so         libnss_mdns4.so.2          libnss_mdns.so.2          linux-sound-base     nvidia-304  resolvconf     ufw
crda        i386-linux-gnu  libcryptsetup.so.4                    libhandle.so.1.0.3       libip6tc.so        libiptc.so.0       libnss_mdns6_minimal.so.2  libxtables.so             lsb                  oss-compat  systemd        x86_64-linux-gnu
cryptsetup  init            libcryptsetup.so.4.2.0                libip4tc.so              libip6tc.so.0      libiptc.so.0.0.0   libnss_mdns6.so.2          libxtables.so.7           modprobe.d           plymouth    terminfo       xtables


/lib32:
ld-2.17.so      libBrokenLocale-2.17.so  libcidn.so.1      libdl-2.17.so   libm.so.6              libnss_compat.so.2    libnss_files.so.2      libnss_nisplus-2.17.so  libpthread-2.17.so  librt-2.17.so        libthread_db.so.1
ld-linux.so.2   libBrokenLocale.so.1     libcrypt-2.17.so  libdl.so.2      libnsl-2.17.so         libnss_dns-2.17.so    libnss_hesiod-2.17.so  libnss_nisplus.so.2     libpthread.so.0     librt.so.1           libutil-2.17.so
libanl-2.17.so  libc-2.17.so             libcrypt.so.1     libm-2.17.so    libnsl.so.1            libnss_dns.so.2       libnss_hesiod.so.2     libnss_nis.so.2         libresolv-2.17.so   libSegFault.so       libutil.so.1
libanl.so.1     libcidn-2.17.so          libc.so.6         libmemusage.so  libnss_compat-2.17.so  libnss_files-2.17.so  libnss_nis-2.17.so     libpcprofile.so         libresolv.so.2      libthread_db-1.0.so


/lib64:
ld-linux-x86-64.so.2


/libx32:
ld-2.17.so         libBrokenLocale-2.17.so  libcidn.so.1      libdl-2.17.so   libm.so.6              libnss_compat.so.2    libnss_files.so.2      libnss_nisplus-2.17.so  libpthread-2.17.so  librt-2.17.so        libthread_db.so.1
ld-linux-x32.so.2  libBrokenLocale.so.1     libcrypt-2.17.so  libdl.so.2      libnsl-2.17.so         libnss_dns-2.17.so    libnss_hesiod-2.17.so  libnss_nisplus.so.2     libpthread.so.0     librt.so.1           libutil-2.17.so
libanl-2.17.so     libc-2.17.so             libcrypt.so.1     libm-2.17.so    libnsl.so.1            libnss_dns.so.2       libnss_hesiod.so.2     libnss_nis.so.2         libresolv-2.17.so   libSegFault.so       libutil.so.1
libanl.so.1        libcidn-2.17.so          libc.so.6         libmemusage.so  libnss_compat-2.17.so  libnss_files-2.17.so  libnss_nis-2.17.so     libpcprofile.so         libresolv.so.2      libthread_db-1.0.so
```

---

### Post by Kujua on 2013-07-08
> And I don't remember /lib32 either (I thought that was just /lib)
Are you running 64-bit version? If so /lib is for 64-bit libraries.
Did you install ia32-libs? /lib32 must have come from that.

Don't know about /libx32. This should show the package which created it:
```
dpkg -S /libx32
```

---

