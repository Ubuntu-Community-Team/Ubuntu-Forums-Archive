---
title: "What exactly is gvfsd-metadata"
date: 2013-11-06
forum: General Help
---

### Post by cyrilm2 on 2013-11-06
Hello,
I don't understand what exactly is gvfsd-metadata and why it's always writing on the disk?
Could somebody explain it to me?

Thanks

---

### Post by Dallco on 2013-11-23
I see gvfsd-metadata eating a lot of system resources and writing to my disk what is it?

---

### Post by Dallco on 2013-11-23
[http://ubuntuforums.org/showthread.php?t=1421580&page=2]("http://ubuntuforums.org/showthread.php?t=1421580&page=2") This old topic gives some solution

rm -rf ~/.local/share/gvfs-metadata

But why? that is the question.

---

### Post by grahammechanical on 2013-11-23
Gnome Virtual File system Daemon.

[http://superuser.com/questions/140865/gvfsd-takes-up-too-much-memory](http://superuser.com/questions/140865/gvfsd-takes-up-too-much-memory)

Synaptic Package Manager has this to say about gvfs

> gvfs is a userspace virtual filesystem where mounts run as separate
processes which you talk to via D-Bus. It also contains a gio module
that seamlessly adds gvfs support to all applications using the gio
API. It also supports exposing the gvfs mounts to non-gio applications
using fuse.


System Monitor>Processes tab tells me that there are several gvfs related processes in memory but at the moment they are using zero% CPU resources.  From that tab in system monitor we can kill off processes should we wish to.

Regards.

---

