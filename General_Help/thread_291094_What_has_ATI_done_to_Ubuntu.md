---
title: "What has ATI done to Ubuntu?"
date: 2006-11-02
forum: General Help
---

### Post by jrohde on 2006-11-02
Hi,

I have a spare pc, on which I'm trying to install Ubuntu Edgy, because I want to give Xen a try.

I installed Edgy 64 bit, using text mode on the alternate CD because of problems with the graphics adapter (ATI Radeon X700 SE). This worked, except for XEN that apparently have an issue with the 64 bit kernel.

I then downloaded the 32 bit edition of Edgy Alternate CD, in order to do the same with this. This time, the installation process doesn't work at all! Again it is ATI that is the problem, but this time I can't make it work after a text mode installation, by installing the ATI proprietary driver. I'm stuck with a black screen, and no keyboard. All I can do is to switch off power. 

I _can_ start in recovery mode, and then perform a startx. Gnome comes up perfectly! Weird...

I appeal to the Ubuntu community for help. I would hate to have to go and buy a nVidia card because of this!

Thanks,

Jakob

---

### Post by Joe_CoT on 2006-11-02
The reason is that Ubuntu by default uses the open source ati or radeon driver for ATI cards -- this doesn't always work for newer ati cards.

Install with the text mode install. Afterwards, boot in recovery mode. From recovery mode:

```
nano -w /etc/X11/xorg.conf
```

From there, find the device section for your video card. Change the driver from "ati" or "radeon" to "vesa". save, exit, restart in normal mode. X-window should come up fine.

You'll probably not get the resolution or frame rate you want. You can install the [ATI binary driver](https://help.ubuntu.com/community/BinaryDriverHowto/ATI) to solve this.

And believe me, I share your ATI pain ;)

---

### Post by jrohde on 2006-11-02
Hi Joe_CoT

What I don't understand is, why it worked fine with the fglrx driver using Ubuntu 64 bit, but it doesn't work using Ubuntu 32 bit!

There must be more differences besides the architecture.

Jakob

---

### Post by jrohde on 2006-11-02
This is really weird!

If I boot in recovery mode, and the run "startx", X is started ok with fglrx as driver and with the correct resolution. But if I just boot in normal mode - using the same driver - the computer halts, and the keyboard doesn't work.

And if I boot using the vesa driver, I get X and Gnome ok, except for the resolution is only 1024x768. Now, if I open a command line and edit xorg.conf, change vesa to fglrx, save and then hit CTRL-ALT-BCKSP, X and Gnome starts ok and with the right resolution, which is 1440x900.

And remember - this problem wasn't there, when I used Edgy 64 bits.

Any idea would be appreciated.

Jakob

---

### Post by jrohde on 2006-11-02
Hi again,

Well, I got tired of waiting for a response, so I went out and bought a new graphics adaptor, a GeForce 6200, and it seems to be working ok.

Jakob

---

