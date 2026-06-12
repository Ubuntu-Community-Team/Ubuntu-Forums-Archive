---
title: "pkill fails due to library issue"
date: 2022-09-12
forum: General Help
---

### Post by Skaperen on 2022-09-12
i get the following error messages from pkill every time i try to use it (as root):
```

pkill: /lib/x86_64-linux-gnu/libc.so.6: version `GLIBC_2.33' not found (required by pkill)
pkill: /lib/x86_64-linux-gnu/libc.so.6: version `GLIBC_2.34' not found (required by pkill)

```

i don't know what version of pkill this is:
```

lt1a/forums/1 /home/forums 5> pkill --version
pkill: /lib/x86_64-linux-gnu/libc.so.6: version `GLIBC_2.33' not found (required by pkill)
pkill: /lib/x86_64-linux-gnu/libc.so.6: version `GLIBC_2.34' not found (required by pkill)
lt1a/forums/1 /home/forums 6>

```
there is no "pkill" package to check that version.

let's see what libraries it needs:
```

lt1a/forums/2 /home/forums 7> ldd /usr/bin/pkill
/usr/bin/pkill: /lib/x86_64-linux-gnu/libc.so.6: version `GLIBC_2.33' not found (required by /usr/bin/pkill)
/usr/bin/pkill: /lib/x86_64-linux-gnu/libc.so.6: version `GLIBC_2.34' not found (required by /usr/bin/pkill)
    linux-vdso.so.1 (0x00007ffeef742000)
    libprocps.so.8 => /lib/x86_64-linux-gnu/libprocps.so.8 (0x00007f57d7e45000)
    libc.so.6 => /lib/x86_64-linux-gnu/libc.so.6 (0x00007f57d7c53000)
    libsystemd.so.0 => /lib/x86_64-linux-gnu/libsystemd.so.0 (0x00007f57d7ba4000)
    libdl.so.2 => /lib/x86_64-linux-gnu/libdl.so.2 (0x00007f57d7b9e000)
    /lib64/ld-linux-x86-64.so.2 (0x00007f57d7e8d000)
    librt.so.1 => /lib/x86_64-linux-gnu/librt.so.1 (0x00007f57d7b94000)
    liblzma.so.5 => /lib/x86_64-linux-gnu/liblzma.so.5 (0x00007f57d7b6b000)
    liblz4.so.1 => /lib/x86_64-linux-gnu/liblz4.so.1 (0x00007f57d7b48000)
    libgcrypt.so.20 => /lib/x86_64-linux-gnu/libgcrypt.so.20 (0x00007f57d7a2a000)
    libpthread.so.0 => /lib/x86_64-linux-gnu/libpthread.so.0 (0x00007f57d7a07000)
    libgpg-error.so.0 => /lib/x86_64-linux-gnu/libgpg-error.so.0 (0x00007f57d79e4000)
lt1a/forums/2 /home/forums 8>

```
someone probably wants to see this:
```

lt1a/forums/1 /home/forums 17> ls --full-time /lib/x86_64-linux-gnu/libc-2.31.so /lib/x86_64-linux-gnu/libc.so.6 /usr/bin/pkill /usr/bin/pgrep
-rwxr-xr-x 1 root root 2029592 2022-04-06 21:24:41.000000000 -0400 /lib/x86_64-linux-gnu/libc-2.31.so
lrwxrwxrwx 1 root root      12 2022-04-06 21:24:41.000000000 -0400 /lib/x86_64-linux-gnu/libc.so.6 -> libc-2.31.so
-rwxr-xr-x 1 root root   30968 2022-02-25 06:57:56.000000000 -0500 /usr/bin/pgrep
lrwxrwxrwx 1 root root       5 2021-09-09 08:59:24.000000000 -0400 /usr/bin/pkill -> pgrep
lt1a/forums/1 /home/forums 18>

```
what can i do next to find what is wrong and fix it?

i am running Xubuntu 20.04 Desktop AMD and want to get this all stable before going to 22.04.

---

### Post by &amp;KyT$0P# on 2022-09-12
> **Skaperen said:**
> there is no "pkill" package to check that version.

The package name is [FONT=Courier New]procps[/FONT]

---

### Post by Skaperen on 2022-09-13
```

lt1a/forums/3 /home/forums 4> dpkg -l|fgrep procps
ii  libprocps8:amd64                      2:3.3.16-1ubuntu2.3                   amd64        library for accessing process information from /proc
ii  procps                                2:3.3.16-1ubuntu2.3                   amd64        /proc file system utilities
lt1a/forums/3 /home/forums 5>

```

---

### Post by Skaperen on 2022-09-13
what is the apt command to validate the installation of a package?  i think i have some wrong files or maybe some wrong packages in this Xubuntu 20.04.

---

### Post by &amp;KyT$0P# on 2022-09-13
[You do have the correct version of that package for 20.04.]("https://packages.ubuntu.com/focal-updates/procps")

> **Skaperen said:**
> what is the apt command to validate the installation of a package?  i think i have some wrong files or maybe some wrong packages in this Xubuntu 20.04.

To check for packages that are not installed correctly, [this thread]("https://ubuntuforums.org/showthread.php?t=2414765") has some ideas.

To check for wrong files, use [FONT=Courier New]debsums[/FONT]

To check for wrong packages, [this thread]("https://ubuntuforums.org/showthread.php?t=2399096") might help (that script should work as-is on 20.04, but it needed modifications for 22.04).

---

### Post by Skaperen on 2022-09-13
so i tried debsums:
```

lt1a/root/2 /root 31# time logcmd -s debsums-ac-out debsums -ac
Script started, file is ./20220913-222358-100052-debsums-ac-out.log
22:23:58 [100056] EXECUTING: 'debsums' '-ac'
/etc/default/apport
/bin/bzgrep
/bin/grep
/bin/zegrep
/bin/zfgrep
/bin/zgrep
/usr/bin/ptargrep
/usr/bin/pgrep
/usr/bin/zipgrep
/usr/bin/xzgrep
[[ 3m26s real 206.862 - user 23.445 - sys 10.230 - 16.27% ]]
22:27:25 [100056] FINISHED - status = 2
Script done, file is ./20220913-222358-100052-debsums-ac-out.log
[[ 3m27s real 207.891 - user 23.460 - sys 10.236 - 16.20% ]]
lt1a/root/2 /root 32#

```
i also have 'rc' status on 4 old kernel versions that i probably can just throw away so i have 'ii' status on 2 newer kernel versions.
```

lt1a/forums/2 /home/forums 4> dpkg -l | grep -v "^ii"
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                  Version                               Architecture Description
+++-=====================================-=====================================-============-======================================================================================================
rc  linux-image-5.13.0-44-generic         5.13.0-44.49~20.04.1                  amd64        Signed kernel image generic
rc  linux-image-5.13.0-48-generic         5.13.0-48.54~20.04.1                  amd64        Signed kernel image generic
rc  linux-image-5.13.0-51-generic         5.13.0-51.58~20.04.1                  amd64        Signed kernel image generic
rc  linux-image-5.13.0-52-generic         5.13.0-52.59~20.04.1                  amd64        Signed kernel image generic
rc  linux-modules-5.13.0-44-generic       5.13.0-44.49~20.04.1                  amd64        Linux kernel extra modules for version 5.13.0 on 64 bit x86 SMP
rc  linux-modules-5.13.0-48-generic       5.13.0-48.54~20.04.1                  amd64        Linux kernel extra modules for version 5.13.0 on 64 bit x86 SMP
rc  linux-modules-5.13.0-51-generic       5.13.0-51.58~20.04.1                  amd64        Linux kernel extra modules for version 5.13.0 on 64 bit x86 SMP
rc  linux-modules-5.13.0-52-generic       5.13.0-52.59~20.04.1                  amd64        Linux kernel extra modules for version 5.13.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.13.0-44-generic 5.13.0-44.49~20.04.1                  amd64        Linux kernel extra modules for version 5.13.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.13.0-48-generic 5.13.0-48.54~20.04.1                  amd64        Linux kernel extra modules for version 5.13.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.13.0-51-generic 5.13.0-51.58~20.04.1                  amd64        Linux kernel extra modules for version 5.13.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.13.0-52-generic 5.13.0-52.59~20.04.1                  amd64        Linux kernel extra modules for version 5.13.0 on 64 bit x86 SMP
lt1a/forums/2 /home/forums 5> dpkg -l | fgrep 'Signed kernel image generic'
rc  linux-image-5.13.0-44-generic         5.13.0-44.49~20.04.1                  amd64        Signed kernel image generic
rc  linux-image-5.13.0-48-generic         5.13.0-48.54~20.04.1                  amd64        Signed kernel image generic
rc  linux-image-5.13.0-51-generic         5.13.0-51.58~20.04.1                  amd64        Signed kernel image generic
rc  linux-image-5.13.0-52-generic         5.13.0-52.59~20.04.1                  amd64        Signed kernel image generic
ii  linux-image-5.15.0-43-generic         5.15.0-43.46~20.04.1                  amd64        Signed kernel image generic
ii  linux-image-5.15.0-46-generic         5.15.0-46.49~20.04.1                  amd64        Signed kernel image generic
lt1a/forums/2 /home/forums 6>

```


things to eventually deal with, or put off until i can go to 22.04 (i do a fresh full install each time so it should not inherit any of these issues).  but, still no clue about pkill.  i should find someone on Xubuntu 20.04 and ask them to check what versions of *pkill* and *libc* they have.  hmmmm, if pkill had been a snap, this be a whole different kind of issue, or maybe not an issue at all.

---

### Post by Skaperen on 2022-09-13
FYI ... i put off 22.04 because i felt i was unfamiliar enough with _Snaps_ to deal with any issues i encounter that keep me from using _Firefox_ (to go search or ask for clues).  but in 20.04, [FONT=courier new]/snap/README[/FONT] is the only thing i have in [FONT=courier new]/snap[/FONT] right now (maybe there is something i can install and play with that can show me how _Snaps_ work and behave).

---

### Post by Skaperen on 2022-09-14
the question is: what version of *glibc* packages and what version of *procps* package are in *Ubuntu* and *Xubuntu* 20.04 LTS (_focal fossa_)?  and does the *pkill* command work (just try *pkill --version*).

---

### Post by &amp;KyT$0P# on 2022-09-14
> **Skaperen said:**
> the question is: what version of *glibc* packages and what version of *procps* package are in *Ubuntu* and *Xubuntu* 20.04 LTS (_focal fossa_)?

You can use the search at [https://packages.ubuntu.com/](https://packages.ubuntu.com/) to answer questions like these.  I think the package for glibc is [FONT=Courier New]libc6[/FONT] in which case 20.04 would have [version 2.31]("https://packages.ubuntu.com/focal-updates/libc6")

---

### Post by Skaperen on 2022-09-14
that's what my research confirmed.

i ran the command, as root: apt-get install --reinstall procps

i didn't know if it was safe to purge it first so i didn't. but after the reinstall, pkill now works:
```

lt1a/forums/1 /home/forums 4> pkill --version
pkill from procps-ng 3.3.16
lt1a/forums/1 /home/forums 5>

```

i should have captured a copy of what was installed originally, in case it was corrupted, to compare. but i had an unrelated reason to reboot (from a couple days ago) and an opportunity to do it about 40 minutes ago (something important got done) so i went for it and was in a hurry to do it and did the reinstall after it came back up (and an upgrade) and now it works. and, no, the upgrade (log below) didn't fix it as i upgraded and rebooted around when i started this thread and no luck back then.

next time i have an issue like this i hope to remember to capture a copy of its files.  that or/and check the md5s.

```

Script started on 2022-09-14 18:26:05-04:00 [TERM="xterm-256color" TTY="/dev/pts/0" COLUMNS="137" LINES="37"]
18:26:05 [1906] EXECUTING: '/root/cmd/dist-upgrade'
---------------------------------------------------------------------------------------------------------------------------apt-get clean-
2022-09-14-18:26:05.746221780 EXECUTING: apt-get clean
[[ real 0.081 - user 0.000 - sys 0.012 - 14.65 ]]
------------------------------------------------------------------------------------------------------------apt-get update --fix-missing-
2022-09-14-18:26:05.863235235 EXECUTING: apt-get update --fix-missing
Hit:1 http://us.archive.ubuntu.com/ubuntu focal InRelease
Get:2 http://security.ubuntu.com/ubuntu focal-security InRelease [114 kB]
Get:3 http://us.archive.ubuntu.com/ubuntu focal-updates InRelease [114 kB]
Get:4 http://us.archive.ubuntu.com/ubuntu focal-backports InRelease [108 kB]
Get:5 http://security.ubuntu.com/ubuntu focal-security/main amd64 DEP-11 Metadata [40.7 kB]
Get:6 http://security.ubuntu.com/ubuntu focal-security amd64 Contents (deb) [129 MB]
Get:7 http://us.archive.ubuntu.com/ubuntu focal-updates/main amd64 Packages [2,081 kB]
Get:8 http://us.archive.ubuntu.com/ubuntu focal-updates/main i386 Packages [717 kB]
Get:9 http://us.archive.ubuntu.com/ubuntu focal-updates/main amd64 DEP-11 Metadata [277 kB]
Get:10 http://us.archive.ubuntu.com/ubuntu focal-updates amd64 Contents (deb) [141 MB]
Get:11 http://security.ubuntu.com/ubuntu focal-security/universe amd64 DEP-11 Metadata [77.5 kB]
Get:12 http://security.ubuntu.com/ubuntu focal-security/universe amd64 c-n-f Metadata [14.8 kB]
Get:13 http://security.ubuntu.com/ubuntu focal-security/multiverse amd64 DEP-11 Metadata [2,464 B]
Get:14 http://us.archive.ubuntu.com/ubuntu focal-updates/universe i386 Packages [691 kB]
Get:15 http://us.archive.ubuntu.com/ubuntu focal-updates/universe amd64 Packages [953 kB]
Get:16 http://us.archive.ubuntu.com/ubuntu focal-updates/universe amd64 DEP-11 Metadata [391 kB]
Get:17 http://us.archive.ubuntu.com/ubuntu focal-updates/universe amd64 c-n-f Metadata [21.5 kB]
Get:18 http://us.archive.ubuntu.com/ubuntu focal-updates/multiverse amd64 DEP-11 Metadata [940 B]
Get:19 http://us.archive.ubuntu.com/ubuntu focal-backports/main amd64 DEP-11 Metadata [7,980 B]
Get:20 http://us.archive.ubuntu.com/ubuntu focal-backports/universe amd64 DEP-11 Metadata [30.5 kB]
Fetched 275 MB in 7min 53s (582 kB/s)
Reading package lists... Done
[[ real 483.623 - user 53.280 - sys 9.079 - 12.89 ]]
---------------------------------------------------------------------------------------------------------------------dpkg --configure -a-
2022-09-14-18:34:09.520458698 EXECUTING: dpkg --configure -a
[[ real 1.861 - user 0.020 - sys 0.005 - 1.31 ]]
---------------------------------------------------------------------------------------------------------apt-get -y install --fix-broken-
2022-09-14-18:34:11.422126770 EXECUTING: apt-get -y install --fix-broken
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
[[ real 0.866 - user 0.498 - sys 0.142 - 73.89 ]]
-----------------------------------------------------------------------------------------------------------------apt-get -y dist-upgrade-
2022-09-14-18:34:12.323444843 EXECUTING: apt-get -y dist-upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  gir1.2-javascriptcoregtk-4.0 gir1.2-webkit2-4.0 libjavascriptcoregtk-4.0-18 libwebkit2gtk-4.0-37
  4 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
  4 standard security updates
  Need to get 21.4 MB of archives.
  After this operation, 12.3 kB of additional disk space will be used.
  Get:1 http://us.archive.ubuntu.com/ubuntu focal-updates/main amd64 libwebkit2gtk-4.0-37 amd64 2.36.7-0ubuntu0.20.04.1 [15.2 MB]
  Get:2 http://us.archive.ubuntu.com/ubuntu focal-updates/main amd64 libjavascriptcoregtk-4.0-18 amd64 2.36.7-0ubuntu0.20.04.1 [6,168 kB]
  Get:3 http://us.archive.ubuntu.com/ubuntu focal-updates/main amd64 gir1.2-webkit2-4.0 amd64 2.36.7-0ubuntu0.20.04.1 [80.1 kB]
  Get:4 http://us.archive.ubuntu.com/ubuntu focal-updates/main amd64 gir1.2-javascriptcoregtk-4.0 amd64 2.36.7-0ubuntu0.20.04.1 [28.8 kB]
  Fetched 21.4 MB in 35s (619 kB/s)
  (Reading database ... 246033 files and directories currently installed.)
  Preparing to unpack .../libwebkit2gtk-4.0-37_2.36.7-0ubuntu0.20.04.1_amd64.deb ...
  Unpacking libwebkit2gtk-4.0-37:amd64 (2.36.7-0ubuntu0.20.04.1) over (2.36.6-0ubuntu0.20.04.1) ...
  Preparing to unpack .../libjavascriptcoregtk-4.0-18_2.36.7-0ubuntu0.20.04.1_amd64.deb ...
  Unpacking libjavascriptcoregtk-4.0-18:amd64 (2.36.7-0ubuntu0.20.04.1) over (2.36.6-0ubuntu0.20.04.1) ...
  Preparing to unpack .../gir1.2-webkit2-4.0_2.36.7-0ubuntu0.20.04.1_amd64.deb ...
  Unpacking gir1.2-webkit2-4.0:amd64 (2.36.7-0ubuntu0.20.04.1) over (2.36.6-0ubuntu0.20.04.1) ...
  Preparing to unpack .../gir1.2-javascriptcoregtk-4.0_2.36.7-0ubuntu0.20.04.1_amd64.deb ...
  Unpacking gir1.2-javascriptcoregtk-4.0:amd64 (2.36.7-0ubuntu0.20.04.1) over (2.36.6-0ubuntu0.20.04.1) ...
  Setting up libjavascriptcoregtk-4.0-18:amd64 (2.36.7-0ubuntu0.20.04.1) ...
  Setting up gir1.2-javascriptcoregtk-4.0:amd64 (2.36.7-0ubuntu0.20.04.1) ...
  Setting up libwebkit2gtk-4.0-37:amd64 (2.36.7-0ubuntu0.20.04.1) ...
  Setting up gir1.2-webkit2-4.0:amd64 (2.36.7-0ubuntu0.20.04.1) ...
  Processing triggers for libc-bin (2.31-0ubuntu9.9) ...
  [[ real 46.302 - user 4.708 - sys 1.058 - 12.45 ]]
  -----------------------------------------------------------------------------------------------------------apt-get -y autoremove --purge-
  2022-09-14-18:34:58.658203363 EXECUTING: apt-get -y autoremove --purge
  Reading package lists... Done
  Building dependency tree
  Reading state information... Done
  0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
  [[ real 0.508 - user 0.462 - sys 0.052 - 101.16 ]]
  -rw-r--r-- 1 root root 261245 Sep 14 18:26 20220914182605.dpkg-l
  -rw-r--r-- 1 root root 261245 Sep 14 18:34 20220914183459.dpkg-l
  [[ real 533.582 - user 59.201 - sys 10.403 - 13.04 ]]
  18:34:59 [1906] FINISHED - status = 0

Script done on 2022-09-14 18:35:00-04:00 [COMMAND_EXIT_CODE="0"]

```

i previewed this post and the edit buffer became empty. perhaps because it was large.  to i had to re-create it from the preview (at least it showed that and didn't totally lose the post.  beware previewing large posts.  this one was 7319 characters up to the end of the 2nd code end tag.  so, please forgive any glitches.

---

### Post by Skaperen on 2022-09-14
and **Edit Post** empties the buffer, too.  **Reply With Quote** fails, too.  something's broken.  probably Javascript download buffering.

---

