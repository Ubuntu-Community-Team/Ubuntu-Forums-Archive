---
title: "Hot GRUB Mess"
date: 2014-01-12
forum: General Help
---

### Post by karasuman on 2014-01-12
I really hope that someone can help me, because I have one desktop which I can't boot and only this old netbook to figure out why.

I have Windows 7 and some flavor of Ubuntu on the desktop, but I boot immediately to a "grub rescue" prompt.

The sticky I have next to the power switch seems to have been intended to include a clear set of instructions:

```
ls
ls(hd0,X)
setroot=(hd0,X)
setprefix=(hd0,X)/boot/grub
insmod normal
```

"X" is supposed to be a partition.  I recall that I should be using the latest letter, but that didn't work, so I tried with the next two, and still no dice.  When I made this post-it neveral months ago, I clearly thought that these were clear and explicit instructions as to how to get up and running again.  But they don't work.  So, help?

And, once I do get back in business, how can I fix grub to give me the usual list of options for which OS you intend to load?

---

### Post by deadflowr on 2014-01-12
> [COLOR=#000000]X" is supposed to be a partition. I recall that I should be using the latest letter[/COLOR]

Shouldn't that be a number?
Normally, it should look like (hd0,1) for the the first drive's first partition, and (hd0,2) for the next and so on.

But if you happen to have a livecd laying around somewhere you might try a quick [boot repair]("https://help.ubuntu.com/community/Boot-Repair")

---

