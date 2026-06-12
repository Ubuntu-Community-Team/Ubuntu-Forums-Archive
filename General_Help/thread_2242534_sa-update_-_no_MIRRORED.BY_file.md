---
title: "sa-update - no MIRRORED.BY file"
date: 2014-09-02
forum: General Help
---

### Post by ceejay13 on 2014-09-02
Hi,

I have been fighting a problem with sa-update since before I upgraded to 14.04 (from 12.04) a couple of weeks ago.  I try to run sa-update and get an error.  Below are the begining (version numbers) and end (actual error) of the debug log using sa-update -D

```
Sep  2 15:39:10.154 [2230] dbg: logger: adding facilities: all
Sep  2 15:39:10.155 [2230] dbg: logger: logging level is DBG
Sep  2 15:39:10.155 [2230] dbg: generic: SpamAssassin version 3.4.0
Sep  2 15:39:10.156 [2230] dbg: generic: Perl 5.018002, PREFIX=/usr, DEF_RULES_DIR=/usr/share/spamassassin, LOCAL_RULES_DIR=/etc/spamassassin, LOCAL_STATE_DIR=/var/lib/spamassassin
Sep  2 15:39:10.156 [2230] dbg: config: timing enabled
Sep  2 15:39:10.158 [2230] dbg: config: score set 0 chosen.
Sep  2 15:39:10.176 [2230] dbg: generic: sa-update version svn1475932
Sep  2 15:39:10.176 [2230] dbg: generic: using update directory: /var/lib/spamassassin/3.004000
Sep  2 15:39:10.804 [2230] dbg: diag: perl platform: 5.018002 linux
Sep  2 15:39:10.804 [2230] dbg: diag: [...] module installed: Digest::SHA, version 5.84_01
Sep  2 15:39:10.804 [2230] dbg: diag: [...] module installed: HTML::Parser, version 3.71
Sep  2 15:39:10.805 [2230] dbg: diag: [...] module installed: Net::DNS, version 0.68
```


```
Sep  2 15:39:11.573 [2230] dbg: timing: total 564 ms - init: 541 (95.8%), parse: 3.7 (0.7%), extract_message_metadata: 8 (1.4%), get_uri_detail_list: 3.0 (0.5%)
Sep  2 15:39:11.574 [2230] dbg: plugin: Mail::SpamAssassin::Plugin::MIMEHeader=HASH(0x9d655a4) implements 'finish_tests', priority 0
Sep  2 15:39:11.574 [2230] dbg: plugin: Mail::SpamAssassin::Plugin::Check=HASH(0x9d6991c) implements 'finish_tests', priority 0
Sep  2 15:39:11.578 [2230] dbg: generic: lint check of site pre files succeeded, continuing with channel updates
Sep  2 15:39:11.578 [2230] dbg: channel: protocol family available: inet,inet6
Sep  2 15:39:11.578 [2230] dbg: channel: no mirror file /var/lib/spamassassin/3.004000/updates_spamassassin_org/MIRRORED.BY, will fetch it
Sep  2 15:39:11.579 [2230] dbg: channel: DNS lookup on mirrors.updates.spamassassin.org
Sep  2 15:41:41.673 [2230] dbg: dns: query failed: mirrors.updates.spamassassin.org => query timed out
error: no mirror data available for channel updates.spamassassin.org
channel: MIRRORED.BY file URL was not in DNS, channel failed
Sep  2 15:41:41.674 [2230] dbg: generic: cleaning up temporary directory/files
Sep  2 15:41:41.674 [2230] dbg: generic: cleaning directory /tmp/.spamassassin2230YBaZc0tmp
Sep  2 15:41:41.676 [2230] dbg: diag: updates complete, exiting with code 4
```

Looking at the log as a Novice, I can't resolve the <spamassassin.org> address using a lookup, also, I don't have any MIRRORED.BY (or any other) file in the /var/lib/spamassassin/3.004000/updates_spamassassin_org/ directory, so I quite see why the script is trying to fetch it and failing.

Has anyone got any suggestions as to how I can rectify this problem so that I can run sa-update?

TIA,

---

### Post by ceejay13 on 2014-09-03
UPDATE:

I have managed to install the rules manually from the tarball file downloaded from the SpamAssassin site, but the update from the internet still gives the same error.

---

### Post by ceejay13 on 2015-02-18
Eventually solved this after building another server by using this command.

sa-update -D --updatedir /tmp/updates

sa-update runs OK now.  Still don't know why this happened in the first place on both an OS upgrade and a new build computer.

---

