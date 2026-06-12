---
title: "A question - screen resolution"
date: 2008-01-12
forum: General Help
---

### Post by wookietim on 2008-01-12
I am playing with the live CD of Ubuntu right now, trying to decide if I would like to install it on my desktop. There is something standing in the way however - Ubuntu thinks I can only have a screen resolution of 800X600.... On Windows I have a much higher resolution and I am not going to bother installing if Ubuntu will only go this big...

Is this one of those "Live CD" quirks that will be fixed by installing it to the HD, or is this a problem with Ubuntu - I am using a Dell Dimension C521, with a normal monitor and nVidia Riva 128 video card...

---

### Post by iris-n on 2008-01-12
Don't worry, it will be quick to fix when you install it on the HD.

The Live CD works with a basic hardware detection, and as the system isn't installed, you can't change the configurations.

---

### Post by wookietim on 2008-01-12
That's cool. Here's another question - how come when I try to install Ubuntu it only gives me the option of using the entire disk as it's partition? I REALLY don't want to sacrifice every piece of windows software I own, after all - I want to dual boot.... I looked at the help for installing Ubuntu from a live CD and it shows that the partitioner is supposed to show three options... Mine shows the last two, and doesn't allow me to set up a dual boot...

I have Windows Vista on the main drive (Which is the main reason I want to jump ship), so that may be a problem? I dislike Vista, but I do want to have the ability to go back to it if i need to...

---

### Post by iris-n on 2008-01-12
That's weird, it really should have these options.
Anyway, you could always partition manually.
Just go to the System->Administration->Partition Editor (gparted) in the live cd and do it!
Shrink your windows partition, create a small one (2x your RAM, as a rule of thumb) for your swap, and another to host your Linux.
This guide can help you:
[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)
Just remember to back it up!

---

### Post by Waldo2020 on 2008-01-12
obviously you don't know about the serious Nvidia (restricted) driver bug.
"nvidia" driver cannot read the EID forcing, in my case a low resolution of 640x480.
A google search shows dozens of people with this problem, so right now using "nv"
is the only option, forgoing acceleration. "nv" reads screen properties fine, it's just Nvidia's
closed driver that is buggy. Some people have had solutions by feeding it alternate EDIDs
or modelines - none of those worked for me.

---

### Post by iris-n on 2008-01-12
I'm sorry, i really haven't heard about it.
I have a nvidia geforce 6200 which is currently working fine with the restricted drivers.

---

