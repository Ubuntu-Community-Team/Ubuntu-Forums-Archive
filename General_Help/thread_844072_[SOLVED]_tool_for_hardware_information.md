---
title: "[SOLVED] tool for hardware information"
date: 2008-06-29
forum: General Help
---

### Post by geo909 on 2008-06-29
Hello everybody,
I remember that in ubuntu there was a tool that presented
hardware information like motherboard, sound devices, graphic cards, etc..

Can you tell me its name or the name of any other related program?
(a command line program would also do)


Thanks a lot

---

### Post by sdennie on 2008-06-29
Try:

```

sudo lshw

```

or

```

sudo lshw -html > hardware.html

```

For a html version you can open in a browser.  Or:

```

sudo dmidecode

```

For more technical information.

---

### Post by dentaku65 on 2008-06-29
You can use hardinfo

```
sudo apt-get install hardinfo
```

---

### Post by geo909 on 2008-06-29
Thanks for your replies.

@dentaku65U:Unfortunately I could not find hardinfo on my repos (I use a base installation of debian etch).

Anyway, lshw is exactly what I wanted. there is also a gui so it's really fine.

Now, I was looking info for my graphic card (I have an old compaq presario 700 btw). The only related thing I could find in lshw was:
```
VGA compatible controller
/0/ec000000/1/0


product: VT8636A [ProSavage KN133] AGP4X VGA Controller (TwisterK)
vendor: S3 Inc.
bus info: pci@01:00.0
version: 01
size: 128MB
width: 32 bits
clock: 66MHz
capabilities:
	VGA graphical framebuffer,
	bus mastering,
	PCI capabilities listing
configuration:
	latency: 64
	maxlatency: 255
	mingnt: 4
```

Is that the graphic card info (I'm dumb on those things)? If not, where should I check when running lshw?

Thanks a lot again.

---

### Post by manfer on 2008-06-29
Yes, that is the graphic card info.

The html format not bad but if you want a GUI for that command you can install lshw-gtk. Maybe more easy to analyze all the info.

To install:

prompt:~$ **sudo apt-get install lshw-gtk**

And it must be run with privileges so:

prompt:~$ **sudo lshw -X**

*Note: If you use it, first time it seems it is not showing all the info. Try double click on any entry.*

---

### Post by geo909 on 2008-06-29
Thank you!
I wasn't vey clear (blame my english, I had found the
gui for this and it works fine..

Thanks everybody again

---

