---
title: "Long boot time"
date: 2007-05-30
forum: General Help
---

### Post by roncrump on 2007-05-30
Hi,

I have recently bought a new laptop (Dell XPS M1210) and set it up to dual boot (need Windows for some work stuff, unfortunately) with Feisty and Vista.

When booting Feisty it seems to take quite a long time. Watching the progress bar it pauses in one spot for what seems like an age (but is probably <<1 minute) before going on.

Anyway, is there any way of determining what step is causing the delay? Is there a log file in which I may see, for example, if there are multiple attempts to load something before moving on?

Thanks for your attention.

Ron.

---

### Post by confused57 on 2007-05-30
> **roncrump said:**
> Hi,

I have recently bought a new laptop (Dell XPS M1210) and set it up to dual boot (need Windows for some work stuff, unfortunately) with Feisty and Vista.

When booting Feisty it seems to take quite a long time. Watching the progress bar it pauses in one spot for what seems like an age (but is probably <<1 minute) before going on.

Anyway, is there any way of determining what step is causing the delay? Is there a log file in which I may see, for example, if there are multiple attempts to load something before moving on?

Thanks for your attention.

Ron.

You might try:
```
dmesg
```

---

### Post by jfinkels on 2007-05-30
> **roncrump said:**
> Hi,

I have recently bought a new laptop (Dell XPS M1210) and set it up to dual boot (need Windows for some work stuff, unfortunately) with Feisty and Vista.

When booting Feisty it seems to take quite a long time. Watching the progress bar it pauses in one spot for what seems like an age (but is probably <<1 minute) before going on.

Anyway, is there any way of determining what step is causing the delay? Is there a log file in which I may see, for example, if there are multiple attempts to load something before moving on?

Thanks for your attention.

Ron.

In addition to taking a look at dmesg, you can enable a more verbose output at the splash screen (during boot) like this.

Make a backup of your /boot/grub/menu.lst:
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup
```

Open your menu.lst like this:
```
gksudo gedit /boot/grub/menu.lst
```

Edit it so that the section that looks like this (it looks like this on my system, it will look slightly different on yours):
```

title           Ubuntu, kernel 2.6.20-16-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=2ba40e10-f6b5-4a52-a163-caf75cc99da7 ro quiet splash
initrd          /boot/initrd.img-2.6.20-16-generic
quiet
savedefault

```
looks like this (remove the word "quiet" from the line beginning with 'kernel'):
```

title           Ubuntu, kernel 2.6.20-16-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=2ba40e10-f6b5-4a52-a163-caf75cc99da7 ro splash
initrd          /boot/initrd.img-2.6.20-16-generic
quiet
savedefault

```

Save this and exit gedit. On your next reboot, you will see some extra messages describing the bootup processes more clearly. For even more fun info, you can get rid of "splash" on that line, also.

---

### Post by roncrump on 2007-05-30
Thanks for the suggestions, I will give them a try this evening.
Ron.

---

### Post by sandervdv on 2007-05-31
I have the same problem, and i discoverd that the slow progress is due to searching the network. If i disable my WiFi then my boottime is about 30 seconds faster.

---

### Post by AZzKikR on 2007-05-31
Usually, it's a networking issue. What you can also try, is booting into safe-mode. You'll see verbose output to your screen, so you can pinpoint where your problem lies. Starting your desktop can be done with executing
```
/etc/init.d/gdm start
```
afterwards.

---

