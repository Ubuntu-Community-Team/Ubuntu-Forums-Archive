---
title: "Permissions on USB flash drive are messed up"
date: 2007-04-08
forum: General Help
---

### Post by bg1256 on 2007-04-08
This has been a problem for the past few months, and it all started when I installed KDE using apt-get.  I'm also using Kubuntu Edgy.

Somehow, my USB flash drive has become read only, and I can't seem to change the permissions.

Here is what I have tried:

```
$ sudo chmod -R 755 /media/JOHN\ SMITH/
```

(where JOHN SMITH is the name of the USB drive)

This command simply hangs every time, while it spikes my processor to 80%.  I've let it run for nearly an hour, with no luck -- and it's only a 512 MB flash drive, so it shouldn't take that long, I wouldn't think.

```
$ sudo chmod 755 /media/JOHN\ SMITH/
```
This does nothing.

I've also tried

```
chown myusername media/JOHN\ SMITH/
```

And that does nothing as well.

So, two questions:

Is there a command that would restore permissions?

Is there a command that would simply reformat this little drive?  There's no data on there that I don't have elsewhere...

Thanks for anyone who can help.

---

### Post by strabes on 2007-04-08
Do you know with what filesystem your usb stick is formatted? It's most likely ntfs, in which case you should install ntfs-3g so that you can read & write to ntfs filesystems:

sudo apt-get install ntfs-3g

Then try it. Hope this helps

---

### Post by bg1256 on 2007-04-08
I actually have that installed already, and it hasn't made a difference.

But I don't actually know how it is formatted.

---

