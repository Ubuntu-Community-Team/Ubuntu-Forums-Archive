---
title: "ATI Driver Success...partially..."
date: 2007-11-23
forum: General Help
---

### Post by Unicycle on 2007-11-23
ATI can go suck a lemon...just to put that out there...

Anyway, I was successful in the installation of the new ATI proprietary driver through Envy.  The first time it complained that my monitor was out of frequency, but I fixed that by changing Xorg.conf to only include my desired resolution (the maximum Envy entered was a resolution my monitor didn't support).

After rebooting, Ubuntu loaded, and everything seemed great.  That's further than I've gotten before, so w00t for that.  I even got 3000+ FPS on glxgears, but...there were no gears.  Just a black box.  This is surprising, because fglrxinfo told me all the right things.

I'm hoping someone will have a solution to this.  Oh, and hopefully it's simple.  I need simple right now... ;)

---

### Post by kshane on 2007-11-23
> **Unicycle said:**
> ATI can go suck a lemon...just to put that out there...

Anyway, I was successful in the installation of the new ATI proprietary driver through Envy.  The first time it complained that my monitor was out of frequency, but I fixed that by changing Xorg.conf to only include my desired resolution (the maximum Envy entered was a resolution my monitor didn't support).

After rebooting, Ubuntu loaded, and everything seemed great.  That's further than I've gotten before, so w00t for that.  I even got 3000+ FPS on glxgears, but...there were no gears.  Just a black box.  This is surprising, because fglrxinfo told me all the right things.

I'm hoping someone will have a solution to this.  Oh, and hopefully it's simple.  I need simple right now... ;)

You might try running This from the terminal:

```

aticonfig --initial

```

Kevin

---

### Post by Unicycle on 2007-11-23
> **kshane said:**
> You might try running This from the terminal:

```

aticonfig --initial

```

Kevin

No luck.

---

### Post by stunner on 2007-11-23
Do compiz or any 3d aps work?  Are you running xgl?

---

### Post by kshane on 2007-11-23
> **Unicycle said:**
> No luck.

Is anything working?

---

### Post by Unicycle on 2007-11-23
> **kshane said:**
> Is anything working?

Yes, everything but 3d.

I am not running XGL.  Maybe I should try it.  How would I do that?

---

### Post by stunner on 2007-11-23
```
sudo apt-get install xserver-xgl
```

---

### Post by enchance on 2007-11-23
Hi, fellow ATI user. I 100% agree with you that ATI sucks. Also, since you're using Envy to install your drivers as do I, try not to use the new driver which is **8.42.3**. Even if it does support AIGLX, that driver slows everything down considerably. To put it into perspective (after several tries), you'll have more success running **Install the ATI driver Manually** and selecting **8.40.4** and installing XGL than running AIGLX w/o XGL.

Once you've installed that driver, restart then install XGL like so
```
$ sudo apt-get install xserver-xgl
```
then reboot.

It's ok if you installed compiz before installing XGL. Ubuntu won't mind. Also, I've tested this on Gutsy as well as on Linux Mint 4.0 Daryna and it works like a charm.

---

### Post by macabro22 on 2007-11-23
What about the new Catalyst 7.11 driver? Is that one working alright?

---

### Post by tiachopvutru on 2007-11-24
Yea, the latest driver, 7.11 Catalyst is pretty easy to install.... Just type

```
sudo sh whatever_the_driver_name_is
```

Then follow the GUI instruction...

I'm happy with it. The performance is better since I don't have XGL to eat my CPU, but it's worse when Compiz is on.

---

### Post by macabro22 on 2007-11-24
Is the slow firefox scrolling issue fixed?

It was reported to be borderline useless with the 8.42 drivers

---

### Post by tiachopvutru on 2007-11-24
> **macabro22 said:**
> Is the slow firefox scrolling issue fixed?

Nope, it isn't. But it only happen when Compiz is on, I think. Well, at least for me, it's like that.

---

### Post by macabro22 on 2007-11-25
that sux.

---

