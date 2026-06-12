---
title: "Ram disk ?"
date: 2018-08-20
forum: General Help
---

### Post by raleigh3 on 2018-08-20
I have 8 Gb of ram and never even come close to using that amount.

Would a ram disk be a waste of time?

If this is to be believed, (Article is dated around 2011)

```
http://ubuntuguide.net/ubuntu-using-ramdisk-for-better-performance-and-fast-response
```

Ubuntu by default uses a half of physical memory (RAM) as ramdisk, and it is mounted onto /dev/shm

/dev/shm is not in my fstab.

---

### Post by oldfred on 2018-08-20
Ubuntu uses all your RAM as you use applications. Only then if you load more than your RAM does it free some for that app. Often we go back and use a previous app and then it already is in RAM. 

       Linux ate my RAM! -  memory use cache
[http://www.linuxatemyram.com/](http://www.linuxatemyram.com/)
Difference between Details screen on RAM and free command
[http://askubuntu.com/questions/743649/new-16gb-of-ram-installed-yet-i-see-15-3-on-my-system-why?noredirect=1#comment1106622_743649](http://askubuntu.com/questions/743649/new-16gb-of-ram-installed-yet-i-see-15-3-on-my-system-why?noredirect=1#comment1106622_743649)

---

### Post by HermanAB on 2018-08-21
Howdy, 
Note that tmpfs is a RAM disk.  Therefore, /tmp is a RAM disk.  

You can put anything there that you want to be able to access faster.  You can also use tmpfs to make one of your own.

---

### Post by Holger_Gehrke on 2018-08-21
Not everything that gets mounted is in '/etc/fstab'. To find out what is mounted you can look at '/etc/mtab'  or just enter 'mount' in the shell without any options or parameters. 

tmpfs is a dynamic ramdisk, it uses as much ram as it needs but only grows up to the size given as an option at mount time. An empty tmpfs uses very little space.

The speed advantage of a ram disk is not as pronounced as one would think because of caching. Putting files that get written to a lot on a ramdisk might help prolonging the life of a SSD.

Be careful about filling up a ramdisk, though. The system starts to swap long before there's no RAM available. I've seen it happen on my 4GB machine when there was still more than 1GB free (not just available, actually unused). The setting "vm.swappiness" in /etc/sysctl.conf is supposed to control this behaviour (the lower, the less likelihood of swapping), but I'm still looking for just the right value to set it to,

Holger

---

### Post by Tadaen_Sylvermane on 2018-08-21
I find ramdisks to be worth it for very few things. In my case, 1 thing. Minecraft. It makes a significant difference. Beyond that I don't know what benefit it provides > an ssd. I know they are good for scratch disks as well.

---

### Post by Yellow Pasque on 2018-08-21
> The system starts to swap long before there's no RAM available. I've seen it happen on my 4GB machine when there was still more than 1GB free (not just available, actually unused).

You seem to be confused. That's what you want to happen. I think you should read this: [https://askubuntu.com/a/184221](https://askubuntu.com/a/184221)
It is a well-written explanation that doesn't require understanding the gory details of a virtual memory system.

---

### Post by Autodave on 2018-08-21
My own opinion would be to get an SSD to use for your boot and programs. You can save all of your music, pics, videos to your spinning HD. An SSD will give you much more speed than you have with a spinning HD. While not as fast as a RAM drive, it gets close.  You can now find 120G SSDs for less than $50 US.

---

### Post by Yellow Pasque on 2018-08-21
> **Autodave said:**
> My own opinion would be to get an SSD to use for your boot and programs.

Where did OP say that s/he didn't have an SSD?

---

### Post by raleigh3 on 2018-08-21
I prefer platter drives. They last much longer.

---

### Post by HermanAB on 2018-08-22
Err... an SSD should outlast you.  A spinning rust thingy not so much.

---

### Post by raleigh3 on 2018-08-23
> **HermanAB said:**
> Howdy, 
Note that tmpfs is a RAM disk.  Therefore, /tmp is a RAM disk.  

You can put anything there that you want to be able to access faster.  You can also use tmpfs to make one of your own.

So if I copied my browser there, would it run any faster?

Or is Ubuntu already doing that in some manner ?

And then I would have to think about files like my bookmarks....Would I have to manually copy them from /tmp to my .mozilla dir?

---

### Post by Yellow Pasque on 2018-08-23
[https://wiki.archlinux.org/index.php/Firefox/Profile_on_RAM](https://wiki.archlinux.org/index.php/Firefox/Profile_on_RAM)

---

