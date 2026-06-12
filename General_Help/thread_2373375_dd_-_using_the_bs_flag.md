---
title: "dd - using the bs flag"
date: 2017-10-05
forum: General Help
---

### Post by CaptainMark on 2017-10-05
I see many guides on copying a .img file to a drive (usually a usb or sc card) using dd and I have been doing this on and off for many years and every different guide seems to give a different value to use for the bs flag, I have a basic understanding of what this flag does, my question is that if a guide for dd'ing a particular image say to use bs=4M and you use a different bs value will this just make the dd run take longer or will it actually incorrectly image the disk and result in a corrupt filesystem on the drive?

I've wondered this many times over the years but most specifically I'm asking this now because I have an image to write and can't find the bs value to use for it.

Many Thanks for answers
Regards
Mark

---

### Post by deadflowr on 2017-10-05
As far as I know block size is dependent on hard drive for best results.
Setting any ole hard drive to something like bs=4m may not be the most efficient way.
Sometimes less can actually be more.
A nifty article on it here:
[http://blog.tdg5.com/tuning-dd-block-size/]("http://blog.tdg5.com/tuning-dd-block-size/")

---

### Post by sudodus on 2017-10-05
The block size has an influence on the copying speed. It may be different in different computers, but generally I would say, that you get full speed at 4096 bytes, bs=4096 alias bs=4K (upper case K). See the following link,

[My standard dd block size is bs=4096](https://askubuntu.com/questions/931581/flashing-ubuntu-iso-to-usb-stick-with-dd/931588#931588)

---

