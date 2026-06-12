---
title: "Reinstall/Rebuild Kernel?"
date: 2007-02-14
forum: General Help
---

### Post by nomad00 on 2007-02-14
Greetings!

I've managed to significantly mess up both my video card configuration and my network card configuration and was thinking the smartest thing to do was start off clean -- except I'm a bit new all this and am not sure how to go about rebuilding the kernel.

Could someone point me to how to do this?

---

### Post by llamakc on 2007-02-14
Most likely you do not need to rebuild the kernel. What sort of video card do you have?

Show us the output of:

```


lspci -v


```

and what your /etc/X11/xorg.conf looks like.

When you speak of your network card configuration, are you using a wired card or wireless? Which wireless card are you using?

---

### Post by nomad00 on 2007-02-14
My video card issue is an odd one, lspci shows my video card as:

```
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AR [Radeon 9600] (prog-if 00 [VGA])
Subsystem: PC Partner Limited Sapphire Radeon 9600XT
Flags: bus master, 66mhz, medium devsel, latency 255, IRQ 177
Memory at e0000000 (32-bit, prefetchable) [size=256M]
I/O ports at 9800 [size=256]
Memory at ff7f0000 (32-bit, non-prefetchable) [size=64k]
Expansion ROM at ff7c0000 [disabled] [size=128k]
Capabilities: [58] AGP version 3.0
Capabilities: [50] Power Management version 2
```

The issue i'm having is that even though glxinfo | grep direct yields Direct Rendering: Yes and fglrxinfo has the ATI information in it, my Screensavers are running at an incredibly slow speed.  

They had been smooth as anything until i tried running that Envy script to try to get as up to date as possible. After that I tried every How-To i could find to get back to 'normal' and I just haven't been able to figure it out.

My network card problem is much more simple.....it simple won't get an IP even though its connected and configured correctly as best as I can tell. And it was working fine...I haven't been able to pin down when it stopped.
edit: its a wired Belkin network card.

Thanks for taking the time to read this! Any help will be greatly appreciated.

---

### Post by llamakc on 2007-02-14
I'm unfamiliar with the Envy script, but unless IT added kernel modules or installed a newer kernel, changing your kernel will most likely not help (unless there are instructions accompanying the script that direct you to do so).

That said, your problem could very well be what ENVY did. Does it have an uninstall feature or uninstall script?

As to the NIC, is the module loaded for it? Can you show us the NIC output from `lspci`, and what modules are currently loaded with `lsmod`?

and of course the output of `ifconfig`

---

### Post by nomad00 on 2007-02-14
since it takes me a bit to transpose the output of the commands (no internet on the linux box at the moment) heres Envy:
[http://www.albertomilone.com/nvidia_scripts1.html]("http://www.albertomilone.com/nvidia_scripts1.html")

posting output in a sec

---

### Post by nomad00 on 2007-02-14
lspci:
```
03:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd RTL-8139/8139C/8139C+ (rev 10)
```

Is there any way to narrow down what we'd want to see from lsmod? Thats a lot to type over :)

edit: ifconfig just yields the lo information

---

### Post by llamakc on 2007-02-14
The script looks awesome. I may give it a try myself. I can't see how that would mess up your network connection. 

As to the problem with the screensavers, you should isolate precisely which ones really slow you down. Maybe that would help figure out the bottleneck?

---

### Post by nomad00 on 2007-02-14
Be careful before running that :)  I'm sure its isolated, as it does appear to work for most people, but after I ran it I ended up unable to load X.

I don't think the two issues are related and I had a fully working system prior to this, so I don't know what I did, but I think it may just be best for me to clean up and start fresh :p 

Any idea how I could do that without doing a full reinstall?

---

### Post by llamakc on 2007-02-14
> **nomad00 said:**
> lspci:
```
03:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd RTL-8139/8139C/8139C+ (rev 10)
```Is there any way to narrow down what we'd want to see from lsmod? Thats a lot to type over :)

edit: ifconfig just yields the lo information

Are you using NetworkManager?

The module for that card is 8139too. Which kernel are you using? Have you tried an older kernel yet?

---

### Post by llamakc on 2007-02-14
> **nomad00 said:**
> Be careful before running that :)  I'm sure its isolated, as it does appear to work for most people, but after I ran it I ended up unable to load X.

I don't think the two issues are related and I had a fully working system prior to this, so I don't know what I did, but I think it may just be best for me to clean up and start fresh :p 

Any idea how I could do that without doing a full reinstall?

I've learned to always keep a separate /home partition so that I can reinstall in case I muck things up. During the reinstall, you just choose to NOT format that partition and make sure it gets mounted to /home while running through the installer.

Before you tried the script, were you using the generic nv or ati driver for Xorg?

---

### Post by nomad00 on 2007-02-14
I have the same issue w/ both the 2.6.17-10 and 2.6.17-11 kernels....the odd bit is that if i boot from the 6.10 Live Cd, the networking works fine.  8139too is listed as well

---

### Post by pay on 2007-02-14
You have an ATI card. does the Envy script work with ATI cards aswell? I thought that it only installed nVidia drivers...

---

### Post by nomad00 on 2007-02-14
> I've learned to always keep a separate /home partition so that I can reinstall in case I muck things up. During the reinstall, you just choose to NOT format that partition and make sure it gets mounted to /home while running through the installer.

Thankfully, thats just what I did, but i didn't realize it was so easy to re-install w/o touching the /home partition --- thanks!

> Before you tried the script, were you using the generic nv or ati driver for Xorg?
Was using the Xorg one, i believe, whichever uses fglrx as the driver....:confused:

---

### Post by nomad00 on 2007-02-14
> You have an ATI card. does the Envy script work with ATI cards aswell? I thought that it only installed nVidia drivers...

Yup, a recent additon, check out [http://albertomilone.com/wordpress/?p=56]("http://albertomilone.com/wordpress/?p=56") for Envy 0.8.1 info

---

### Post by llamakc on 2007-02-14
> **nomad00 said:**
> Thankfully, thats just what I did, but i didn't realize it was so easy to re-install w/o touching the /home partition --- thanks!


Was using the Xorg one, i believe, whichever uses fglrx as the driver....:confused:

When reinstalling and you get to the part about partitioning, definitely choose "manually edit partition table," and be sure to write down which partition /home is mounted on now so that during the reinstall you can set it to mount at /home (and NOT format it).

As for the stock driver on an ATI card, it would be "ati" or "radeon" unless you installed the fglrx driver.

---

### Post by nomad00 on 2007-02-14
> As for the stock driver on an ATI card, it would be "ati" or "radeon" unless you installed the fglrx driver.

I had installed XGL & Beryl and in the process set up the fglrx driver.  Things weren't going so well, which is when I tried running Envy

---

### Post by llamakc on 2007-02-14
You can edit your /etc/X11/xorg.conf file to switch back to the ati driver.

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf-backup-with-fglrx

sudo nano /etc/X11/xorg.conf

and change the entry of "fglrx" to "ati". Restart the Xserver.

---

### Post by nomad00 on 2007-02-14
I did do that, and that got be back to a stable set up -- w/ the exception of my screensavers (and maybe other stuff i haven't found yet?) Which is what makes me think that maybe i've messed something else up in the process.

---

### Post by nomad00 on 2007-02-14
I'm going to attempt a reinstall and see how it goes --- thank you so much for your help!

---

### Post by pay on 2007-02-14
Before you do that. try ```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by drivel on 2007-02-14
On lauchpad.net,there is a post about this.

---

