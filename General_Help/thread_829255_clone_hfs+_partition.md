---
title: "clone hfs+ partition"
date: 2008-06-14
forum: General Help
---

### Post by Xiong Chiamiov on 2008-06-14
I thought about posting this in the Apple forum, but it's not Apple-specific, I guess... it'll go there if I can't find any help.

So, in all my OS-experimenting-goodness, I've been trying to install OSX on my 'puter.  I've got a 10gig HFS+ partition all setup for it, but it won't boot into the installer.  That is not the point of this post, but background so you'll understand why I'm trying to do this.

My roomie has OSX installed (in a 30gig partition) on his laptop.  My plan was to use partimage to copy his OSX partition over to our fileserver, then restore from there onto my HFS+ partition, but partimage seems to only work with HFS, not HFS+.

I read something somewhere about using dd, but I believe that will cause problems, considering that my partition is only 10 gigs, and his is 30?  He's only used 10 gigs, so if I was able to copy only used space, I'd be fine.

Both of our computers have Windows and Kubuntu installed (and his obviously OSX).  My fileserver just has Xubuntu.

---

### Post by Martiini on 2009-04-06
edit: clonezilla works
Im also looking for backup/image tool to backup osx leopard hfs+.
Partimage doesn't work with hfs+ ... 
solution is to create dmg or use norton ghost .. what I've found this far.

---

