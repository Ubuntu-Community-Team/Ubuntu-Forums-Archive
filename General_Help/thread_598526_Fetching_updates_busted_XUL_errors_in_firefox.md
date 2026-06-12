---
title: "Fetching updates busted/ XUL errors in firefox"
date: 2007-10-31
forum: General Help
---

### Post by erikharrison on 2007-10-31
Hey all. I had a pair of possibly unrelated issues crop up at the same time.

Yesterday, when checking for updates the Update Manager complained thusly:

```
http://security.ubuntu.com/ubuntu/dists/gutsy-security/Release: Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)
http://us.archive.ubuntu.com/ubuntu/dists/gutsy/Release: Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)
http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/Release: Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)
http://us.archive.ubuntu.com/ubuntu/dists/gutsy-backports/Release: Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)
```

I noticed today that some firefox dialogs are broken - there are what I assume to be XUL errors complaining about malformed XML. For example, the download manager:
```
XML Parsing Error: syntax error
Location: chrome://mozapps/content/downloads/downloads.xul
Line Number 1, Column 1:for empty MIME type field.
^

```
Obviously this isn't cool. Anyone able to give me a hand?

---

### Post by erikharrison on 2007-11-01
Updating - simply reinstalling firefox fixed the firefox issue. Still not sure what's up with updates. Poking about.

---

### Post by Maestro23 on 2007-11-01
Post your /etc/apt/sources.list

In terminal:

> cat /etc/apt/sources.list

---

