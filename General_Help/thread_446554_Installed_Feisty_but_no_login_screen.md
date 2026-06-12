---
title: "Installed Feisty but no login screen"
date: 2007-05-17
forum: General Help
---

### Post by erugalatha on 2007-05-17
Hi,

I finally got feisty installed on my laptop and it boots up fine with no errors until it gets to the part where the login screen is supposed to appear - the screen goes black and there's no response even though it looks like there still disk access ongoing.  There is no command prompt either.

Is it just the display manager cannot load or maybe there's a resolution problem?  I'm stumped on this one so can somebody point me in the right direction?

---

### Post by flowingfire on 2007-05-17
I had this problem a number of times, but I'm not sure if we have the same dilemma.  When I would boot up, I wouldn't get a command prompt or a login screen, but it would give me a cursor to type with on a big dark screen ... And it simply couldn't do anything.

Is this the issue you're having?

Because the problem was in xorg.conf and people showed me how to make sure that it's working... I'm a newbie and no expert, but somebody here with more experience in the matter could probably assist you in making sure that your display works correctly.

In the grub loader on startup, can you log into the recovery mode and get a terminal prompt?  If so, then you might be in business.  Then you can enter whatever modes are necessary to fix the display stuff.  Or you could directly edit xorg.conf with something like "sudo pico /etc/X11/xorg.conf" . . .

---

### Post by erugalatha on 2007-05-17
Hi,

Thanks a lot for replying.  We seem to have a similar problem but not exactly the same - I get a completely blank screen - no prompt, no nothing - but I can see disk access light flashing sometimes on the laptop.  I can't see what's happening onscreen though to know what's going on.

When I go into recovery mode I can get to a prompt but I can't install any updates because it doesn't detect my network cable ... so I'm offline.   I tried doing a sudo apt-get update and sudo apt-get dist-upgrade but it failed to connect to all the repos.

It's seems screwed to me ... any idea what I should do with xorg.conf?

---

### Post by zvacet on 2007-05-17
[http://www.psychocats.net/ubuntu/nox]("http://www.psychocats.net/ubuntu/nox")

---

### Post by erugalatha on 2007-05-17
Thanks for the link but I've had no luck with it -  still a blank/black screen.

I'm using an ATI Mobility Radeon X1400 if that's any help.

---

### Post by zvacet on 2007-05-17
```
  sudo dpkg-reconfigure xserver-xorg
```

select **vesa** just to get graphic and after that go for drivers for your graphic card.When you find them and install run above command again and select ati or radeon(I don´t know wich one cause i don´t use it).

---

### Post by erugalatha on 2007-05-18
ok so the vesa selection work and I could gain access to a graphical login.

I then downloaded the ATI drivers for linux but when I run:

sudo sh ./ati-driver-installer-8.36.5-x86.x86_64.run

The install does not complete as per the instructions here:

[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.36.5-inst.html](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.36.5-inst.html)

Is there any other way to get these drivers installed?

---

### Post by JoePits on 2007-06-01
yeah if you have vesa and ur ubuntu gui desktop working than you can use synaptic package manager to get the real ati drivers.  you dont need to do that file from ati's site.

---

