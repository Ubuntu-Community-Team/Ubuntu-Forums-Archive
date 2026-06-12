---
title: "Stuck in Emergency mode"
date: 2019-08-18
forum: General Help
---

### Post by ytterbious on 2019-08-18
Every time I boot into Ubuntu now, I am greeted with "You are in Emergency Mode" with the messages:
```
couldnt get size
```
```
no caching mode page found
```
and
```
assuming drive cache: write-through
```

It has been like this for about a month, mostly due to frustration and not getting anywhere. I tried fsck to no avail, it didn't seem to do anything when I ran it, if I recall correctly. Not sure if it was user error or it just didn't need to be run. I want to say that I got stuck in error mode after my computer got unplugged while running, but it has been so long now I can't be completely certain. I did run a command, I want to say it was journalctl, and I got three red error messages. I can run it again and write down the exact messages if that would help.

*Side-bar: *Does anyone know how to the output from a message off of emergency mode or a virtual console, onto a flash drive (or other partition such as Windows) as .txt file for later reference?

---

### Post by freedombacon on 2019-08-19
You can get the output that's on the screen up to the emergency mode to a text file with this:

```
journalctl -xb > journal.txt
```

I don't know if USB will automount in emergency mode, but you should be able to do it manually.

This should show you the device name:
```
dmesg | tail
```

Make a directory to mount it, then mount it:
```
mkdir /mnt/usb
mount /dev/sdX /mnt/usb
```

---

### Post by ytterbious on 2019-08-21
Alright, here is the journalctl output: [https://paste.ubuntu.com/p/Gk5BwWhP9q/](https://paste.ubuntu.com/p/Gk5BwWhP9q/)


I can go back in and find which entries were in red, especially if that would help.

---

