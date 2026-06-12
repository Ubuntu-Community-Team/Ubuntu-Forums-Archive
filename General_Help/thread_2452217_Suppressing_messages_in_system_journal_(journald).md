---
title: "Suppressing messages in system journal (journald)"
date: 2020-10-18
forum: General Help
---

### Post by David_Partridge on 2020-10-18
I've been able to suppress the annoying "DVE-2018-0001" message in syslog by adding

```
if ($programname == "systemd-resolved") and ($msg contains "DVE-2018-0001") then stop
```

into [FONT=courier new]/etc/rsyslog.d/50-default.conf[/FONT].

Which is fine, but that doesn't suppress the message in the system journal which you view using journalctl and is written by journald.

So the dread "Server returned error NXDOMAIN ..." message still pollutes the system journal in huge numbers.

Is there any way to suppress to tell journald that it should forever more suppress this noise.

David

---

### Post by David_Partridge on 2020-10-19
I asked on the systemd-devel mailing list - Lennart Poettering says there's no way to suppress messages in the journal.

David

---

