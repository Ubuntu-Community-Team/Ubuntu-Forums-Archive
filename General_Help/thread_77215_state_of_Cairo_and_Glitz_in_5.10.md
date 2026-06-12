---
title: "state of Cairo and Glitz in 5.10"
date: 2005-10-16
forum: General Help
---

### Post by Rounan on 2005-10-16
I was very excited to hear that Ubuntu 5.10 uses GTK 2.8, which includes Cairo support. GTK rendering with Cairo using the glitz (OpenGL) backend paves the way for (finally) getting the GPU to do most of the graphics processing work rather than the CPU.

So, I installed 5.10 and libglitz. However, my Athlon64 3700+ still uses >50% CPU when I drag one window over another quickly. Either I've misunderstood what the GTK2.8 migration was supposed to accomplish, or I've missed some configuration somewhere along the way.

The only thing I can find on this topic is [this article]("http://madpenguin.org/cms/index.php/?m=show&id=5145&page=2"), which is a preview of the 5.10 RC. It says I need to install a cairo-capable theme and references CVS, which I'm hesitant to use.

What is the state of Cairo/glitz support in Ubuntu repositories, what do I have to do to get it, and is it going to fix the 50%-CPU-to-move-a-window problem?

---

### Post by zerwas on 2005-10-16
Hi,

I am also really interested in this :)
I tried the things that is spoken of in your link.
Using the clearlooks-cairo CVS-theme breaks mostly everything :rolleyes: (on my Ubuntu).

---

### Post by yage on 2005-10-16
This answers some questions [http://www.gnome.org/~davyd/gnome-2-12/]("http://www.gnome.org/~davyd/gnome-2-12/")

---

### Post by Rounan on 2005-10-16
The link makes it sound like GTK2.8 makes cairo rendering available to developers, but it's up to individual app developers to use it. Is this the case? If so, are these ports a priority in Ubuntu?

---

### Post by yage on 2005-10-16
Been searching some pages now and it's like you wrote. It's only an API and ther are no realday apps ready yet... There are only som exaple "apps" like a clock.. The dev packages are in breezy as fare as i can see. 
For even more info take a look at the cairo page. [http://cairographics.org]("http://cairographics.org")

---

