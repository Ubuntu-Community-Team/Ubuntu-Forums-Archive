---
title: "[SOLVED] NFS auto-umount?"
date: 2007-11-14
forum: General Help
---

### Post by ofb on 2007-11-14
When the sharing machine is shut off, Nautilus & Konqueror are jammed, and running 'umount' to dislodge the vanished share won't work -- I have to reboot.

Since NFS is older than many of its users, and network connections were traditionally sporadic, surely by now there's a trick or two for gracefully unmounting a vanished share. Anyone happen to know what it is?

---

### Post by ofb on 2007-11-14
This isn't good:

```
o@redfish:~$ sudo umount.nfs /home/o/files/nfs
umount.nfs: Server failed to unmount '192.168.0.2:/home/o/files/downloads'
o@redfish:~$ sudo umount.nfs /home/o/files/nfs -f
umount.nfs: Server failed to unmount '192.168.0.2:/home/o/files/downloads'
umount2: Device or resource busy
```

The '-f' option is meant to "Force unmount the file system in case of unreachable NFS system."

---

### Post by ofb on 2007-11-15
Reading too much.

From the [Linux NFS-HOWTO]("http://nfs.sourceforge.net/nfs-howto/")

> 4.3.1. Soft versus Hard Mounting

There are some options you should consider adding at once. They govern the way the NFS client handles a server crash or network outage. One of the cool things about NFS is that it can handle this gracefully. If you set up the clients right. There are two distinct failure modes: 
...
hard
The program accessing a file on a NFS mounted file system will hang when the server crashes. The process cannot be interrupted or killed (except by a "sure kill") unless you also specify intr. When the NFS server is back online the program will continue undisturbed from where it was. We recommend using hard,intr on all NFS mounted file systems.

From man mount,
> intr 
This will allow NFS operations (on hard mounts) to be interrupted while waiting for a response from the server.

From man nfs
> hard 
If an NFS file operation has a major timeout then report "server not responding" on the console and continue retrying indefinitely. This is the default. 
intr 
If an NFS file operation has a major timeout and it is hard mounted, then allow signals to interupt the file operation and cause it to return EINTR to the calling program. The default is to not allow file operations to be interrupted.

Modify fstab to,
```
192.168.0.2:/home/o/files/downloads /home/o/files/nfs nfs hard,intr
```

Result,
```

o@redfish:~$ sudo umount.nfs /home/o/files/nfs -f
umount.nfs: Server failed to unmount '192.168.0.2:/home/o/files/downloads'
```

The line 'umount2: Device or resource busy' is now gone, and although the return says it failed to unmount, Konqueror is no longer jammed.

---

### Post by ofb on 2007-11-15
Thinking about this:
```
o@redfish:~$ sudo umount.nfs /home/o/files/nfs -f
umount.nfs: Server failed to unmount '192.168.0.2:/home/o/files/downloads'
```

I expect it fails to unmount because it cannot override fstab.

You could add 'noauto', but that gets you nowhere, as the fstab entry is made entirely useless -- the share will not be mounted on boot, and cannot be mounted with a simple 'sudo mount -a'. The share could only be mounted with an independent and tedious 'sudo mount 192.168.0.2:/home/o/files/downloads /home/o/files/nfs hard,intr'

So, anyway, add the 'hard,intr' to your NFS fstab entry so you can clear your machine with 'umount.nfs [mountpoint] -f' in the event of inevitable connection loss.

Hopefully someday soon NFS will be brought out of the Dark Ages and all of this will be handled in the background.

---

### Post by morticul on 2008-02-29
I have exactly the same problem. I was all excited to go put hard,intr in my fstab, to realize that it was already there...

This means, this wasn't the solution. My nfs was interrupted through a suspend session maybe this is too hard to recover :S

---

