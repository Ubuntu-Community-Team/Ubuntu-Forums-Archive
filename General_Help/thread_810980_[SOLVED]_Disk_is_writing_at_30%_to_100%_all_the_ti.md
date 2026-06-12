---
title: "[SOLVED] Disk is writing at 30% to 100% all the time(not firefox)"
date: 2008-05-28
forum: General Help
---

### Post by secondstage on 2008-05-28
According to the System Monitor Applet in the top tool bar, my system is writing to the hard drive at about 30% to 90%, all the time. I have removed firefox 3 b5, for firefox 2, and that didn't do anything. I have tried epiphany, and that didn't do anything. It doesn't seem to affect speed, but I'd really like to know what it is. 

It's a SATA drive formatted to ext3.

Thanks in advance

---

### Post by sdennie on 2008-05-28
You could see what's causing the writes by doing:

```

sudo sh -c "echo 1 > /proc/sys/vm/block_dump"

```

Wait for a few seconds and then type:

```

dmesg

```

Then, after you've figured out what's going on, turn off the block dump with:

```

sudo sh -c "echo 0 > /proc/sys/vm/block_dump"

```

---

### Post by secondstage on 2008-05-28
It is mostly kjournald and mythtvbackend. I don't ude MythTV anymore, so I'm just going to remove it. But why is kjournald using so much of my drive?

---

### Post by sdennie on 2008-05-28
The ext3 journal defualts to a 5 second commit time.  It's normal to see that show up frequently.

---

### Post by secondstage on 2008-05-28
When you say frequently, could that be considered all of the time?


I just noticed that when I open Synaptic, or apt-get, the levels of usage drop to about 5%. Is this so that apt-get will have as much bandwidth as it might need?

I just removed MythTV, and the usage has dropped to zero. Sorry that I wasted your time.

---

### Post by sdennie on 2008-05-28
Seeing kjournald come up every 5 seconds wouldn't be uncommon.  It's not something to really worry about though.  If you find it exceedingly annoying for some reason, you could change it with:

```

sudo mount -o remount,commit=60 /

```

That will change it to only write every 60 seconds.  That change isn't permanent though and you'd have to add the commit=60 to /etc/fstab.

---

### Post by secondstage on 2008-05-29
And I thought that I knew a lot about how Ubuntu works

Thanks for the help!

---

