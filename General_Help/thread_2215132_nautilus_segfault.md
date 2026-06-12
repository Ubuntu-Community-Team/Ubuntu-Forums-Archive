---
title: "nautilus segfault"
date: 2014-04-04
forum: General Help
---

### Post by Pedroski55 on 2014-04-04
I'm still getting a nautilus segfault:

Apr  5 10:10:53 pedro-bedro kernel: [13202.344455] nautilus[1826]: segfault at 9e7de24 ip 09e7de24 sp bf9ead84 error 15

This is Ubuntu 12.04.02 

I just opened the file manager to look for a file, did a search for it, then right clicked to look at its properties. Bang, nautilus crashed. 

Maybe someone knows what is causing this, or can pass this on to someone who might be able to fix it.

Thanks.

---

### Post by ibjsb4 on 2014-04-05
Try opening it in terminal and look for errors.

```
nautilus
```

It also looks like you haven't updated/upgraded for while (12.04.02).  Why is that?

---

### Post by Pedroski55 on 2014-04-05
Thanks for the reply.
pedro@pedro-bedro:~$ uname -a
Linux pedro-bedro 3.5.0-23-generic #35~precise1-Ubuntu SMP Fri Jan 25 17:15:33 UTC 2013 i686 athlon i386 GNU/Linux
pedro@pedro-bedro:~$ 

This is Ubuntu 12.04 LTS, supposed to go for 5 years. I update very regularly.

nautilus in a terminal does not show any errors, it just opens a file browser window

---

### Post by ibjsb4 on 2014-04-05
Yes, 12.04 has 5 years of support, but you say your running 12.04.02 and the latest version is 12.04.04.

Don't yet know what to say about nautilus.  Got any PPA's (third party software) installed?  Maybe a reinstall?  How often does nautilus crash?

Some bug reports

[http://www.google.com/search?q=nautilus%20segfault%20ubuntu%2012.04](http://www.google.com/search?q=nautilus%20segfault%20ubuntu%2012.04)

---

### Post by tgalati4 on 2014-04-05
You can run a self-check:

```
nautilus -c
```

---

### Post by Pedroski55 on 2014-04-06
nautilus -c shows no problems. This is a reinstall. I wiped the partion clean, deleted all data, took a long time, then reinstalled, because I was getting so many problems. 

Not unconnected, I suppose, is the fact that this Toshiba laptop will not run Ubuntu's latest kernels. I cannot boot with "menuentry 'Ubuntu, with Linux 3.5.0-48-generic' or some other more recent kernels. They get some kind of recursive fault, the screen fills with kernel panic text, then freezes. I cannot find this text in the logs. I suppose the kernel dumps it to tty.

A reinstall installed 3.5.0-23-generic, which boots fine, no problems. I was going to buy a new laptop, suspecting hardware problems, but I also run Fedora and Windows on this Toshiba, both of which work fine, no crashes. Fedora is a lot further ahead with the kernel than Ubuntu. It has no boot problems.

I use this laptop everyday, I need it to boot ok, not crash.

Now I am waiting for the next kernel update, to see if that works. Sooner or later, the problem will go away. A good tip for laymen like me though, is to have more than one system installed. They probably won't both go wrong at the same time. I had a similar problem with Fed 17. I just left Fed alone for a year, then it worked again!

---

### Post by mircea273 on 2014-04-06
It may be that you experience this issue [https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1270542](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1270542)  or this [https://bugs.launchpad.net/ubuntu/+source/nautilus-python/+bug/1203349](https://bugs.launchpad.net/ubuntu/+source/nautilus-python/+bug/1203349)

Personally I think the problem is related to the thumbnailer. It crashes when invalid media files are present in a folder. If you open other folder that has no such file it usually works. It may be that you have some zero sized media file or an invalid one and this triggers the crash...I hope they will fix it soon.

---

### Post by ibjsb4 on 2014-04-06
> **Pedroski55 said:**
> 
Not unconnected, I suppose, is the fact that this Toshiba laptop will not run Ubuntu's latest kernels. I cannot boot with "menuentry 'Ubuntu, with Linux 3.5.0-48-generic' or some other more recent kernels. They get some kind of recursive fault, the screen fills with kernel panic text, then freezes. I cannot find this text in the logs. I suppose the kernel dumps it to tty.

A reinstall installed 3.5.0-23-generic, which boots fine, no problems. I was going to buy a new laptop, suspecting hardware problems, but I also run Fedora and Windows on this Toshiba, both of which work fine, no crashes. Fedora is a lot further ahead with the kernel than Ubuntu. It has no boot problems.


I'm not on 12o4 at the moment, but there are several kernel versions to choose from.  I run 12o4 on the (up to date) 3.2.xx kernel and I think up to kernel version 3.13 is offered.

---

