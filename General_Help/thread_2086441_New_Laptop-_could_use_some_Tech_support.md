---
title: "New Laptop- could use some Tech support"
date: 2012-11-20
forum: General Help
---

### Post by Prometheus418 on 2012-11-20
Hello-

my Dell Latitude D630 recently died due to the faulty NVidia chip, so I needed to purchase a new notebook.

This time, I opted for a Lenovo Thinkpad T400- not the cutting edge, but still a nice machine, and so far, it's running much cooler than the Dell ever did.

In the swapover, I did something that is probably not advisable, but it worked about 95%- I just took the SSD from the Dell, and plugged it into the Lenovo.  Actually, I'm pretty impressed- I'm typing this on the new notebook, and it more or less "just worked."

Here's the only caveat- there are occasionally graphical errors that pop up on the new machine.  I'm not going to blame this on ubuntu because I swapped a configured system into new hardware- I was actually surprised it even booted, much less operates as a functional system with wireless connectivity and most of the other bells and whistles.

So, with that pleasant surprise, I am now (perhaps unrealistically) hoping for some way to solve my graphical errors.  I am hoping that some of you guru-types have a superb bit of command-line wizardry that will allow me to rescan this system, drop the outdated drivers, and install the correct ones- sort of like I was installing a new system.

Here's what is going on-

I swapped from a system that had an Nvidia quadro 135m to one with an Intel gma4500.  This seems to be the only existing issue.  Not everything makes it hiccup- just a few random items, but when it fails, it fails big.  The major killer was when I tried to install fingerprint scanner support- which just killed everything until I removed it.

More minor, yet annoying, issues involve cairo-dock -o, which sometimes hangs after waking from suspension, and a much slower compiz spin (I have cube, rotate cube, reflection, 3d windows, and other pleasant looking stuff on there- I know I don't need it, but it sure is fun to look at) One little clue I got was that there may not be a driver on this system that supports openGL, but don't hold me to that.

So even though I've had Ubuntu for a while now, I'm still a n00b here.  Can anyone walk me through the process of rehab-ing this system in terms that an apologetic ex-windows user can follow?  I like the setup how it is, and don't want to go through hours of reinstalling everything if I can avoid it- If I have to do it, I will, and it won't count as a strike against Linux- Windows could not have done this either...  Though if Ubuntu can take a swap like this, it would go a long way towards convincing my engineering group that the open-source kung-fu is strong, and we should gently guide the folks with the checkbooks in that direction.

Any advice you can offer would be appreciated!  If there's no other choice, I'll suck it up and start from scratch- but it's so close that I hate to do that prematurely.

Thanks...

---

### Post by kclark on 2012-11-21
I'm sure there is a way to do this.  Maybe update all of the software with apt-get forcing it to reconfigure?  I did something similar a year or so back and got most everything working but it never operated like it should, I put a month or so into it before deciding that I'd be better off reinstalling the whole system.  No fun but it works much better.

---

### Post by carl4926 on 2012-11-21
The nvidia and intel graphics are different hardware.
The drivers for intel are in the kernel
Of course, there is a driver for nvidia there too, (as well you may have installed the proprietary driver), but no matter, as at boot the system will automatically probe and detect the intel chip and apply the correct driver.

By moving the HD (which is fine), but I guess is a challenge for the OS.

Have you tested a live cd/usb to see if that behaves well?

---

### Post by jocko on 2012-11-21
If you have the proprietary nvidia driver installed, you probably need to remove it and the xorg configuration file to allow xorg to load the correct driver.
These commands should do it:
```
sudo apt-get purge nvidia*
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

---

### Post by Prometheus418 on 2012-11-21
> **jocko said:**
> If you have the proprietary nvidia driver installed, you probably need to remove it and the xorg configuration file to allow xorg to load the correct driver.
These commands should do it:
```
sudo apt-get purge nvidia*
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

This seems to have worked, at least for the time being.  I'm going to mark this solved, and see how it runs for the next couple of days.  If it's acting up, I'll reinstall over the weekend.

Thanks!

---

