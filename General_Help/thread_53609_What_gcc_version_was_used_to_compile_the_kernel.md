---
title: "What gcc version was used to compile the kernel?"
date: 2005-08-01
forum: General Help
---

### Post by Kimm on 2005-08-01
How do I know what version of GCC was used to compile the kernel?
I want to get my webcam working and I know a driver that can do that, but last time I tried it I was using the wrong version of gcc and that... wasnt to good for the kernel itselfe...

I'm using the latest kernel for Hoary, 2.6.10-5-686, and I have all repositories enabled if that makes any differance...

Can anyone help?

---

### Post by az on 2005-08-01
[QUOTE=Kimm]How do I know what version of GCC was used to compile the kernel?
I want to get my webcam working and I know a driver that can do that, but last time I tried it I was using the wrong version of gcc and that... wasnt to good for the kernel itselfe...

I'm using the latest kernel for Hoary, 2.6.10-5-686, and I have all repositories enabled if that makes any differance...

Can anyone help?[/QUOTE]

The stock kernel is always conpiled with the stock compiler.

If you installed build-essential and do not have any other compiler installed (like 4.0) you should be good to go.

Look in /usr/share/doc/linux-image* for relevant documentation such as patches and bugfixes in the installed kernel.

Also, do you have the linux-headers package installed?  You will need that (instead of the full linux-tree) to make a module.

---

### Post by Kimm on 2005-08-01
thank you, I had 4.0 installed but I removed that before compilation... but I am stil having trubble with the compiled module. When I try to load it this is what I get:

```

$ sudo ./load
flushing hd...
done.
loading driver module...
insmod: error inserting './zc030x.ko': -1 unknown symbol in module
done.

```

and ofcourse it doesnt work...
I'm using the zc0302 driver if you didnt notice... I dont know if that makes any differance. I'm trying to use it for my Creative Webcam NX.

 ](*,)

---

