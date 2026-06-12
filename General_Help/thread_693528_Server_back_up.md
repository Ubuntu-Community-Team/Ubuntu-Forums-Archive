---
title: "Server back up"
date: 2008-02-11
forum: General Help
---

### Post by wh33t on 2008-02-11
I"ve done a lot of work on a dedicated ubuntu server I rent. I have lots of cron scripts, directory permissions etc set up and I"m curious is their anyways to just export out the entire thing? Short of doing a byte by byte read from the disk?

I'm praying apt-get has a mode for apt-get back up entire machine into one file that can then be imported lol? Here's hoping right?

Any one got any idea how I can do this simply? I'd like to back up the entire machine.

---

### Post by Sokertes on 2008-02-15
You can try mondo/mindi at [http://mondorescue.org/](http://mondorescue.org/) which does just that. You can set it up with your specs that you want (with in reason).

Now the question would be how would you store/transport the backup. Local backup drive on the server? Download it to your computer? Both?

Sokertes

---

### Post by wh33t on 2008-02-15
Thanks for replying. I was beginning to think I had stumped the Ubuntu community :confused:

The server is about 1000km away from so I would be doing remotely to my computer. I have no idea how I would restore my system like that. 

Also... not sure about linux, but I know if you clone a windows pc, you can't simply just move that hdd image to another computer with different motherboard,cpu etc because none of the drivers will line up. Is this similar with Linux?

---

### Post by leftcase on 2008-02-15
Give it a try.

I moved a hard drive only the other day from one desktop computer to a totally different model and it worked without a problem...

I've only noticed a couple of problems in the past when I've tried this:

1) Graphics might be misconfigured (although as you're using a server you mightn't have graphics installed.), in which case run this command to reconfigure them:

```
sudo dpkg-reconfigure xserver-xorg
```

2) A black screen at boot time. In which case:

_Could be a swap issue_

Change the resolution in /etc/usplash.conf to 1024×768

```
sudo swapoff /dev/hda2
sudo mkswap /dev/hda2
```

```
sudo update-initramfs -u
```

_Or a graphics issue_

edit /etc/initramfs-tools/modules

vga16fb
fbcon
vesafb

edit /etc/modprobe.d/blacklist-framebuffer comment out the following (prefix with #)

blacklist vesafb
blacklist vga16fb

last but not least, run the following in a terminal

```
sudo update-initramfs -u
```

Good luck!

---

### Post by wh33t on 2008-02-15
Ha ha thanks for all that. I guess I'll try a remote read during the middle of the night when my webserver is nice and quiet.

And it's ubuntuserver, there is no graphics. :)

---

### Post by Sokertes on 2008-02-17
When using mondo rescue you have the option to restore from a backup which makes it real nice.

---

