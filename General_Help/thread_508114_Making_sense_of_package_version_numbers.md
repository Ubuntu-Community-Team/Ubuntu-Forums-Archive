---
title: "Making sense of package version numbers"
date: 2007-07-23
forum: General Help
---

### Post by eastern_strider on 2007-07-23
I've seen this question asked several times with no satisfactory answer. Could someone explain how to understand package version numbers?

For example what does the following mean? (the numbers are taken from the libboost-dev package):

```

1.33.1-9ubuntu3

```

Is this newer than this package?

```

1.33.1-7ubuntu1

```

Or are they essentially the same package with slightly different names for some curious reason?

Any insight is appreciated.

---

### Post by zanglang on 2007-07-24
1.33.1 would be "upstream" version number, which means which official release is it based on. I recall from a transcript somewhere 9 would be the Debian version, and 3 would be the Ubuntu modification version... but I might be wrong. :)

So yes, 9ubuntu3 would be newer than 7ubuntu1.

---

### Post by eastern_strider on 2007-07-24
Thanks for your clarification. However, I think sometimes package versions are updated because it belongs to a new ubuntu distribution; not because the package is actually updated.

For example 1.33.1-9ubuntu3 and 1.33.1-7ubuntu1 may actually be the same package named differently because one is coming from feisty and the other from edgy. My question is: is that the case? What exactly do 9 and 1 mean? Is the part before the dash the actual version number?

---

### Post by pointone on 2007-07-24
[http://www.debian.org/doc/debian-policy/ch-controlfields.html#s-f-Version](http://www.debian.org/doc/debian-policy/ch-controlfields.html#s-f-Version)

---

### Post by zanglang on 2007-07-25
> **pointone said:**
> [http://www.debian.org/doc/debian-policy/ch-controlfields.html#s-f-Version](http://www.debian.org/doc/debian-policy/ch-controlfields.html#s-f-Version)

Ah, makes perfect sense now. Thanks for the link. :D

> For example 1.33.1-9ubuntu3 and 1.33.1-7ubuntu1 may actually be the same package named differently because one is coming from feisty and the other from edgy. My question is: is that the case? What exactly do 9 and 1 mean? Is the part before the dash the actual version number?
So that would mean they are from the same *upstream version*, but 9 is from a *higher Debian revision*, perhaps with additional patches applied. 3 and 1 would be additional revisions to the original Debian package, you can check the package changelog to make sure.

---

