---
title: "Invalid filename"
date: 2012-11-14
forum: General Help
---

### Post by eslavko on 2012-11-14
Hello....

After invoking sudo apt-get update I got error...

```
snip snip


Reading package lists... Done
N: Ignoring file 'getdeb.list.bck' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension

```

How to solve?

Ubuntu 12.04

---

### Post by Impavidus on 2012-11-14
It's a backup file that's ignored by apt-get. Most likely an almost identical file without the .bck exists. You can probably ignore this message.

It's actually not an error but a notification. It starts with an N, errors start with E (warnings with W).

---

### Post by eslavko on 2012-11-14
yes identical filename without bkc extension exists. And both have length of 0. Is it safe to delete it?

---

### Post by sisco311 on 2012-11-14
If both files are empty, then yes, it's safe to delete both of them.

---

### Post by eslavko on 2012-11-14
deleted and seems ok now.

---

