---
title: "synpatic error"
date: 2008-03-21
forum: General Help
---

### Post by tony2tone on 2008-03-21
Hi Need Help
while opening synaptic package manager I get this error:

E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

what can I do to fix this?:confused:

---

### Post by dcstar on 2008-03-21
> **tony2tone said:**
> Hi Need Help
while opening synaptic package manager I get this error:

E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

what can I do to fix this?:confused:

In a terminal, try:

```
sudo cp /var/lib/dpkg/status.old /var/lib/dpkg/status
```

---

### Post by tony2tone on 2008-03-21
thanks for the reply:)

when I tried the command in terminal I get this error

faust@fuzzed:~$ sudo cp /var/lib/dpkg/status.old /var/lib/dpkg/status
cp: cannot stat `/var/lib/dpkg/status.old': No such file or directory

---

### Post by wormser on 2008-03-21
I am unsure about this being the resolution for the error.  But, I do see an issue with the command.  The command is suppose to copy the file and make a back up.  It appears the back up file was put in front of the original file.  Just switch the files around like the command below.

```
sudo cp /var/lib/dpkg/status /var/lib/dpkg/status.old
```

---

### Post by tony2tone on 2008-03-21
no luck. I'm getting this error

faust@fuzzed:~$ sudo cp /var/lib/dpkg/status /var/lib/dpkg/status.old
[sudo] password for faust:
cp: cannot stat `/var/lib/dpkg/status': No such file or directory

---

