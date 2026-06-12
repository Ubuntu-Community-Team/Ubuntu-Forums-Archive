---
title: "Making a disk, into a .iso"
date: 2006-10-12
forum: General Help
---

### Post by Crooksey on 2006-10-12
Im using qemu, and i need to run windows for my pascal class, how can i convert my windows 9in1 disk into a .iso, or whats the best way to create a hardrive image from a friends windows machine?

Thanks.

---

### Post by kuja on 2006-10-12
Something about this smells illegal...

---

### Post by Crooksey on 2006-10-12
What the fact i have an XP disk, all i want to do is install it through ubuntu, i payed for it, i have the cd key, i can install it how i like.

---

### Post by kuja on 2006-10-12
I was particularly referring to the second option, which, if possible, would circumvent entering the cd key. Anyhow, there should be several ways to do it. I'm not sure, but I think if you go something like

cat /dev/cdrom > winxp.iso

that might be able to create the image. Not something I've played with much. Other than that the only software I've used to do it is K3b, and it does an excellent job IMO.

My 404th post, congratulations me! 404... bean not found?

---

### Post by Ocxic on 2006-10-12
except K3B won't make cd images. if it does for you I'd like to know what you did to get that function...

---

### Post by kuja on 2006-10-12
Hehe, silly. Of course it can. Go into copy cd (or copy dvd), check the box "Only create ISO image", and in the image tab, change the location to whatever you want it to be.

---

### Post by Ocxic on 2006-10-13
I spent a half hour trying to figure that out with no succes and I didn't even see that.....wow i must be losin it.

---

