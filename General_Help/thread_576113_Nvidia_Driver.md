---
title: "Nvidia Driver"
date: 2007-10-14
forum: General Help
---

### Post by papuccino1 on 2007-10-14
I was wondering of anyone could tell me how to install my driver.
As you may notice im new to the hole Linux stuff.

I really need this fast, i would appriciate this a lot.

Nvidia GeForce FX 5500.

Yours,
Papuccino1.

---

### Post by conehead77 on 2007-10-14
you can try to go to
system -> administration -> restricted drivers

and then activate the restricted nvidea driver. Im not a nvidea user and do not know if it works with your card, but id say its worth a try.
edit: I use ATI and had to do the same though

---

### Post by papuccino1 on 2007-10-15
It worked.
Thanks mate, it really helped me here.
I think i'll use Linux from now on. :)

---

### Post by FredB on 2007-10-15
Linux is really simpler than it was a few year ago. I remember killing X, and get my computer to build official driver before being able to use fully my nvidia card.

---

### Post by papuccino1 on 2007-10-15
I have another questions. It might be a newbie one but anyways i really need to know this.
I wanted to play a OT (Open Tibia Server) i need a Ip Changer.
And there is a tutorial on how to make one work but i don't understand anything.

[http://otfans.net/showthread.php?t=56486](http://otfans.net/showthread.php?t=56486)

I would seriously appreciate if anyone could explain to me step by step on what to do.
Thanks in advance.

PS: I need to know how to make the 8.0 version work. Thanks mates.

Yours,
Papuccino1.

---

### Post by isecore on 2007-10-15
> **FredB said:**
> Linux is really simpler than it was a few year ago. I remember killing X, and get my computer to build official driver before being able to use fully my nvidia card.

Ah yes, good times... Many fond memories of burning the midnight oil waiting for a kernel-module to compile and then finding that I was missing some critical dependency.

Err, wait... maybe they weren't THAT good after all...

---

### Post by rockprincess on 2007-10-16
i haven't used feisty before (I'm still on edgy)

a friend told me though that he did the exact same thing, namely:
system -> administration -> restricted drivers

the next time he booted his computer, the xserver couldn't be started because something was wrong with the xorg conf
he then had to change "nvidia" to "nv" in the xorg conf.

is this normal, or did my friend just screw his machine by installing a wrong nvidia driver?

---

### Post by isecore on 2007-10-17
> **rockprincess said:**
> i haven't used feisty before (I'm still on edgy)

a friend told me though that he did the exact same thing, namely:
system -> administration -> restricted drivers

the next time he booted his computer, the xserver couldn't be started because something was wrong with the xorg conf
he then had to change "nvidia" to "nv" in the xorg conf.

is this normal, or did my friend just screw his machine by installing a wrong nvidia driver?

No, not really. What probably happened was that the Nvidia kernel-module didn't get loaded. It happens sometime. Doing a 
```
sudo modprobe nvidia
```
in a terminal window should do the trick, hopefully. If it doesn't, then the proper kernel-module hasn't been installed and you should probably go hunt for it in synaptic. It's most likely named "linux-restricted-modules-NUMBERSINDICATINGYOURKERNELVERSION" or similar.

---

### Post by rockprincess on 2007-10-17
cheers, i'll pass that information onto my friend!

i'm learning something new each day! 

thank you mucho for your reply! :)

---

