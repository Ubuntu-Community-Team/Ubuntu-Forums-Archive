---
title: "Backup problem with Deja-dup via ftp on Ubuntu 14.04 Trusty Tahr"
date: 2014-04-24
forum: General Help
---

### Post by claudio.gaz on 2014-04-24
Hello everyone,

I have the following problem: I have downloaded the brand-new Ubuntu 14.04 Trusty (updating Ubuntu 12.04), and I have configured the default backup utility (Deja-dup) in order to backup some folders on a server via ftp (I am the manager of that server, on which runs Ubuntu 12.04). I have done exactly what I did in Ubuntu 12.04, where all was perfectly working, but now the software carries out the upload up to almost 25 MB (on 3 GB overall), and then returns the following error: "Backup Failed: operation unsupported". If I try to resume the backup, it starts again from 0 and stops at the same point.

If I perform a backup on an external drive, it works perfectly though...

How can I solve this issue?

Thank you,
Claudio

---

### Post by drrob1 on 2014-05-17
This bug affects me also

---

### Post by undrline on 2014-11-26
> **claudio.gaz said:**
> Hello everyone,

I have the following problem: I have downloaded the brand-new Ubuntu 14.04 Trusty (updating Ubuntu 12.04), and I have configured the default backup utility (Deja-dup) in order to backup some folders on a server via ftp (I am the manager of that server, on which runs Ubuntu 12.04). I have done exactly what I did in Ubuntu 12.04, where all was perfectly working, but now the software carries out the upload up to almost 25 MB (on 3 GB overall), and then returns the following error: "Backup Failed: operation unsupported". If I try to resume the backup, it starts again from 0 and stops at the same point.

If I perform a backup on an external drive, it works perfectly though...

How can I solve this issue?

Thank you,
Claudio

> **drrob1 said:**
> This bug affects me also

Did you ever find a solution?

I have submitted a bug to the devs here:
[https://bugs.launchpad.net/deja-dup/+bug/1396691](https://bugs.launchpad.net/deja-dup/+bug/1396691)

Please log in to Launchpad and click "This bug also affects me."  You can also add your details there too:

[COLOR=#333333][FONT=monospace]1. The distribution of Linux you're using:
    lsb_release -d[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]2. The version of deja-dup and duplicity:
    (if on Ubuntu or Debian:)
    dpkg-query -W deja-dup duplicity[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]    (if on Fedora or other RPM-based systems:)
    rpm -q deja-dup duplicity[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]3. The file /tmp/deja-dup.gsettings after running the following line (you may want to scrub the file of any incriminating file names or details):
    gsettings list-recursively org.gnome.DejaDup > /tmp/deja-dup.gsettings[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]4. The file /tmp/deja-dup.log after running the appropriate line below and replicating the problem (you may want to scrub the log of any incriminating file names or details):[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace] * If you're having problems backing up:
    DEJA_DUP_DEBUG=1 deja-dup --backup | tail -n 1000 > /tmp/deja-dup.log[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace] * If you're having problems restoring:
    DEJA_DUP_DEBUG=1 deja-dup --restore | tail -n 1000 > /tmp/deja-dup.log[/FONT][/COLOR]

---

