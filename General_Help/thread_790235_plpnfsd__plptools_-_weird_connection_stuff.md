---
title: "plpnfsd / plptools - weird connection stuff"
date: 2008-05-11
forum: General Help
---

### Post by Krank on 2008-05-11
I own a Psion 5mx, which I use for more or less everything. I'd very much like to be able to connect it to my Ubuntu workstation and copy files between the machines, preferrably with as little hassle as possible.

First, I tried [Java Psion Link](http://website.lineone.net/~john.montgomery/psionlink/index.html). Couldn't get the dependencies working, so I began looking round for other solutions.

PLPtools seemed to be able to do what I wanted.

Howerver, there seems to be some kind of inconsistency here... 

1. NCPD is successfully started through the /etc/init.d/plptools command.
2. PLPFTP works great - I can access all of the Psion's files through the FTP-like commandline. It's hardly simple nor efficient, though. I could write a Python wrapper around it, of course, but I'd rather not.
...and here comes the strange part...
3. PLPNFSD doesn't work.

It doens't give eny error mssages, even using three -v to increase verbosity, and even using -D for debug mode.

All I get is:
```

krank@frustration:/media/psion$ plpnfsd -v -v -v
Owner set to krank.krank
plpnfsd: version 0.18, mounting on /var/lib/plptools/mnt ...
krank@frustration:/media/psion$

```

/var/lib/plptools/mnt exists.
/var/lib/plptools/mnt is empty. Bot before the operation and after.

Nothing seems to be mounted, and yet I get no error messages, no warnigns, no nothing.

I've tried using sudo (makes the program hang, no other discernable effect. Still no errors nor warnings).

I've tried using a different directory (/media/psion), to no effect.

Honestly, I'm at my wit's end here. Any ideas?

---

### Post by imagia on 2008-08-19
I'm trying to connect to a Psion series 5 too but not getting very far with plptools.

I'm using an FT232 USB-serial adapter that shows up in the output of lsusb and is already supported by the kernel now, so no need for drivers. Running plpftp just tells me no psion is connected. Where am I going wrong here??

---

