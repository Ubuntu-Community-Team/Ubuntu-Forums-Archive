---
title: "xfce and xubuntu - Same thing?"
date: 2014-06-02
forum: General Help
---

### Post by 777funk on 2014-06-02
I have the following login options after I get past the GRUB screen:
[LIST]
[*]Ubuntu
[*]Ubuntu 2D
[*]Ubuntu Gnome
[*]XFCE
[*]XUbuntu
[/LIST]

Seems like Gnome, Xubuntu, and XFCE have a little more power available for programs that need it. Are they all the same thing? 

Is there anything that's even more stripped down than these versions? I ask because I do audio recording and that tends to have issues if other things are going on in the background. Something as simple as maximizing a window can cause an audio dropout (i.e. XRun). 

thanks for any guidance here!

---

### Post by LastDino on 2014-06-03
From what I know, yes, but I could be wrong. There is more stripped down version of Ubuntu; its called Lubuntu.   However, if you can handle it, I suggest trying out Arc, its something you can quite litrally build from scratch.

---

### Post by sudodus on 2014-06-03
Yes, Lubuntu is the lightest of the Ubuntu flavours. It uses the LXDE desktop environment which is even lighter than Lubuntu.

Openbox is the window manager used by Lubuntu and LXDE. If you run only Openbox, it will be even lighter than LXDE.

But there is a cost too. The environment will be stripped down, and you may need to install some program packages yourself to get all you need.

This link illustrates the usage of RAM (when the computer is running idle after login).

[https://help.ubuntu.com/community/9w/RAM_%26_disk_usage](https://help.ubuntu.com/community/9w/RAM_%26_disk_usage)

---

### Post by sudodus on 2014-06-03
By the way, you can also install ***Ubuntu Studio*** with a low-latency kernel, or install a low-latency kernel in any flavour or derivative of Ubuntu.

```
sudo apt-get install linux-image-{some-version-numbers}-lowlatency
```

It is good for your kind of applications, (but does not serve as well for general purpose tasks where stability is more important than snappiness).

---

