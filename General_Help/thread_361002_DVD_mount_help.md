---
title: "DVD mount help"
date: 2007-02-13
forum: General Help
---

### Post by Ban-Man on 2007-02-13
Sorry if I missed any post about this befor but I have a Dual Layer DVD iso file that's roughly 6gb and I'd like to mount rather than burn. So far I've tried cdemu .8, and the built in mount iso9660 (I think that's right) function but I always seem to get errors. Anyone have any ideas? Thanks in advance if you do. I'm using edgy eft 6.10 if you're wondering

---

### Post by L14UX_1NS1D3 on 2007-02-13
hi there ban-man.
To answer your question Linux is so cool that you don't need any software to mount an image.
All you need is a little command-line voodoo.
[B]Heres the code :

sudo mount /dir/image.iso -o loop /media/mountpoint/
[/B]

What your doing is mounting the iso image as a loopback device, so replace "mountpont" with something like crom0 or some mount point directory thats in your /media/ directory and type in the path of a the iso image and your all set. ;) 

Hope this helps.
please give me feedback if the advice helped! 8-)

---

### Post by Ban-Man on 2007-02-14
Hey linux inside,

  Thanks a lot that got it to work I had already tried that but I had the iso9660 flag on it too so I guess that was the problem.

---

