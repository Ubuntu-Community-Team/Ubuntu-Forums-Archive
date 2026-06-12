---
title: "Running linux in linux"
date: 2008-05-03
forum: General Help
---

### Post by dmacdonald111 on 2008-05-03
I currently have the following setup on my machine;

hda1 - Linux base
hda2 - swap
hda3 - Linux running
hda4 - Home for hda3

What I would like to be able to do, is run hda1 using something like qemu in hda3 to save me rebooting all the time.

I know that with qemu, you select a img file, but is there a way that I can use the version installed on hda1 instead?

TIA

Daniel

---

### Post by scragar on 2008-05-03
[http://fabrice.bellard.free.fr/qemu/qemu-doc.html#SEC20](http://fabrice.bellard.free.fr/qemu/qemu-doc.html#SEC20)

You could add your HD fairly easily, and from there edit fstab to mount it as / - although there's then the problem of making sure it's always mounted...

---

### Post by dmacdonald111 on 2008-05-03
Thank you scragar. I did have a quick look through that document once before and I didn't even notice that part! Kewl :)

---

