---
title: "switch kernel"
date: 2008-04-09
forum: General Help
---

### Post by terranz on 2008-04-09
I have installed 8.04 and damn it it just works like no other distro or version of Ubuntu I have used before (except that you still have to edit grub by hand if you want to change the default boot).

I decided to get the 686 kernel, so after reading around I ```
apt-get install linux-image-686
```

I rebooted and didn't see any new options from the grub boot screen and when I did uname -r I got
```
gerard@gerard-desktop:~$ uname -r
2.6.24-15-generic
gerard@gerard-desktop:~$ 
```

What have I missed out?

*aside* Ubuntu is going to make linux boring. Ubuntu already makes MAC OS and Windows look excessively complicated and difficult to use.  There's hardly anything left to do anymore it just works. :guitar:

---

### Post by Junglizer on 2008-04-09
> **terranz said:**
> I have installed 8.04 and damn it it just works like no other distro or version of Ubuntu I have used before (except that you still have to edit grub by hand if you want to change the default boot).

I decided to get the 686 kernel, so after reading around I ```
apt-get install linux-image-686
```

I rebooted and didn't see any new options from the grub boot screen and when I did uname -r I got
```
gerard@gerard-desktop:~$ uname -r
2.6.24-15-generic
gerard@gerard-desktop:~$ 
```

What have I missed out?

*aside* Ubuntu is going to make linux boring. Ubuntu already makes MAC OS and Windows look excessively complicated and difficult to use.  There's hardly anything left to do anymore it just works. :guitar:

I'm not entirely sure which kernel you were trying to add, but regardless, did you edit your grub config to point to the right image file? Just installing the image isn't likely to do that. 

Also, in regards to your side note: I agree, except that it doesn't always 'just work' but often it does, but I don't like the way Ubuntu 'handles itself' as a Linux distribution, and I don't use it.

---

### Post by bodhi.zazen on 2008-04-09
Ubuntu changed the way it handles kernels. The generic kernel is just fine and unless you wish to compile your own kernel you should stay with it.

Here is anoverview (I could not find another):

[https://lists.ubuntu.com/archives/ubuntu-devel/2006-August/019983.html](https://lists.ubuntu.com/archives/ubuntu-devel/2006-August/019983.html)

And this :

[http://tuxicity.wordpress.com/2007/08/13/linux-ubuntu-2622-9-generic-vs-linux-ubuntu-2622-9-my-architecture/](http://tuxicity.wordpress.com/2007/08/13/linux-ubuntu-2622-9-generic-vs-linux-ubuntu-2622-9-my-architecture/)

---

### Post by terranz on 2008-04-09
I read that the i386 kernel will only address 850ish MB of RAM, what this person mistaken?
The post was about a much older version of Ubuntu.

---

