---
title: "xen - dom0 running on edgy - getting glibc tls error"
date: 2006-11-08
forum: General Help
---

### Post by jkbrowne on 2006-11-08
Hello all,

I have edgy installed and booting a xen dom0 kernel.  The system boots fine and I can run unpriviledged domains successfully.  However, I'm getting the following error when the dom0 kernel boots:

```

  ***************************************************************
  ***************************************************************
  ** WARNING: Currently emulating unsupported memory accesses  **
  **          in /lib/tls glibc libraries. The emulation is    **
  **          slow. To ensure full performance you should      **
  **          install a 'xen-friendly' (nosegneg) version of   **
  **          the library, or disable tls support by executing **
  **          the following as root:                           **
  **          mv /lib/tls /lib/tls.disabled                    **
  ** Offending process: init (pid=1)                           **
  ***************************************************************
  ***************************************************************

```

Of course, I wanted to get the maximum performance from my xen box so I went looking for the "nosegneg" version of glibc.  After enabling some extra feeds in synaptic I found the libc6-xen package and installed it.  This package installed the following files:

```

/.
/etc
/etc/ld.so.conf.d
/etc/ld.so.conf.d/xen.conf
/lib
/lib/tls
/lib/tls/i686
/lib/tls/i686/cmov
/lib/tls/i686/cmov/nosegneg
/lib/tls/i686/cmov/nosegneg/ld-2.4.so
/lib/tls/i686/cmov/nosegneg/libanl-2.4.so
/lib/tls/i686/cmov/nosegneg/libBrokenLocale-2.4.so
/lib/tls/i686/cmov/nosegneg/libc-2.4.so
/lib/tls/i686/cmov/nosegneg/libcidn-2.4.so
/lib/tls/i686/cmov/nosegneg/libcrypt-2.4.so
/lib/tls/i686/cmov/nosegneg/libdl-2.4.so
/lib/tls/i686/cmov/nosegneg/libm-2.4.so
/lib/tls/i686/cmov/nosegneg/libmemusage.so
/lib/tls/i686/cmov/nosegneg/libnsl-2.4.so
/lib/tls/i686/cmov/nosegneg/libnss_compat-2.4.so
/lib/tls/i686/cmov/nosegneg/libnss_dns-2.4.so
/lib/tls/i686/cmov/nosegneg/libnss_files-2.4.so
/lib/tls/i686/cmov/nosegneg/libnss_hesiod-2.4.so
/lib/tls/i686/cmov/nosegneg/libnss_nis-2.4.so
/lib/tls/i686/cmov/nosegneg/libnss_nisplus-2.4.so
/lib/tls/i686/cmov/nosegneg/libpcprofile.so
/lib/tls/i686/cmov/nosegneg/libpthread-2.4.so
/lib/tls/i686/cmov/nosegneg/libresolv-2.4.so
/lib/tls/i686/cmov/nosegneg/librt-2.4.so
/lib/tls/i686/cmov/nosegneg/libSegFault.so
/lib/tls/i686/cmov/nosegneg/libthread_db-1.0.so
/lib/tls/i686/cmov/nosegneg/libutil-2.4.so
/usr
/usr/share
/usr/share/doc
/usr/share/doc/libc6-xen
/usr/share/doc/libc6-xen/changelog.Debian.gz
/usr/share/doc/libc6-xen/copyright
/usr/share/doc/libc6-xen/log-test-i686-linux-xen.gz
/usr/lib
/lib/tls/i686/cmov/nosegneg/ld-linux.so.2
/lib/tls/i686/cmov/nosegneg/libanl.so.1
/lib/tls/i686/cmov/nosegneg/libBrokenLocale.so.1
/lib/tls/i686/cmov/nosegneg/libc.so.6
/lib/tls/i686/cmov/nosegneg/libcidn.so.1
/lib/tls/i686/cmov/nosegneg/libcrypt.so.1
/lib/tls/i686/cmov/nosegneg/libdl.so.2
/lib/tls/i686/cmov/nosegneg/libm.so.6
/lib/tls/i686/cmov/nosegneg/libnsl.so.1
/lib/tls/i686/cmov/nosegneg/libnss_compat.so.2
/lib/tls/i686/cmov/nosegneg/libnss_dns.so.2
/lib/tls/i686/cmov/nosegneg/libnss_files.so.2
/lib/tls/i686/cmov/nosegneg/libnss_hesiod.so.2
/lib/tls/i686/cmov/nosegneg/libnss_nis.so.2
/lib/tls/i686/cmov/nosegneg/libnss_nisplus.so.2
/lib/tls/i686/cmov/nosegneg/libpthread.so.0
/lib/tls/i686/cmov/nosegneg/libresolv.so.2
/lib/tls/i686/cmov/nosegneg/librt.so.1
/lib/tls/i686/cmov/nosegneg/libthread_db.so.1
/lib/tls/i686/cmov/nosegneg/libutil.so.1

```

Unfortunately, installing this nosegneg glibc package did not fix the issue.  The same error still appears when I boot the dom0 kernel.

The ldconfig configuration appears to be correct:
```

jbrowne@ub1:~$ cat /etc/ld.so.conf.d/xen.conf
hwcap 0 nosegneg
jbrowne@ub1:~$ 

```

And ldd shows that /sbin/init is using the nosegneg glibc:

```

jbrowne@ub1:~$ ldd /sbin/init
        linux-gate.so.1 =>  (0xbfffe000)
        libc.so.6 => /lib/tls/i686/cmov/nosegneg/libc.so.6 (0xb7e8c000)
        /lib/ld-linux.so.2 (0xb7fcf000)
jbrowne@ub1:~$ 

```

I've re-run ldconfig manually, but it does not appear to help.  I'm a-bit confused at this point, so if anyone with xen experience has any suggestions I would very much appreciate them!

Thanks

---

### Post by kasper22 on 2006-11-10
did you do this:
mv /lib/tls /lib/tls.disabled 

That should fix the problem

---

### Post by tgal on 2006-11-23
Hello!

My problems with installation of xen-3.0.3 on Ubuntu 6.10 Server are exactly the same. I tried with and without libc6-xen, with and without moving away /lib/tls.

The warning keeps showing up in all cases ("offending process is init (pid=1)").

ldd /sbin/init says:

with libc6-xen installed and /lib/tls in place:

        linux-gate.so.1 =>  (0xbfffe000)
        libc.so.6 => /lib/tls/i686/cmov/nosegneg/libc.so.6 (0xb7e50000)
        /lib/ld-linux.so.2 (0xb7f8d000)

with /lib/tls moved away:

        linux-gate.so.1 =>  (0xbfffe000)
        libc.so.6 => /lib/libc.so.6 (0xb7e7a000)
        /lib/ld-linux.so.2 (0xb7fa0000)

I am lost now. What else might be the cause of the warning?

Is it impossible to run Xen without this tls compatibility mode on Ubuntu? Shall I use another distribution? Which one?


Thanks for every hint,
Tobias

---

### Post by David.Little on 2006-11-29
Hello

I am having the same trouble, ldd also seem to say it is using the nosegneg version.

I don't remember seeing this error when I was using the ubuntu kernel, but now I am using the downloaded binary from xensource and I get the error.

I can't use the ubuntu kernel as I get a kernel panic when I start a DomU using the ubuntu kernel as Dom0.

Does this help in figuring this out at all?

---

### Post by alben on 2006-12-12
I've found a patch in the current (unstable) Xen source [here]("http://lists.xensource.com/archives/html/xen-changelog/2006-10/msg00262.html"),

inserted the new code into *linux-2.6-xen-sparse/arch/i386/kernel/fixup.c* after line 48,
```

if (current->tgid == 1) /* Ignore statically linked init */
     return; 

```
and recomipled everything.

The warning has disappeared - no matter which TLS version i use. Currently I've this one selected:

```

#ldd /sbin/init

linux-gate.so.1 =>  (0xafffe000)
libc.so.6 => /lib/tls/i686/cmov/nosegneg/libc.so.6 (0xa7e61000)
/lib/ld-linux.so.2 (0xa7f9e000)

```

I'm not sure how to find out, if everything is working correctly and without simulation. Maybe someone know how to test the TLS feature. Maybe with some C code.

---

