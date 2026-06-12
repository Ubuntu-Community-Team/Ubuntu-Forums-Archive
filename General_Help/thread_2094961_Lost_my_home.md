---
title: "Lost my /home"
date: 2012-12-15
forum: General Help
---

### Post by risotto77 on 2012-12-15
Hi 

As title says I can not go into my /home. Computer leaves me out with a root terminal so I can try to fix this myself. OK. So I had my revodrive (raid kind of ssd thing) mounted at /home. 'mount' now says 'the device does not exist'(it used to show up as /dev/mapper/sel_*).

Now, what do I do?

---

### Post by risotto77 on 2012-12-15
I want to find out if the device is broken or the problem is in the Ubuntu setup. I have tried 'lspci', because the revodrive s pci connected, but cannot find any entries for 'revodrive'. I am not sure what to expect. Please help.

---

### Post by steeldriver on 2012-12-15
Can you see it with fdisk?

```
sudo fdisk -l
```

---

### Post by risotto77 on 2012-12-15
yes in a way. It shows as four separate disks instead of one raid-disk. So I have 60GB /dev/sdb, 60GB /dev/sdc, 60GB /dev/sdd, 60GB /dev/sde. Guess that is good in a way, but I need them to appear as one 240GB disk somehow?

---

### Post by steeldriver on 2012-12-15
well I don't know anything about that device but I imagine that if you can see the underlying disks then it's a 'fakeraid' and the actual assembly is done by dmraid

what variant/version of Ubuntu are you running? have you done any kernel upgrades that might have broken dmraid?

---

### Post by risotto77 on 2012-12-15
Computer has Ubuntu Gnome Remix 12.10. Kernel 3.5.0-19-generic. I did not pay very much attention on content of the updates yesterday. (edit: will look for fakeraid and dmraid stuff, thanks)

---

### Post by SuperFreak on 2012-12-15
I looked into Revo drives awhile ago and dismissed them for my Ubuntu computer because I got the impression they are incompatible with Linux (need Windows drivers). Perhaps this has changed since I looked but it might be worthwhile looking at the minimum requirements for your drive.

---

