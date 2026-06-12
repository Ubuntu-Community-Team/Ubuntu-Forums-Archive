---
title: "Unexpected Very Very Slow Boot"
date: 2007-07-11
forum: General Help
---

### Post by joels on 2007-07-11
Hi all,
I've seen a million "slow boot" posts, but I know nothing about what they're talking about. I'm a bit of a noob to linux, but I'm advanced enough with PCs.
I've got a AMD 1900+ processor, 768mb RAM and tons of hard disk space, so I'd expect Ubuntu to load up fairly quickly, from what I've heard others say.

It always freezes for a couple of minutes with the orange splash screen progress bar a couple of pixels across. I don't know how to see whats happening behind the splash screen either.

I've attatched a bootchart image of a bootup. I'm willing to have a tinker with any bootup files if someone shows me how.

---

### Post by mouseboyx on 2007-07-12
run in terminal

```
sudo nano /boot/grub/menu.lst
```remove splash so that it looks somewhat like~

title        Ubuntu
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.20-16-generic root=UUID=0d927b63-3d03-401e-beac-651282b5dc4d ro quiet
initrd        /boot/initrd.img-2.6.20-16-generic
quiet
savedefault

that will allow you to see what is behind the boot up screen.

---

### Post by joels on 2007-07-12
Thanks will do.

Edit: Okay, so it freezes for the majority of the time when it says
"...Loading, please wait..."
Then it goes on to say
"kinit: trying to resume from ..." lots of numbers and bits and pieces. Then,
"no resume image, doing normal boot". It does this fairly quickly, then the rest all moves quickly until the login screen.

So I'm guessing its something during the "loading" part thats getting stuck, or lagging behind. Or maybe it could be the kinit part, but thats not displaying during the holdup. hmmm? any suggestions?

---

