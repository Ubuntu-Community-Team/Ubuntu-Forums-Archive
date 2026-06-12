---
title: "Opening BMP files in ristretto does not work"
date: 2020-05-15
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2020-05-15
What is another basic image view that works
```
~$ lsb_release -a && apt-cache policy ristretto
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 20.04 LTS
Release:    20.04
Codename:    focal
ristretto:
  Installed: 0.10.0-1
  Candidate: 0.10.0-1
  Version table:
 *** 0.10.0-1 500
        500 http://us.archive.ubuntu.com/ubuntu focal/universe amd64 Packages
        100 /var/lib/dpkg/status


```
This was a issues a few years ago and it got fixed - [https://bugs.launchpad.net/ubuntu/+source/ristretto/+bug/1762242](https://bugs.launchpad.net/ubuntu/+source/ristretto/+bug/1762242)

---

### Post by &amp;KyT$0P# on 2020-05-15
> **pqwoerituytrueiwoq said:**
> What is another basic image view that works

I use Viewnior and it is able to open BMP files, including the sample BMP file from that bug.

---

### Post by pqwoerituytrueiwoq on 2020-05-15
Thanks, i really like how it does ot have the list thumb nails of other images on the left (that feature makes it really slow when you have a folder with 4k+ images on a hdd)

---

### Post by guiverc on 2020-05-15
I recall there being many versions/types of BMP files (I recall differences between OS/2 & windows of the day so maybe win3/win9x which required you to be careful to create files usable by all), however I just found a really old BMP file and it opens fine with `gpicview`  (default viewer of LXDE/legacy-Lubuntu)

[https://packages.ubuntu.com/search?suite=all&searchon=names&keywords=gpicview](https://packages.ubuntu.com/search?suite=all&searchon=names&keywords=gpicview)

---

### Post by pqwoerituytrueiwoq on 2020-05-15
I made a upstream report for this bug:
[https://bugs.launchpad.net/ubuntu/+source/file/+bug/1879019](https://bugs.launchpad.net/ubuntu/+source/file/+bug/1879019)

@[**[COLOR=#DD4814][B]guiverc**[/COLOR][/B]]("https://ubuntuforums.org/member.php?u=2074246") can _[FONT=courier new]file --mime-type /path/to/image.bmp[/FONT]_ give you useful data for your old bmp file?

EDIT: if i save a bmp using gimp it works, but it does not work with screenshots from my BIOS

---

