---
title: "File system problems + X won't work"
date: 2007-03-31
forum: General Help
---

### Post by tomj on 2007-03-31
Hi,
I have run into loads of problem after compiling the 2.6.20.4 kernel. I used the previous configuration for my old kernel and only changed the system timer to 1000Hz from 250Hz.

X stopped working (also wouldn't work with old kernel) so I started to try and get that to work I was just getting ready to reinstall the nvidia legacy drivers (read that when you change kernel you need to reinstall drivers although I was using the built in drivers). I thought I would try X one last time and X gave an error about not being able to start because of  0 free bytes. So I deleted some files that had been liing around taking up space. The partition still has no space:-( .

'df' give this as output
Filesystem                1k-blocks            Used        Available     Use%  Mounted on
/dev/hda7               5162796       5015040                  0     100%  /

There is 1.4GB free which far less than 5% its more like 28% I thought it might be some corruption but after running e2fsck on it using my old instilation of ubuntu (currently using Kubuntu). It did not return any errors I have scoured google for similar problems but i havn't found any.

Any help would be greatly appreciated

---

