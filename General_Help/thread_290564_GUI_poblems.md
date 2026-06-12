---
title: "GUI poblems"
date: 2006-11-01
forum: General Help
---

### Post by c00w on 2006-11-01
When I try to load my gui it says that it cannot get my video device to work. It then syasy it cannot connect to xorg 00:01. I assume this is to get the driver. Anybody know where I can get the driver for a nviddia 5600+. I will post a more detailed message later.

---

### Post by taurus on 2006-11-01
Try to configure it again with

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by dro0g on 2006-11-01
I don't know if it's related to the updates that installed this morning, but I had a similar thing happen. I installed the updates this morning then suspended my laptop and went in to the office. When I got in, and brought it back up, I couldn't get an external USB mouse to work (touchpad still worked) so I rebooted. No more X.

I had to reduce the default color depth to 16 from 24 to get X to load. When it does, none of the pointing devices work (mouse, touchpad or nipple thing) Also when it loads it comes up with an error that the CPU doesn't support speedstep (it does) and none of the other gnome applets seem to work (the power ones don't show it plugged in and the battery one shows the battery as empty)

I just rebooted about a fifth time and used the i386 kernel rather than generic. and everything comes back normally. If I boot back to the generic, same thing - mouse doesn't work, etc.

So try changing the default color depth and see if you can get into X.

---

### Post by marcozs on 2006-11-01
> **c00w said:**
> When I try to load my gui it says that it cannot get my video device to work. It then syasy it cannot connect to xorg 00:01. I assume this is to get the driver. Anybody know where I can get the driver for a nviddia 5600+. I will post a more detailed message later.

What drivers do you use for the nvidia card, the standard nv or the nvdia?
Are you using any compiz/beryl?
Maybe you should post your xorg.conf

---

### Post by c00w on 2006-11-02
I used nv when i reconfigured my xorg.conf i am wonderiing which one i should use. so i should use Nvidia not nv?

---

### Post by c00w on 2006-11-02
also what is compiz/beryl

---

