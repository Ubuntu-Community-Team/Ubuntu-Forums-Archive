---
title: "Nouveau drivers and Nvidia drivers..."
date: 2013-07-19
forum: General Help
---

### Post by aimlessnat on 2013-07-19
Is it possible to have both the Nouveau drivers and Nvidia drivers both installed, but just use the Nouveau drivers?

I'm running 13.04 and the Nvidia drivers seem to cause a few issues (black screen and beep when logging out etc.) but the general performance is still much better than the Nouveau driver. It's easy enough to switch back to the Nouveau driver, but in doing this the Nvidia drivers seem to get removed? I would like to be able to just switch between the drivers without having to reinstall each time.

Any help/ideas? :confused:

---

### Post by Claus7 on 2013-07-19
Hello,

my experience is that this is not possible (usually two drivers for the same card are conflicting with each other). 
Maybe two different partitions with the same home folder? One with nvidia and the other with nouveau.
This is what I can think of.

Regards!

---

### Post by Bashing-om on 2013-07-19
aimlessnat; Hi !

It Might be possible if you want to learn how to set up Xorg.conf files for the desired driver. 
Heavy duty thread that might give you some ideas:
[thread]1743535[/thread]

[INDENT][INDENT]hey, it is a thought[/INDENT][/INDENT]

---

### Post by deadflowr on 2013-07-20
Both drivers installed?
Or both drivers running?

Most people who install the nvidia drivers still have the nouveau drivers installed.
It's just that when the nvidia drivers get installed, the nouveau drivers get blacklisted.

---

### Post by aimlessnat on 2013-07-20
Hey guys, thanks heaps for your replies. 

@Bashing-on
Cheers, I'll look into this!

@deadflowr
I just want both drivers installed. I understand the issues with having two drivers running simultaneously. It seems that after installing the Nvidia drivers and then switching back to the nouveau driver, the Nvidia drivers are removed in the process. Is this just me?

---

### Post by deadflowr on 2013-07-20
How are you switching back to the nouveau drivers?

---

### Post by aimlessnat on 2013-07-20
In Additional Drivers under Software & Updates, it listed all the available Nvidia drivers plus the Nouveau driver. I just selected the nouveau driver and applied changes. Boom, Nvidia drivers gone.

---

