---
title: "[Kernel] Upgrading kernel"
date: 2005-10-30
forum: General Help
---

### Post by kal on 2005-10-30
Hi ppl,

I'm new to Ubuntu (I usually use Gentoo) and i would like to compil my own kernel : 2.6.14. By the way, i can't get uspash working anymore with this new kernel, and theres a lot of problem with modules while booting. Is there a pecific way to build his own kernel on ubuntu ?

Thank you ;)

---

### Post by Xian on 2005-10-30
There's a 'Debian way' which is what this wiki topic is based on:

[Kernel Compile How-To](https://wiki.ubuntu.com/KernelHowto)

---

### Post by kal on 2005-10-30
Ok but this article consider we're using kernel-source avalaible with apt-get. I want to use a 2.6.14 downloaded from kernel.org, is it possible ?

---

### Post by Xian on 2005-10-30
Of course. You had asked for a 'specific' method. Debian is after all still Linux, and the same compilation of a kernel by hand will work here just like it will in other distros. Use the same commands that you are already familiar with and the results will be no different. Most people use the Ubuntu source kernel package because they have a certain place they prefer to start from, and then add their own needs from that point.

Get your own source, apply what patches you desire and then pick up in this guide at the Config section:

[Kernel Compile By Hand](https://wiki.ubuntu.com/KernelByHandHowto)

---

### Post by kal on 2005-10-30
All right, that's what I did and i can't get usplash working. Maybe because kernel need to be patched to work with usplash ?

EDIT: Or maybe usplash need a specific initrd?

---

### Post by Xian on 2005-10-30
[QUOTE=kal]All right, that's what I did and i can't get usplash working. Maybe because kernel need to be patched to work with usplash ?

EDIT: Or maybe usplash need a specific initrd?[/QUOTE]
It wouldn't need a specific initrd file because it is not like gensplash or bootsplash, and so does not load the images in a similar fashion. More likely it needs a module to be compiled, but this is just a guess.

If you went through the trouble of compiling the kernel from scratch I'd think you'd be comfortable with using a bootsplash theme instead of that usplash image. It is certainly less than desireable and somewhat gross when compared to a real bootsplash. I mean why do all that work and then use such a crappy boot image?

---

### Post by kal on 2005-10-30
Well,

usplash displays informations about boot such as : loading module, synchronig clock etc...

I won't have these information with fbsplash. By the way, i think that this distribution isn't for me ;)
I don't really know what's going on when I use it and I think I'm going back to my distribution installed on my first partition : Gentoo :)

By the way, this distribution is excellent for newbies and those which does'nt care about how it works, cauz' it works well ;)

Kal

---

### Post by Xian on 2005-10-30
[QUOTE=kal]usplash displays informations about boot such as : loading module, synchronig clock etc...

I won't have these information with fbsplash. [/quote]
Of course you would.
Just enable the verbose mode.

[QUOTE=kal]By the way, i think that this distribution isn't for me ;)
I don't really know what's going on when I use it and I think I'm going back to my distribution installed on my first partition : Gentoo :)[/QUOTE]
You can run Gentoo but you don't know what's going on when you use Ubuntu? The only difference with Ubuntu is that many things whiich are more transparent (by design) in Gentoo take place behind the scenes (by design) in Ubuntu. That is not to say that you can not manage them just as easily. It simply requires a different method.

---

