---
title: "Ubuntu boots directly to text-only mode"
date: 2014-05-23
forum: General Help
---

### Post by fried1ninja on 2014-05-23
Hey there everyone, before I get to blabbering on, I would like to note that I am an novice linux user. 

So. heres my problem from the beginning:

I was switching graphics drivers from open source to proprietary so I can run games better. I made the switch, and tried to reboot. the logout button was not working in LXDE. So I opened a termnial and typed "lxsession", and that usually logs me out. Well I rebooted, and the splash screen was completely gone, the boot loader I was still able to see (where I choose between booting into Ubuntu or doing a memtest). 

The system booted up fine, so I decided I was going to disable the splash screen. I edited /etc/default/grub, and replaced "quiet splash" with "text" 
I saved, exited, updated grub via terminal, and rebooted. 

The Splash screen was now gone and replaced with text. Just what I wanted - cool. But when it booted, it just took me directly to text-only mode. I tried startx, but it just gave me a black screen that hung. 

So how would I go about fixing this? Should I login to text-only mode and edit the grub file back to quiet splash? 

Thanks for sticking with me and reading all of this. I can't wait for some answers.

---

### Post by fried1ninja on 2014-05-23
I forgot to add; when I logged out of LXDE with "lxsession", the screen turned into a bunch of lines and hung (I had to do a hard shutdown)

---

### Post by steeldriver on 2014-05-23
Try editing it back to just an empty string

```

GRUB_CMDLINE_LINUX_DEFAULT=""

```

(and then running sudo update-grub of course) - that should remove the splash, but boot to the default graphical display manager instead of just a text console

---

### Post by fried1ninja on 2014-05-23
I knew there was something fishy about "text". Thats what I don't remember typing back on my first install. I was going off of a tutorial on how to disable the splash screen since I couldn't remember. Anyways, thanks a lot.

---

