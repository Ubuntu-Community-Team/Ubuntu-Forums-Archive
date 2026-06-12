---
title: "How do you disable swap (when using LiveCD)?"
date: 2007-08-05
forum: General Help
---

### Post by LodeRunner on 2007-08-05
I was following [this]("https://wiki.ubuntu.com/BootToRAM") guide to create a responsive, customized, read-only Ubuntu install on a USB drive, when I came across this: "Ubuntu LiveCD scripts will mount any swap it finds."  Understandable, but (in this case) undesirable. I would like to ensure that my hard drives aren't touched at all.  I have plenty of RAM, so I'm not worried about performance. How would I go about disabling the auto-mount-swap scripts?

---

### Post by ityro on 2007-08-06
I am new to Linux but have had Swap problems. Does this look like it might help?

Swap Partition (reset)
sudo swapoff -a
sudo /sbin/mkswap /dev/hda5
sudo swapon -a 

Replace /hda5 with your swap, you probably just want the swapoff for now but will need the rest to reset/restore swap. 

Hope it helps, I don't think it can hurt or I would have done that.

---

### Post by LodeRunner on 2007-08-06
> **ityro said:**
> I am new to Linux but have had Swap problems. Does this look like it might help?

Swap Partition (reset)
sudo swapoff -a
sudo /sbin/mkswap /dev/hda5
sudo swapon -a 

Replace /hda5 with your swap, you probably just want the swapoff for now but will need the rest to reset/restore swap. 

Hope it helps, I don't think it can hurt or I would have done that.

Might work if I did that every time on startup, but I was really hoping someone knew which LiveCD scripts contained the auto-mount instructions, so I could simply comment them out.  Or... perhaps a little grep-ing is in order...

---

### Post by ityro on 2007-08-06
Way over my head. Best I can think of is to write a script that runs at start-up until you find what you are looking for. I can't do that either. Sorry I can't help and Best of Luck.

---

