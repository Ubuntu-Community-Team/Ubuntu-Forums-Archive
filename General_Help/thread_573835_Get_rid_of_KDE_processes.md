---
title: "Get rid of KDE processes"
date: 2007-10-12
forum: General Help
---

### Post by th_11 on 2007-10-12
Hey,
I have Feisty and at some point I decided to install KDE... Well, I really doesn't like it or use it BUT I still wouldn't completely remove it as it has some applications I use (like Konqueror and some other programs that came into my panel after installing KDE).

Now everything is almost fine as I just don't choose KDE as my session handler on the login screen, I still can use Konqueror etc. But the problem I just found out is that there are ALOT of "KDE processes" running on my Gnome session.

For example:
[B]khelper
kthread
kswapd0
kblockd/0
ksuspend_usbd
khubd[/B]

and many more!

I would like to know how to make those processes not to start everytime I log on to my Gnome desktop? Are they really even needed as I don't use KDE itself at all?

---

### Post by sstusick on 2007-10-12
If you are using any of the KDE programs, Gnome might need these processes to run such programs.

---

### Post by th_11 on 2007-10-12
Ahh ok, then I need to leave those processes running I think.

---

### Post by mk04 on 2007-10-24
I got the same question. Originally I installed Gutsy with Kubuntu but I decided to remove Kubuntu and install Ubuntu. Using this method: [http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

But there are still KDE processes in the system process. All of them only running under user root and using "0 bytes" of memory. How do I get rid of these. 

BTW, I am not running any KDE programs. Only programs I install so far was XMMS, Gnomad2, and AutoMatix.

---

