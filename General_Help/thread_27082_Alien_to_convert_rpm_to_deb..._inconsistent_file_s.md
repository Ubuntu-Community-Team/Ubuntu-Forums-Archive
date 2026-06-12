---
title: "Alien to convert rpm to deb... inconsistent file sizes"
date: 2005-04-14
forum: General Help
---

### Post by shakin on 2005-04-14
I'm actually wondering how alien works. I converted the fish shell from rpm to deb and it installed perfectly. The source rpm was 150k and the resulting deb was 1.6MB. I looked through the deb and there are a lot of extra files in it, but I don't know what they're for.

Also, I just reconverted the rpm to deb and the file size is a more appropriate 150k. Why is it suddenly much different? Why doesn't it package all the same files as the first deb did? Does alien package any dependencies along with the deb? This would mean that the deb would be different depending on what is installed on the machine that makes the deb.

This indicates to me that packaging a deb this way doesn't make it good for redistribution. Does an alien deb still include a list of dependencies so apt can download them if needed?

Thanks.

---

### Post by Bob D. on 2005-04-15
While an interesting question, it may be a bit obscure for most of the denizens of these forums, me included.  ;-)

Might be interesting to write the developer of alien and see what he says. You can write him here: [email]joey@kitenet.net[/email]

He also has a comparison of the different package formats that may be of interest here: [http://www.kitenet.net/~joey/pkg-comp/](http://www.kitenet.net/~joey/pkg-comp/)

Do post  back what you hear from Joey.

Bob

---

### Post by shakin on 2005-04-15
Thanks Bob, will do.

---

