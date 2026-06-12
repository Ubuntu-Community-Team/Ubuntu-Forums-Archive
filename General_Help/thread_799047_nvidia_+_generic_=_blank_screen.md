---
title: "nvidia + generic = blank screen"
date: 2008-05-18
forum: General Help
---

### Post by ghira on 2008-05-18
I have a Lenovo N100.

I just upgraded from Dapper, and thought all was well until I noticed
that dmesg said I only had one CPU. grub has defaulted to the 386
kernel. (I had 686 before). I'd said "yes" to an invitation
to install nvidia drivers. (In dapper i always installed them by hand)

I reboot in generic kernel and just get a black screen. I'm assuming
generic is what I "ought" to use - I've seen references to it being
the way to make both my cores work.

I have seen various messages about nvidia on the forums, but I'm
not sure I've seen my particular combo of difficulties.

---

### Post by ghira on 2008-05-18
ok, after more searching I have found refs to this problem elsewhere. hmm.

I'm assuming generic is the kernel i really want to use.

---

### Post by ghira on 2008-05-21
OK, this seems odd. I can't boot in generic, but if I boot
in generic in recovery mode, then do "telinit 3", all is well.

So the nvidia drivers are basically ok with the generic kernel,
but something else is going wrong if I boot in generic directly?

Um.

---

### Post by danwood76 on 2008-05-21
I smell compiz or something else killing it.

Currently the only kernels available are generic or i386 for the standard desktop.
I doubt theres much in it to be honest, one is compiled with 686 compatibility and one with 386 but they are virtually the same anyhoo.

In recovery mode switch back to the nv driver like so:

First boot into recovery mode.

Second open up xorg.conf for editing.
```

nano /etc/X11/xorg.conf

```
(you could do this from the GUI by using gedit if you launch X in recovery mode)

Then find the line that says nvidia and replace it with just nv then reboot.
that should give you a straight boot, if you black screen again press ctrl+alt+F1, login to the CLI and run this to see whats killed X:
```

cat /var/log/Xorg.0.log | grep '(EE)'

```
and post it here.

---

### Post by ghira on 2008-05-21
There is one important difference: if I boot the 386 kernel,
only one of my cores runs.

For now I'll leave my working generic two core system running
thanks to the recovery + telinit 3 thing but next time I reboot
I'll do as you suggest.

---

