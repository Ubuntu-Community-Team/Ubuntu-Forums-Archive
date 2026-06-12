---
title: "boot up in ubuntu error message"
date: 2014-11-20
forum: General Help
---

### Post by kccv42 on 2014-11-20
Everytime i boot up Ubuntu, before the start screen it says "by signal  22". This was only part of the whole message. The message appeared fast then ubuntu screen. What does it mean? Ubuntu works fine though.

---

### Post by oldfred on 2014-11-21
Use system log app to view dmesg. It is a long file with mostly standard entries. You want errors, warnings or any with long timestamp differences.

Or just open dmesg and see if you have the full errror message or other errors.
gksudo gedit /var/log/dmesg

---

### Post by kccv42 on 2014-11-21
I will give it a try thanks.

---

