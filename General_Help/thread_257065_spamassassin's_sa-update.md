---
title: "spamassassin's sa-update"
date: 2006-09-14
forum: General Help
---

### Post by dayzed2 on 2006-09-14
Ubuntu 6.06 LTS
I am running a production mail server using spamassassin version 3.1.0. I am trying to use the nice little tool called sa-update that updates the spamassassin rules. However it doesn't seem to be working correctly, although I am a little confused as to what it is complaining about. Perhaps someone can enlighten me. Here is my output:
------------------------
root@desktop:/# sa-update -D
[5690] dbg: logger: adding facilities: all
[5690] dbg: logger: logging level is DBG
[5690] dbg: generic: SpamAssassin version 3.1.0
[5690] dbg: config: score set 0 chosen.
[5690] dbg: dns: is Net::DNS::Resolver available? yes
[5690] dbg: dns: Net::DNS version: 0.53
[5690] dbg: generic: sa-update version svn231362
[5690] dbg: generic: using update directory: /etc/spamassassin
[5690] dbg: diag: perl platform: 5.008007 linux
[5690] dbg: diag: module installed: Digest::SHA1, version 2.10
[5690] dbg: diag: module installed: DB_File, version 1.811
[5690] dbg: diag: module installed: HTML::Parser, version 3.48
[5690] dbg: diag: module installed: MIME::Base64, version 3.05
[5690] dbg: diag: module installed: Net::DNS, version 0.53
[5690] dbg: diag: module installed: Net::SMTP, version 2.29
[5690] dbg: diag: module installed: Mail::SPF::Query, version 1.997
[5690] dbg: diag: module not installed: IP::Country::Fast ('require' failed)
[5690] dbg: diag: module not installed: Razor2::Client::Agent ('require' failed)
[5690] dbg: diag: module not installed: Net::Ident ('require' failed)
[5690] dbg: diag: module not installed: IO::Socket::INET6 ('require' failed)
[5690] dbg: diag: module not installed: IO::Socket::SSL ('require' failed)
[5690] dbg: diag: module installed: Time::HiRes, version 1.66
[5690] dbg: diag: module not installed: DBI ('require' failed)
[5690] dbg: diag: module installed: Getopt::Long, version 2.34
[5690] dbg: diag: module installed: LWP::UserAgent, version 2.033
[5690] dbg: diag: module installed: HTTP::Date, version 1.46
[5690] dbg: diag: module installed: Archive::Tar, version 1.26
[5690] dbg: diag: module installed: IO::Zlib, version 1.04
[5690] dbg: channel: attempting channel updates.spamassassin.org
[5690] dbg: channel: update directory /etc/spamassassin/updates_spamassassin_org
[5690] dbg: channel: channel cf file /etc/spamassassin/updates_spamassassin_org.cf
[5690] dbg: dns: query failed: 0.1.3.updates.spamassassin.org => NOERROR
[5690] dbg: channel: no updates available, skipping channel
[5690] dbg: diag: updates complete, exiting with code 0
root@desktop:/#

---

### Post by dayzed2 on 2006-09-14
The answer is:
do not use sa-update with SpamAssassin version 3.1.0 it is broken and does not work per
[http://issues.apache.org/SpamAssassin/show_bug.cgi?id=4788#c10](http://issues.apache.org/SpamAssassin/show_bug.cgi?id=4788#c10)
[http://wiki.apache.org/spamassassin/RuleUpdates](http://wiki.apache.org/spamassassin/RuleUpdates)

The fix is:
I un-installed spamassassin by doing a
"dpkg --purge spamassassin"
The reason why I did this instead of a "apt-get uninstall spamassassin" is so that I get everything completely un-installed. We don't want any directories or config files left behind.

Then I used cpan to get the latest version of spamassassin. sa-update works great with the latest version of spamassassin.

---

