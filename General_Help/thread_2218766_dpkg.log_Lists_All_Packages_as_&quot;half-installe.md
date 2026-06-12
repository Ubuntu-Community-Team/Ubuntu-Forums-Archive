---
title: "dpkg.log Lists All Packages as &quot;half-installed&quot; or &quot;half-configured&quot; on Trusty"
date: 2014-04-21
forum: General Help
---

### Post by taytaybongsong on 2014-04-21
I'm on a fresh install of Xubuntu Trusty here (after experiencing multiple issues in regard to ecnrypted swap and encrypted home on previous installs of both Xubuntu and plain Ubuntu, as detailed in my responses to this thread: [http://ubuntuforums.org/showthread.php?t=2217889](http://ubuntuforums.org/showthread.php?t=2217889)) and after hours of installing some packages I needed, and configuring everything from scratch, I noticed that Synaptic kept throwing out variations on the following message in its info/terminal window, after installing any package:
```
(synaptic:13647): GLib-CRITICAL **: g_child_watch_add_full: assertion 'pid > 0' failed
```
On a hunch, I decided to check out dpkg.log, and I noticed that the majority of package installations ended up as either "half-installed" or "half-configured", including packages from the Trusty install itself! To give you a sample, here are a few lines from the log file:
```
2014-04-16 18:26:47 trigproc libc-bin:amd64 2.19-0ubuntu6 <none>
2014-04-16 18:26:47 status half-configured libc-bin:amd64 2.19-0ubuntu6
2014-04-16 18:26:47 status installed libc-bin:amd64 2.19-0ubuntu6
2014-04-16 18:26:47 trigproc initramfs-tools:all 0.103ubuntu4 <none>
2014-04-16 18:26:47 status half-configured initramfs-tools:all 0.103ubuntu4
2014-04-16 18:26:47 status installed initramfs-tools:all 0.103ubuntu4
2014-04-16 18:27:54 startup archives unpack
2014-04-16 18:27:54 install install-info:amd64 <none> 5.2.0.dfsg.1-2
2014-04-16 18:27:54 status half-installed install-info:amd64 5.2.0.dfsg.1-2
2014-04-16 18:27:54 status unpacked install-info:amd64 5.2.0.dfsg.1-2
2014-04-16 18:27:54 status unpacked install-info:amd64 5.2.0.dfsg.1-2
2014-04-16 18:27:54 startup packages configure
2014-04-16 18:27:54 configure install-info:amd64 5.2.0.dfsg.1-2 <none>
2014-04-16 18:27:54 status unpacked install-info:amd64 5.2.0.dfsg.1-2
2014-04-16 18:27:54 status half-configured install-info:amd64 5.2.0.dfsg.1-2
```
It goes on and on like that from top to bottom, including packages I installed myself.
This does not seem right at all.

Tried reinstalling dpkg, no changes. Tried sudo dpkg --configure -a, sudo apt-get install -f and sudo apt-get clean (though not in that particular order), and there are no changes. That GLib error still consistently pops up and all packages still end up as either "half-installed", "half-configured", or sometimes both.

Can the knowledgeable amongst you please tell me what's going on here?

---

### Post by taytaybongsong on 2014-04-22
anyone know where to go from here?
are these errors as serious as they seem?
can this all be fixed in a fairly non-time consuming fashion?
could these issues be due to encrypting my home folder during the install?
if so, should i do a fresh install again without encrypting my home folder?
or,  would it just make more sense to reinstall 13.10, and restore my ppas,  applications and settings (i have a fairly comprehensive backup)?

i  don't dual boot or anything like that, so it's important that my system  is relatively problem-free. any help would be greatly appreciated.

---

### Post by taytaybongsong on 2014-04-23
hello

---

### Post by taytaybongsong on 2014-04-24
is there anybody out there?

---

### Post by ibjsb4 on 2014-04-24
I would imagine not many people use the encrypt home option and even less can help you.  I do not encrypt either.

I know that I would not be happy with repairing such problems on a fresh install.  Seems like you are just setting yourself up for more problems.

You say that you configured and installed packages.  So at first the install worked normal?  Could you of installed a PPA that borked your system?

Have you tried ..

```
sudo apt-get dist-upgrade
```

---

### Post by Elfy on 2014-04-24
same here - sort of - 

```
grep base-passwd:amd64 /var/log/dpkg.log

2014-04-06 09:50:58 install base-passwd:amd64 <none> 3.5.32
2014-04-06 09:50:58 status half-installed base-passwd:amd64 3.5.32
2014-04-06 09:50:58 status unpacked base-passwd:amd64 3.5.32
2014-04-06 09:50:58 status unpacked base-passwd:amd64 3.5.32
2014-04-06 09:50:58 configure base-passwd:amd64 3.5.32 3.5.32
2014-04-06 09:50:58 status unpacked base-passwd:amd64 3.5.32
2014-04-06 09:50:58 status half-configured base-passwd:amd64 3.5.32
2014-04-06 09:50:58 status installed base-passwd:amd64 3.5.32
2014-04-06 09:50:59 upgrade base-passwd:amd64 3.5.32 3.5.32
2014-04-06 09:50:59 status half-configured base-passwd:amd64 3.5.32
2014-04-06 09:50:59 status unpacked base-passwd:amd64 3.5.32
2014-04-06 09:50:59 status half-installed base-passwd:amd64 3.5.32
2014-04-06 09:50:59 status half-installed base-passwd:amd64 3.5.32
2014-04-06 09:50:59 status unpacked base-passwd:amd64 3.5.32
2014-04-06 09:50:59 status unpacked base-passwd:amd64 3.5.32
2014-04-06 09:51:05 configure base-passwd:amd64 3.5.32 <none>
2014-04-06 09:51:05 status unpacked base-passwd:amd64 3.5.32
2014-04-06 09:51:05 status half-configured base-passwd:amd64 3.5.32
2014-04-06 09:51:05 status installed base-passwd:amd64 3.5.32
2014-04-10 07:10:15 upgrade base-passwd:amd64 3.5.32 3.5.33
2014-04-10 07:10:15 status half-configured base-passwd:amd64 3.5.32
2014-04-10 07:10:15 status unpacked base-passwd:amd64 3.5.32
2014-04-10 07:10:15 status half-installed base-passwd:amd64 3.5.32
2014-04-10 07:10:15 status half-installed base-passwd:amd64 3.5.32
2014-04-10 07:10:16 status unpacked base-passwd:amd64 3.5.33
2014-04-10 07:10:16 status unpacked base-passwd:amd64 3.5.33
2014-04-10 07:10:18 configure base-passwd:amd64 3.5.33 <none>
2014-04-10 07:10:18 status unpacked base-passwd:amd64 3.5.33
2014-04-10 07:10:18 status half-configured base-passwd:amd64 3.5.33
2014-04-10 07:10:19 status installed base-passwd:amd64 3.5.33
```

Do your packages end on something other than installed?

---

### Post by taytaybongsong on 2014-04-24
well, i rolled back to 13.10 and restored my settings, ppas and packages. between this nonsense and the fact that no flavors of the recent lts release work well with an encrypted swap partition, it just wasn't worth it. i'll wait 'til more bugs are ironed out.

elfy: yes, on 14.04 i had many packages that ended up as half-installed too.

ibjsb4: i tried dist upgrade from 13.10 before doing a fresh install, yes. neither ended up well. i can live without encrypted home, but not without encrypted swap (which as mentioned above, just does not play well with this release).

---

