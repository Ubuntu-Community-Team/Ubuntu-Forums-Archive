---
title: "swap problem"
date: 2008-04-24
forum: General Help
---

### Post by akahige on 2008-04-24
In the last several weeks, I've noticed an odd problem with my swap partition: it fills slowly up, and will not reduce in size even when all open applications are closed.

I've got 2 GB of RAM, and the memory usage never gets over 50%, so I'm not sure why the swap is getting hit at all. It all seemed to start with a recent Firefox upgrade (or so I thought), but closing Firefox (which is pretty much always running) doesn't eliminate the high swap usage.

Is there a way of tracing what's causing this? And is there a way to purge the swap usage without having to resort to a reboot?

Here's the current usage:
```
$ swapon -s
Filename                                Type            Size    Used    Priority
/dev/sda3                               partition       2096472 930524  -1

```

---

### Post by forestpixie on 2008-04-24
You can use top to find what is using swap - run it in a terminal and once it's running - using f will give a new screen through which you can specify a new column - use p to get a swap column and then any key to return to the screen.

You can use swapoff and swapon to turn swap of and on :) 

```
sudo swapoff -a
sudo swapon -a
```

_Edit_ - to change sort order in top so that it sorts by swap - uppercase f then change to swap with p and then any key to enter again. Top should now show processes sorted by swap with a column for swap. Thanks for the question - didn't know any of that before I started :)

---

### Post by mali2297 on 2008-04-24
As I understand it, used swap won't be released until some other application needs it. This is working as designed, although you can manually empty swap by issuing
```

sudo swapoff -a
sudo swapon -a

```

But it is still strange that the swap is used in the first place...
Do you experience any negative effects like slow response?

---

### Post by akahige on 2008-04-24
> **mali2297 said:**
> But it is still strange that the swap is used in the first place...
Do you experience any negative effects like slow response?

Yes. Things get jittery when more than 50% of the swap is chewed up.

In top, the breakdown for swap usage seems to be roughly:
600 MB Firefox
340 MB Xorg
1 GB VMware
430 MB VMware vmx
106 MB XFCE

...which is all kind of odd since that looks like well over 50% of the available swap space...


In trying the swapoff and on commands, it didn't really seem to empty the swap (if it's supposed to have the same effect as a reboot). It spiked the swap to 100%, sent the RAM to about 60%, froze the whole system, and then settled down to about 60% swap usage. Turning swap back on dropped the memory usage to about 30%, and the swap to about 50%.

That wasn't really what I expected to see. Does it make sense to you?

---

### Post by mali2297 on 2008-04-25
For what do you use VMware?

I know nothing about virtualization, but can it be related to your problem?

---

### Post by dcstar on 2008-04-25
> **mali2297 said:**
> For what do you use VMware?

I know nothing about virtualization, but can it be related to your problem?

VMware Server has Host-Settings-Memory which can be change swap use.

---

### Post by akahige on 2008-04-25
> **dcstar said:**
> VMware Server has Host-Settings-Memory which can be change swap use.

That gave me an idea... I recently updated VMware (Workstation 6), and while I didn't have issues with the previous version, this one seems to need some attending to. I played with the swap settings (basically eliminating the swap usage and keeping everything in RAM), and so far that seems to be working well.

I wasn't surprised to see that not only does Firefox love to eat memory, but also swap. From everything that I've read, v3 has substantially better memory handling than v2 (which I'm running here). Does this also apply to the swap usage, or just RAM?

---

