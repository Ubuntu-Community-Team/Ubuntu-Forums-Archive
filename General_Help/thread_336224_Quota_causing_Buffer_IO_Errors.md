---
title: "Quota causing Buffer I/O Errors"
date: 2007-01-11
forum: General Help
---

### Post by cjansen on 2007-01-11
Good morning

I'm in the middle of setting up a hosting server for work but I ran into an odd problem with quota

As soon as I added usrquota and grpquota to the options on hda1 in fstab I got Buffer I/O errors during boot. As if the hard drive was starting to fail. If I remove them from fstab then the problem goes away.

This is happening on the ubuntu server 6.10 and quota was installed using apt-get. I've never used quota before so I'm at a complete loss.

Other than that ubuntu has been wonderful. I've used slackware for quite some time but the apt-get package management is rockin' my world. =)

---

