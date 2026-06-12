---
title: "Ubuntu will boot, but X won't"
date: 2007-07-28
forum: General Help
---

### Post by exaulz on 2007-07-28
Hey guys, I just finished installing a brand new nVidia 8600GT graphics card. I'm under Windows Vista right now, running Aero, everything is sweet.

But, Ubuntu won't start. Yesterday, I remember trying to install the driver for my old integrated graphics card, and, I had to edit some X settings. Alot of weird stuff that I really didn't know what I was doing. I was just pressing "OK" "OK" "OK". But now, Ubuntu will start (like the command-prompt version), but when I type 'startx' I get an error.

If anyone knows about some thing I could install, a command I could run, whatever, please tell me.

Please help!

---

### Post by merlinus on 2007-07-28
At the command prompt:

```

sudo dpkg-reconfigure xserver-xorg

```
You can probably go with the default for most screens, but select "vesa" for your video driver.

Then:
```

startx

```

This should at least get you to a GUI, then you can search how to install the correct video drivers for your card.

-merlin

---

### Post by exaulz on 2007-07-28
Thanks merlinus. I'll try that.

*boots into Ubuntu*

---

### Post by thomasaaron on 2007-07-28
[http://www.nvidia.com/object/linux_display_ia32_100.14.09.html](http://www.nvidia.com/object/linux_display_ia32_100.14.09.html)

Follow the directions on this page exactly (they're at the bottom).
That's how I got my 8600 up and running.

---

### Post by thomasaaron on 2007-07-28
Also, on step 3, make sure you cd into the directory the download is in.

---

### Post by exaulz on 2007-07-28
I did what merlinus told me, and, here's the log file (it's attached) (I got it through accessing the partition through Windows... Explore2FS <3).

Don't know if that'll help.

Thomasaaron, I'll try that. Thankies.

EDIT:

Thomasaaron, how do I download the file through the terminal or whateve rit is I have access to? Remember, I have no GUI now.

EDIT 2:

I'm gonna try to wget the file. Thanks for the link though.

*boots into Ubuntu again*

---

### Post by confused57 on 2007-07-28
> **exaulz said:**
> I did what merlinus told me, and, here's the log file (it's attached) (I got it through accessing the partition through Windows... Explore2FS <3).

Don't know if that'll help.

Thomasaaron, I'll try that. Thankies.

EDIT:

Thomasaaron, how do I download the file through the terminal or whateve rit is I have access to? Remember, I have no GUI now.

EDIT 2:

I'm gonna try to wget the file. Thanks for the link though.

*boots into Ubuntu again*

Here's instructions by bodhi.zazen for installing from Nvidia's website:
[http://ubuntuforums.org/showpost.php?p=3000269&postcount=28](http://ubuntuforums.org/showpost.php?p=3000269&postcount=28)

---

### Post by exaulz on 2007-07-28
> **thomasaaron said:**
> [http://www.nvidia.com/object/linux_display_ia32_100.14.09.html](http://www.nvidia.com/object/linux_display_ia32_100.14.09.html)

Follow the directions on this page exactly (they're at the bottom).
That's how I got my 8600 up and running.
THANK YOU SO MUCH! I'm writing this post from Ubuntu. THANK YOU! ^_^;;

*gives you some sugar for your Ubuntu coffee*

---

