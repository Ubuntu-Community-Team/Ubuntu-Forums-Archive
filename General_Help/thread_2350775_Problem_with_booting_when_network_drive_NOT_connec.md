---
title: "Problem with booting when network drive NOT connected"
date: 2017-01-27
forum: General Help
---

### Post by Steve Francis on 2017-01-27
I have a laptop running Linux and Windows in a dual boot configuration.

I have configured the Linux boot up to automatically mount a network drive (nfs) on start up by adding a line to the/etc/fstab/ file. All works well.

However, when I take the laptop to another location (i.e. where the network drive is not physically connected), it takes an age to boot up. Eventually it does, but I have to wait over a minute. (Presumably it's spending this time looking for the network drive before giving up.0

Am I stuck with this? Ideally, at the boot menu, I would like options that say
1. Linux (ignore network drives at start up)
2. Linux
3. Windows

At the moment, the boot menu only gives me options 2 and 3 to choose from.

---

### Post by QIII on 2017-01-27
Hello!

Try adding 

```
nobootwait
``` to your options in the stanza that mounts the drive.

---

### Post by Steve Francis on 2017-01-27
Thanks for your suggestion.

I edited the line in /etc/fstab as follows

192.168.1.120:/volume1/share /home/steve/NAShome nfs nouser,rsize=8192,wsize=8192,atime,auto,rw,dev,exec,suid,**nobootwait** 0 0

The outcome was that it stopped mounting the network drive at boot up, even when it was physically connected to the network. :(

---

### Post by bearlake on 2017-01-27
> **Steve Francis said:**
> Thanks for your suggestion.

I edited the line in /etc/fstab as follows

192.168.1.120:/volume1/share /home/steve/NAShome nfs nouser,rsize=8192,wsize=8192,atime,auto,rw,dev,exec,suid,**nobootwait** 0 0

The outcome was that it stopped mounting the network drive at boot up, even when it was physically connected to the network. :(

Not sure which version of Ubuntu you are using, but came across this.

[http://askubuntu.com/questions/786928/ubuntu-16-04-fstab-fails-with-nobootwait](http://askubuntu.com/questions/786928/ubuntu-16-04-fstab-fails-with-nobootwait)

---

