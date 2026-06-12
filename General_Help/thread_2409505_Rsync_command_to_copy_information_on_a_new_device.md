---
title: "Rsync command to copy information on a new device?"
date: 2019-01-03
forum: General Help
---

### Post by dimmetrix on 2019-01-03
Hi!

I need to create a backup or clonate of all my current device to a new one and check that each of the data has been copied correctly. What options should I use in rsync?

Is it the right program to do this?

Thank you.

---

### Post by HermanAB on 2019-01-03
Rsync examples are in the man page.

---

### Post by tea for one on 2019-01-03
> **dimmetrix said:**
> Hi!

I need to create a backup or clonate of all my current device to a new one and check that each of the data has been copied correctly. What options should I use in rsync?

Is it the right program to do this?

Thank you.

It looks like you want to clone your operating system _and_ personal data, is that correct? 

Please supply some information about your source device and target device.

If you only want to backup personal data then Grsync (GUI for rsync) is a bit easier to follow.

In the meantime, have a look at [https://clonezilla.org/](https://clonezilla.org/).

If you haven't used Clonezilla before then carefully read the info in the website - it is a powerful tool and it can appear to be a bit daunting for first time users.

---

