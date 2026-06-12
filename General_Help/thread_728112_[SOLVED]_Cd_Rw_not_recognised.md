---
title: "[SOLVED] Cd Rw not recognised"
date: 2008-03-18
forum: General Help
---

### Post by Rytron on 2008-03-18
Hi,
I had a cd rw that had an OS on it. I wanted to erase this and burn a different OS onto it. So I opened up K3B and choose burn image. I selected the iso image to burn and then a message came up that said I needed to erase the cd rw first. After the erase was finished the new OS was being burned onto the Cd rw. Shortly after the burn process began I realised that I actually wanted to burn a different OS. So I canceled the burn process. Then I wanted to erase the cd rw - however now the cd rw is not recognised. It just spins a few times in the cd drive.

Is there a terminal command / other method to force erase a cd rw to make it usable again?

Thanks.

---

### Post by olafbooij on 2008-03-21
Hi,

I used to do this with cdrecord. Something like:
```
cdrecord dev=b,t,l -v blank=all
```

The b,t,l should point to your device. Run:
```
cdrecord -scanbus
```
to find your specific device (for my dvd-recorder it's dev=0,0,0)

Greets,
Olaf

---

### Post by Rytron on 2008-06-09
No joy.
That cd rw was binned.

---

