---
title: "Deleting a sys file."
date: 2014-12-30
forum: General Help
---

### Post by Maximilian_F._Blas on 2014-12-30
I'm running ubuntu. And need to delete an entire folder in /sys/module/ but it won't let me, not even when using sudo. Claiming it's not permitted

---

### Post by Bucky Ball on 2014-12-30
Welcome. You are using sudo in a terminal? You could try 'sudo nautilus' which will open the file manager as root. Be careful what you are doing in there as root because then you will have permission to delete anything!

What are you attempting to delete, exactly?

---

### Post by Maximilian_F._Blas on 2014-12-30
/sys/module/ideapad_laptop.  I need to delete this to disable the permanent hard block on my wifi router. I tried what you said though and again it says operation not permitted

---

### Post by QIII on 2014-12-30
I'm sorry if I don't understand.

Are you saying that removing a system directory on your computer will affect your router itself, or that you believe it will allow you to connect to your router?

If the latter, on what basis have you determined this?

---

### Post by Bucky Ball on 2014-12-30
*Thread moved to **General Help**.*

Unsure how that got there. Did you install manually? When you say a block on your router, what do you mean exactly? Your wifi is not seeing the router? Could you give more detail about what is actually happening and how you came to the conclusion you need to delete that file?

* QIII beat me to it, but what they said. :-k

---

### Post by deadflowr on 2014-12-30
It's probably not allowing you delete it because it currently in use.
what's
```
lsmod
```
show

also there is probably a better solution, like blacklisting the module rather than deleting it.

---

### Post by CharlesA on 2014-12-30
Maybe this will help?
[http://billauer.co.il/blog/2014/08/linux-ubuntu-yoga-hardware-blocked-wireless-lan/](http://billauer.co.il/blog/2014/08/linux-ubuntu-yoga-hardware-blocked-wireless-lan/)

---

### Post by Maximilian_F._Blas on 2014-12-30
So here's the situation. I'm running a lenovo yoga 2. Unfortunately many people have had problems where an irreversible hardblock happens on the network card, that is, instead of it being a software issue, it's a hardware issue. Usually this is because an actual switch is turned off on the machine itself, however, in these scenarios there is no switch. This is because of a driver issue with lenovo. I used to run windows, this is when it happened. The driver error kicked and the wifi setting was permanently off. For a long time though I wanted to switch to ubuntu so I did. However the driver installed itself onto ubuntu (just like other people) and now I can't delete no matter how hard I try. The downside is it removes the capabilities of lenovo specific buttons but this is fine for me. I just want my machine to access internet.

I'd like to blacklist the module but I don't know how

I also can't read or understand any of this. [http://billauer.co.il/blog/2014/08/linux-ubuntu-yoga-hardware-blocked-wireless-lan/](http://billauer.co.il/blog/2014/08/linux-ubuntu-yoga-hardware-blocked-wireless-lan/)

---

### Post by Bucky Ball on 2014-12-30
Yes, that link is fairly involved, but looks like you are on the right track ...

---

### Post by Maximilian_F._Blas on 2014-12-30
Can anybody give me an instructions to blacklist the module in an understandable format? I have a lot of experience with terminal but I just don't understand that link

---

### Post by CharlesA on 2014-12-31
I don't think just blacklisting that driver is going to help. Judging from the instructions on the link above, there are several things that need to be done before it will work.

It looks like the "simple" fix is to compile an updated driver from scratch and install it that way, but that is a bit involved as well.

---

### Post by Maximilian_F._Blas on 2014-12-31
yeah, i just successfully black listed by using **sudo gedit /etc/modprobe.d/blacklist.conf** and added *blacklist **ideapad_laptop* at the bottom. the driver is now gone, i just need to figure out how to switch the hard lock off and it will be good. The purpose of blacklisting the driver was to prevent the faulty laptop hardware from slamming the hard lock on every boot.

---

### Post by Bucky Ball on 2014-12-31
From your link:

> Blacklisting this module has been suggested for Yoga laptops all over the web. In particular this post suggests to insmod the module once with a hack that forces the Wifi on, and then blacklist it.

But by blacklisting ideapad-laptop, the computer loses some precious functionality, including disabling Wifi and the touchpad by pressing a button. So this is not an appealing solution.

Starting to wonder if you're heading down the wrong avenue ... :-k

---

### Post by Maximilian_F._Blas on 2014-12-31
after blacklisting i lost no functionality :) but of course that doesn't flip the switch back off for the hard block. so I'm trying a different method by actually modifying the driver. using that tutorial from before. ill let you know how it goes in a sec

---

### Post by Maximilian_F._Blas on 2014-12-31
i feel embarrassed to ask this, but can someone please compile this file for me? i don't understand how to use gcc nor do i know if its even on my machine. the file is [here]("http://billauer.co.il/download/yoga-wifi-fix.zip"). and its from that link posted earlier.

---

### Post by CharlesA on 2014-12-31
You have to compile it on your machine.

gcc should be in the build-essential meta package:

```
sudo apt-get install build-essential
```

---

### Post by Maximilian_F._Blas on 2014-12-31
so i just use this in terminal and a window will popup to select the .c file?

---

### Post by Maximilian_F._Blas on 2014-12-31
it says E: Unable to locate package build-essential

---

### Post by schragge on 2014-12-31
Then update your package database first:
```

sudo apt-get update
sudo apt-get install build-essential

```

---

### Post by Maximilian_F._Blas on 2014-12-31
Thanks everyone for your help! I compiled the file successfully and swapped it with the bad driver :) I could not have done it without you all!

---

### Post by Maximilian_F._Blas on 2014-12-31
Thanks everyone for your help! I compiled the file successfully and swapped it with the bad driver :) I could not have done it without you all!

---

### Post by Bucky Ball on 2014-12-31
Great news! Enjoy and good luck. ;)

---

