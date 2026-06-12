---
title: "Very strange data or code"
date: 2018-02-13
forum: General Help
---

### Post by Gnusboy on 2018-02-13
Hey y'all

This is the weirdest thing I've seen. This code or information, just appeared in my recent history. It appears to be system data that's well beyond my comprehension or knowledge.
Can anyone recognize it or tell me if it can impact my system? Here are a couple of screenshots that may help

---

### Post by Gnusboy on 2018-02-13
I forgot to post these items on my last post:
in the list of documents in Libre Writer, these 5 items are listed as individual docs
Doomed
Entries
https: |Y4eZXm_YWu.js
Drivers_autoprobe
dnsmask\.odt
None of these open a document - except for dnsmask\.odt which goes here:

---

### Post by Impavidus on 2018-02-14
You are looking at the /sys pseudo file system: [https://en.wikipedia.org/wiki/Sysfs](https://en.wikipedia.org/wiki/Sysfs)
It's part of the system that allows you to see several internal properties of your running system. There are some symbolic links pointing back and forth between different directories. That's why you can have such a convoluted path.

---

### Post by Gnusboy on 2018-02-14
Impavidus
Thank you. As always, you come up with the info I need to understand my system.
I think I owe you a beer.

---

