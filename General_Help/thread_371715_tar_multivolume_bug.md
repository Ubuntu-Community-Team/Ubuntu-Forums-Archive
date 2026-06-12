---
title: "tar multivolume bug"
date: 2007-02-27
forum: General Help
---

### Post by accod on 2007-02-27
Hi all,

I'm pretty sure this is a bug in the tar utility packaged with Drapper Drake but before I report it I thought I'd ask here.

Running a fully updated drapper drake install using tar 1.15.1, I get the following when creating a multivolume archive:

/home/hlu1vUWT0KaFsA-xhpdaTABN/cjNx6oZBd4jr1onGpfffghtVjperu6/PMF5RWN,TYzerupAR/atweuS9ev0uhvJAFDtn8NgvVSl/VRgPbWQYPDs66OIkdkSTjVl9rwuflaLkNvrEXA3otQFxe,
Prepare volume #2 for `/dev/nst0' and hit return:
tar: home/hlu1vUWT0KaFsA-xhpdaTABN/cjNx6oZBd4jr1onGpfffghtVjperu6/PMF5RWN,TYzerupAR/atweuS9ev0uhvJAFDtn8NgvVSl/VRgPbWQYPDs66OIkdkSTjVl9rwuflaLkNvrEXA3otQFxe,: file name too long to be stored in a GNU multivolume header

Ignore the weird filenames, I'm backing up an encfs encrypted directory.  This happens with long normally named files too.

tar was called using the following:

tar -cvMf /dev/nst0 /home

Any ideas?

Thanks.

---

### Post by uhldo on 2007-12-18
It's quite an old post but i think is useful !

I've quite the same troubles ...

my tar version is:
tar (GNU tar) 1.18

I've tried with :

*--format=pax*

tested with --multivolume : all ok !

hope that help!
bie,
l.

---

