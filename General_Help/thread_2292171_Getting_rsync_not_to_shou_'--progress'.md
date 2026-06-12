---
title: "Getting rsync not to shou '--progress'"
date: 2015-08-25
forum: General Help
---

### Post by funkytwig2 on 2015-08-25
Hi, I am writing some backup scripts which put the output into a log file.  As well as punting the file names of changed files it is also putting the progress in so it looks like this:

```
sending incremental file list
created directory /home/ben/backups/email_1440553501_F_Wed_26Aug2015_0245
nfxekxib.default/panacea.dat
         18,194 100%    0.00kB/s    0:00:00 (xfr#1, to-chk=71/100)
nfxekxib.default/ImapMail/mail.xtreamlab.net/INBOX
     11,673,499 100%  318.08MB/s    0:00:00 (xfr#2, to-chk=46/100)
nfxekxib.default/ImapMail/mail.xtreamlab.net/INBOX.msf
      6,671,709 100%  113.62MB/s    0:00:00 (xfr#3, to-chk=45/100)
nfxekxib.default/ImapMail/mail.xtreamlab.net/INBOX.sbd/Junk.msf
        884,020 100%   14.29MB/s    0:00:00 (xfr#4, to-chk=34/100)
```

Which is not what I want, I only want:

```
sending incremental file list
created directory /home/ben/backups/email_1440553501_F_Wed_26Aug2015_0245
nfxekxib.default/panacea.dat
nfxekxib.default/ImapMail/mail.xtreamlab.net/INBOX
nfxekxib.default/ImapMail/mail.xtreamlab.net/INBOX.msf
nfxekxib.default/ImapMail/mail.xtreamlab.net/INBOX.sbd/Junk.msf
```

Is there a way of doing this?

---

### Post by papibe on 2015-08-25
Hi funkytwig2

The option --progress is not a default, and it only implied by -P

Something simple like this should work:
```
rsync -av /path/to/source/ /path/to/destination/
```
Does that help? If not, could you post the rsync command you are using?

Regards.

---

