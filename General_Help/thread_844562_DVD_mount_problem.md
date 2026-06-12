---
title: "DVD mount problem"
date: 2008-06-29
forum: General Help
---

### Post by utab on 2008-06-29
Dear all,

To recover my backup, I am trying to mount a dvd. But it is not working as intended. I can mount cds, that is not a problem fortunately...

The output from dmesg | grep CD is
[http://pastebin.com/d387e2dc3](http://pastebin.com/d387e2dc3)

The output of sudo hdparm -I /dev/scd0
[http://pastebin.com/m2834c77a](http://pastebin.com/m2834c77a)

The output of cat /etc/fstab
[http://pastebin.com/m612e1ec0](http://pastebin.com/m612e1ec0)

A similar thread I found was this but it was not concluded :/

Any help is appreciated.

Umut

---

### Post by Bruce M. on 2008-07-12
> **utab said:**
> Dear all,

To recover my backup, I am trying to mount a dvd. But it is not working as intended. I can mount cds, that is not a problem fortunately...

The output of cat /etc/fstab
[http://pastebin.com/m612e1ec0](http://pastebin.com/m612e1ec0)

Any help is appreciated.

Umut

Hi Umut,

I notice in /etc/fstab you have a line commented out:

```
/dev/scd0       /media/cdrom0    auto user,noauto,exec,utf8 0       0
#/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```
What I have is:
```
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
```
for both of mine.

Try this:
```
#/dev/scd0       /media/cdrom0    auto user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```
and see if it makes a difference.

Hope this helps.
Bruce

---

