---
title: "My copy of Lubuntu freezes entirely at random times."
date: 2015-12-22
forum: General Help
---

### Post by faxity on 2015-12-22
Lubuntu keeps freezing entirely on my Laptop. Whenever it freezes I can't do anything about it-- my cursor is locked, the keyboard wouldn't do anything and REISUB doesn't work.
Whenever this happens I'd have to hold the laptop's power button until it shuts down to restart it.

It seems to happen at random times; it doesn't seem to trigger when I do anything specific. It can happen from when I'm playing games to when I'm on Chrome to when I'm listening to music.
One time it froze only about 5 minutes after I log in Lubuntu. Another time, it took up to 5 hours for it to freeze.
This is a fresh install of Lubuntu. I have installed this on my laptop yesterday.

Here are some specs if it helps any:
--Acer Aspire E E5-511P-C9BM
--8GB Ram
--Intel Celeron Quad-core 1.83 GHz
--Intel HD Graphics

I am entirely new to Linux so I don't know how to check on Terminal what exactly is causing this problem. Is there anything I could do that might fix this?

Thanks.

---

### Post by matt_symes on 2015-12-22
Hi

This is a know bug and looks to be real pain to find as it seems to totally freeze the system. 

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1509723](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1509723)

The workaround looks to be to use kernel 4.1.12 or maybe 4.1.13 as they look to be working for people.

The other thing that may fix it is to add this parameter to your kernel command line.

```
intel_idle.max_cstate=1
```

So before we decide which solution to attempt, i need to know your current kernel version and grub command line. 

Open a terminal and type

```
uname -r
```

Post the output here and then post the output of this

```
cat /proc/cmdline
```

Kind regards

---

