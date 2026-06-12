---
title: "Snap packages"
date: 2016-07-11
forum: General Help
---

### Post by Chanath on 2016-07-11
Has anyone created a snap package from a deb package or from other source? If so, could you write a how to? I know there are snap packages to download and use, but would like to create one from a deb package.

---

### Post by dino99 on 2016-07-11
The place to glance at: [https://developer.ubuntu.com/en/snappy/build-apps/](https://developer.ubuntu.com/en/snappy/build-apps/)
and many other threads from your favorite search engine of course ):P.

---

### Post by Chanath on 2016-07-11
> **dino99 said:**
> The place to glance at: [https://developer.ubuntu.com/en/snappy/build-apps/](https://developer.ubuntu.com/en/snappy/build-apps/)
and many other threads from your favorite search engine of course ):P.
I've been there. Do you understand anything in it to create a snap package out of a existing deb package?

---

### Post by mactrent2 on 2016-07-11
> **Chanath said:**
> I've been there. Do you understand anything in it to create a snap package out of a existing deb package?

Looks like it's supposed to make a snap out of the git/tar/whatever else that the deb package was made from, so as to skip the middleman.  That being said, if you still want to use the deb, there's the [FONT=trebuchet ms]stage-packages[/FONT] option in the .yaml file.  Looking at examples in the [wiki]("https://wiki.ubuntu.com/Snappy/Parts"), I'd say you could make a null-plugin that would build no code, then just pull in the debs as dependencies.

I'd love to hear how this works for you.  ;)

---

