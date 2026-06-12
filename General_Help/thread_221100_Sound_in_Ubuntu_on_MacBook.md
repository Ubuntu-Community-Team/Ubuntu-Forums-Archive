---
title: "Sound in Ubuntu on MacBook"
date: 2006-07-22
forum: General Help
---

### Post by eyebrowman92 on 2006-07-22
It was said that new kernel updates fixed this problem, but not for me. I just installed ubuntu on my MacBook and there is no sound. I have the latest kernel. Does anyone know how to fix this?

---

### Post by uidzer0 on 2006-11-09
I'm trying to get sound working with 6.10... No luck so far it acts like it's working but I don't get any output. Has anyone had any luck?

-Ben

---

### Post by jasonparekh on 2006-11-09
Hi Ben,

Are you running the stock Ubuntu kernel (2.6.17)?

If so, you may need to apply the Mactel patches (I'm not sure, I don't recall trying sound on the stock kernel, I compiled my own pretty much right away).

Hopefully someone else can give more insight to the situation, and I'm assuming you've searched past threads.

Compiling your own kernel isn't really that difficult, and I'd recommend it.  There should be a HOWTO for the Ubuntu/Debian way (using make-kpkg).

jason
[http://www.jasonparekh.com/linux-on-macbook]("http://www.jasonparekh.com/linux-on-macbook")

---

### Post by uidzer0 on 2006-11-10
Hey Jason,

Thanks for the reply - I'll give it a shot

---

### Post by uidzer0 on 2006-11-11
All of the kernel patches look like they are for the macbook, I am running the macbook pro... Does the same patch apply?

---

### Post by Yfrwlf on 2007-03-11
To get sound working on a Macbook *Pro*, all you have to do to my knowledge is go to the volume control preferences, enable all of the volume controls, then unmute them all, then go to the switches tab and enable the "line in as output" switch.  You should then have working sound.  There are only certain ones you actually have to have unmuted but I just do them all.

As for a regular Macbook, I don't know if this will work.

---

### Post by RelativelyQuantum on 2007-12-31
> **Yfrwlf said:**
> As for a regular Macbook, I don't know if this will work.

I just tried, and it doesn't. Here's something interesting though:

[http://ubuntuforums.org/showthread.php?t=555730](http://ubuntuforums.org/showthread.php?t=555730)

I haven't had much luck with it, but it seems others have. It might be worth a shot. I'll probably try again just to make entirely certain I did everything right.

Hope this helps.

---

### Post by RelativelyQuantum on 2008-01-06
Just so everyone is clear:

I've tried a number of things to get sound working, and the method in this tutorial doesn't work:

[http://help.ubuntu.com/community/MacBook_Santa_Rosa](http://help.ubuntu.com/community/MacBook_Santa_Rosa)

 I've recently gotten Gutsy to interface with my wireless card, but otherwise I'm still having alot of trouble.

---

