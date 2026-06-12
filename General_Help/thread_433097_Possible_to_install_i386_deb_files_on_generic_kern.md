---
title: "Possible to install i386 deb files on generic kernel"
date: 2007-05-04
forum: General Help
---

### Post by lbyrd33 on 2007-05-04
I have a 64 bit machine running the generic kernel. Is it possible to force install a deb program written in i386 on my machine?

---

### Post by crispy_420 on 2007-05-05
So you have standard install and not 64 bit version? Should be no issues as long as dependenciea are met. In that case your processor spec should not matter at all.

---

### Post by lbyrd33 on 2007-05-05
> **crispy_420 said:**
> So you have standard install and not 64 bit version? Should be no issues as long as dependenciea are met. In that case your processor spec should not matter at all.

I orginally did a fresh install of Feisty using the 64 bit version. When update manager upgraded my kernel it installed the generic kernel. When I try to install a i386 deb file in a terminal or whatever it says that the file architecture is not compatible. Im just a little confused about why I cant get around this.

---

### Post by crispy_420 on 2007-05-05
I don't think you can install 32bit in 64bit. Try installing 32bit till 64 matures.

---

### Post by lbyrd33 on 2007-05-06
> **crispy_420 said:**
> I don't think you can install 32bit in 64bit. Try installing 32bit till 64 matures.

Im sorry, I thought the generic kernel would be able to handle both types of files.

---

### Post by lbyrd33 on 2007-05-11
> **crispy_420 said:**
> I don't think you can install 32bit in 64bit. Try installing 32bit till 64 matures.

I figured out how to get this to work on another forum:

```

sudo dpkg -i --force-architecture packagename_i386.deb

```

and have these packages installed

 ```

sudo apt-get install ia32-libs ia32-libs-sdl ia32-libs-gtk

```

---

