---
title: "Gufw: Allowing software install"
date: 2015-01-29
forum: General Help
---

### Post by Swiftjay on 2015-01-29
I have gufw set up to block all incoming and outgoing connections except ports and websites I want but I need to know what the IP address of the software centre and update servers.  Could anyone provide this for me?

---

### Post by Lars Noodén on 2015-01-29
The actual machines vary depending on which country's mirrors you have chosen to use.  You can find the machines you are using in /etc/apt/sources.list and in the files found in /etc/apt/sources.list.d/

You could collate them manually or grab them with "find" and "awk" and "sort"

```

find /etc/apt/ -type f -exec *awk '/^deb/ { gsub(/^.*\/\//, "", $2) ; gsub(/\/.*$/, "", $2); print $2 ; } ' {}* \; | sort -u

```

From there you can look up the ip numbers of those hosts using "dig" or "host"

---

