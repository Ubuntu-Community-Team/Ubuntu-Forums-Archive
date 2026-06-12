---
title: "Ubuntu showing uncharacteristic slowness"
date: 2013-02-03
forum: General Help
---

### Post by ghost25 on 2013-02-03
Hey all, got a weird one for ya.

I'm running 10.04 Lucid Netbook with Gnome 2.30.2, kernel Linux 2.6.32-45-generic. Hardware is an HP Pavilion 760n running 512MB RAM on a P4 1.8GHz. Yes, I'm running Netbook, as I found it requires fewer resources than a full-fledged "desktop" version.

Without getting into too much detail right away, I've noticed it starting to lag when performing certain tasks. I can't share folders even with Samba, shared printing is hit-or-miss, and it'll randomly decide to stop working how it's supposed to. I'm not sure if it's due to excessive heat building up (shouldn't be, as I added another fan to it {but it's placed in an empty hard drive cage so IDK}), or if I screwed something up in etc/fstab, or in some other little-accessed but vital file. I try to stay out of sudo and root as much as I can, typically just using "sudo [command]" for whatever.

I've tried pinging some sites, and I'm getting normal response times in the 50-60ms range, however sites themselves are taking forever at times to load. Boot times are what I expect, however while the load to desktop is normal programs themselves lag out, sometimes to the point of becoming entirely unresponsive.

I'm really not sure what the problem is at this point, but I'm willing to try anything. I can clean up files pretty easily, and I'm not afraid of editing what one might think of as "registry" files. Let me know what lines and feedback from them you need, I'll get them posted as soon as I can.

Thanks for the help.

---

### Post by tgalati4 on 2013-02-03
Did you install a temperature monitor on your panel?  Most P4's have a temperature sensor.  If they get too hot, they will stop.

Open a terminal:

```
dmesg | tail -50
```

Open another terminal:
```
sudo apt-get install htop
htop
```

Look for stuck processes eating up CPU and I/O waits which may indicate hard disk problems.

Finally:

```
free
```

What is your RAM situation?

---

### Post by HermanAB on 2013-02-03
Blinking kompooter doing something you don't understand:
# tail -f /var/log/messages
# top
# ntop

---

