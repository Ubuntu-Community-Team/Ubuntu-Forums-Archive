---
title: "How to dual boot Ubuntu and Back|Track 2"
date: 2007-12-08
forum: General Help
---

### Post by paranoiahax on 2007-12-08
Hi, I've recently got fed up with Windows so wiped my Windows partition completely, and decided to try out another Distribution of Linux, and my friend recommended Back|Track2, a Slackware distribution for security penetration and testing.

Now I downloaded the live CD, booted it up and installed it successfully, I can even access it from Ubuntu, see it all there nicely.

However, I am unsure on how to access it. I currently have GRUB as my boot loader, would be prepared to switch to LiLo if I had to but I like GRUB the way it is as I've customized it all nicely and I'm quite familiar with it.

As far as I'm aware, Back|Track2 is installed on (hd0,1) and my Ubuntu is installed on (hd0,0)

I have tried doing what I did whenever Windoze screwed up GRUB by "root (hd0,0)" and "(setup (hd0)" and other variations of this but it does not seem to have worked. 

Here is a snippet of my current menu.lst:

```
title		Ubuntu
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=919e75f9-2aee-4076-8b67-5e95f9a42bc1 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
password	--md5 *MY MD5 HASH*

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
#title		Other operating systems:
#root
```

I have tried playing about with this also, e.g. by adding a selection for Back|Track2 like so:

```
title		Back|Track 2
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=919e75f9-2aee-4076-8b67-5e95f9a42bc1 ro quiet splash
initrd		/boot/initrd.img-2.5.22-14-generic
password	--md5 *MY MD5 HASH*
```

but this didn't work and I realised that it probably wouldn't work because it's not the right kernel, but I just tried editing the root partition.

So I was wondering if anyone could give me any help, on how to detect and set up the GRUB automatically, or even manually in menu.lst

P.S. I've tried "sudo update-grub" too, but this did not recognize my other partition and just annoyed me because it added loads of unwanted selections and got rid of my passwords.

Thanks in advance, Para

---

### Post by paranoiahax on 2007-12-08
any one? :(

---

