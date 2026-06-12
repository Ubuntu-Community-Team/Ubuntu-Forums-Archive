---
title: "Data DVD backup encrypted on the fly with LUKS?"
date: 2007-06-22
forum: General Help
---

### Post by ariel on 2007-06-22
Hi, I was wondering if it is possible to burn a data DVD with on the fly LUKS encryption, say with K3b or gnome-baker.

So that when an encrypted CD / DVD is inserted, a password prompt would pop up (like for encrypted USB disks)

I found this:

[http://gentoo-wiki.com/HOWTO_Burn_Encrypted_Optical_Media_With_Luks](http://gentoo-wiki.com/HOWTO_Burn_Encrypted_Optical_Media_With_Luks)

but I'd like a more user friendly, and on-the-fly (no iso pre-generation) solution. I've searched in K3b forums but wasn't able to 
find any reference.

Any clue?

---

### Post by ariel on 2007-06-24
Well... it looks like there is no easy way to do this. So... opening feature requests in k3b/gnomebaker seem to be the next step ;)

---

### Post by ariel on 2007-06-26
Not a lot of people LUKS-encrypting CDs on the fly :)

Finally I'm using a gentoo script that generates and burns the LUKS encrypted CD/DVD automagically. There is a little bug in gnome but no big deal, the thing basically works. The scripts I'm using and the bug description can be found here:

[https://bugs.launchpad.net/ubuntu/+source/gnome-mount/+bug/122241](https://bugs.launchpad.net/ubuntu/+source/gnome-mount/+bug/122241)

---

