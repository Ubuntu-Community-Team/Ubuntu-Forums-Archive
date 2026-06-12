---
title: "Appstream data error."
date: 2016-11-29
forum: General Help
---

### Post by Hewjr100 on 2016-11-29
Anyone get this error message today:

AppStream cache update completed, but some metadata was ignored due to errors.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
All packages are up to date.
henry@wyatt:~$

Henry

---

### Post by mc4man on 2016-11-29
[https://bugs.launchpad.net/ubuntu/+source/appstream/+bug/1644498](https://bugs.launchpad.net/ubuntu/+source/appstream/+bug/1644498)

---

### Post by Hewjr100 on 2016-11-30
Ok got it, thanks.

Henry

---

### Post by Hewjr100 on 2016-12-01
Btw I still get that error, does it effect anything, and is there a fix on the way?

Henry

---

### Post by howefield on 2016-12-01
> **Hewjr100 said:**
> Btw I still get that error, does it effect anything, and is there a fix on the way?

Read the bug report and mark it as "affects me too". Although it shouldn't happen, it seems a fairly low risk bug so I wouldn't worry about it.

Looks like a fix is on the way.

---

### Post by Hewjr100 on 2016-12-01
Thank you howefield.

Henry

---

### Post by howefield on 2016-12-02
[ubuntu/xenial-proposed] appstream 0.9.4-1ubuntu2 (Accepted)

```
Launchpad-Bugs-Fixed: 1644498
Changes:
 appstream (0.9.4-1ubuntu2) xenial; urgency=medium
 .
   * yaml-parser-errors.patch: Deal with errors in the YAML structure
     in the best way possible.
   * modern-metadata.patch: Recognize and return modern AppStream
     component types. (LP: #1644498)
```

Should make its way from *-proposed* on to your machine within the next day or so, if not already.

---

### Post by Hewjr100 on 2016-12-02
Great news howefiled, I hate errror messages, even if they are not harmfull.  Must be my OCD.

Henry

---

### Post by Hewjr100 on 2016-12-05
Today, Monday Dec. 5th I do not get error message anymore, must have been fixed.

Henry

---

### Post by howefield on 2016-12-05
> **Hewjr100 said:**
> Today, Monday Dec. 5th I do not get error message anymore, must have been fixed.

Cool, easy enough to check that you have the updated package with the terminal command..

```
apt-cache policy appstream
```

The output should have something like "*0.9.4-1ubuntu2*" in it.

---

### Post by Hewjr100 on 2016-12-05
Well to be honest, I just did a fresh/clean install of ubuntu 16.10.  My wifi did not work in 16.04, but it does in 16.10.

Henry

---

### Post by Hewjr100 on 2016-12-20
Getting this error message again.  I noticed that a fix was released, but apparently its back.

Henry

---

