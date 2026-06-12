---
title: "Creating GRUB splash image"
date: 2007-08-17
forum: General Help
---

### Post by gabeyg on 2007-08-17
how can i do that?
I know how to add splash image to menu.lst, but don't how to create the image.

---

### Post by ivesjd on 2007-08-17
What format does the image need to be? Do you have any links toa howto or info on it?

---

### Post by gabeyg on 2007-08-17
> **ivesjd said:**
> What format does the image need to be? Do you have any links toa howto or info on it?
Like Fedora 7, I'd like to make splash image format of .xpm then compress by .gz. So I'd like to make xpm image. And no, i don't have any knowledge about howto about this.

---

### Post by joann on 2007-08-26
Hello Gabeyg,

Creating a custom splash image is relativly straight forward. Basicly you just have to make sure the splash image is in the correct format, and the location is properly referenced in the menu.lst file. Read these websites they have a bunch of very useful information. 

[http://gentoo-wiki.com/HOWTO_Splash_image_in_GRUB](http://gentoo-wiki.com/HOWTO_Splash_image_in_GRUB)
[https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)

Also if you want a more custom look try editing the line just below "Pretty colours" :)

Hope this helps...

Happy Customizing
-Joann

---

### Post by nqsonk9 on 2007-08-26
Sorry if i ask a noob question but someone please explain to me what grub splash image is ? It changes the booting image after grub ?
Thanks

---

### Post by erfahren on 2007-08-26
> **nqsonk9 said:**
> Sorry if i ask a noob question but someone please explain to me what grub splash image is ? It changes the booting image after grub ?
Thanks
instead of having the (boring) black screen with white text GRUB menu there is a background image.
hermanzone also has info about that: [http://users.bigpond.net.au/hermanzone/p15.htm#splash](http://users.bigpond.net.au/hermanzone/p15.htm#splash)

here's what I inserted into my menu.lst
```

# My splash image
splashimage=(hd0,4)/boot/ubuntu_grub_splash.xpm.gz
foreground ffffff
background 303030
border 000000

```
my splash image is attached (in PNG format)

---

