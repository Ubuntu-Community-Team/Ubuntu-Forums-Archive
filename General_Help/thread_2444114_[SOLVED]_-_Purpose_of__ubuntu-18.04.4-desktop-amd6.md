---
title: "[SOLVED] - Purpose of  ubuntu-18.04.4-desktop-amd64.{manifest,list,metalink}"
date: 2020-05-24
forum: General Help
---

### Post by warronfrench on 2020-05-24
I believe I am posting to the correct forum for New to Ubuntu Users.

I have been engineering/administering solutions for SUN/Oracle Solaris, HPUX, Irix, and RHEL-variants for over 20 years.  This is my first time looking into Ubuntu|Debian-variants.

I was looking at the download page "[http://mirror.math.princeton.edu/pub/ubuntu-iso/bionic/](http://mirror.math.princeton.edu/pub/ubuntu-iso/bionic/)" and found downloads for server and desktop; which I have no confusion or misgivings about.  I was wondering what the purpose of the following file types are:

[LIST]
[*]ubuntu-18.04.4-desktop-amd64.list
[*]ubuntu-18.04.4-desktop-amd64.manifest
[*]ubuntu-18.04.4-desktop-amd64.metalink
[/LIST]

I have never seen such a file in association with the OSes I have administered before.

Since I am a noob, I will be asking tons of questions, which eventually will die off.  I promise.

---

### Post by dino99 on 2020-05-25
Download protocols  [https://wiki.ubuntu.com/MetalinkIsoDownloads](https://wiki.ubuntu.com/MetalinkIsoDownloads)

---

### Post by warronfrench on 2020-05-28
Thanks dino99.  So a download through a metalink will start the download of a single file at one server and then continue to download if it fails on "server1" by continuing on with "server2" and etcetera until completion of the download.  Then at the end file integrity is confirmed.

---

