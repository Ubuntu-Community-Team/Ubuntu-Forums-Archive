---
title: "Run a script with root privileges after login"
date: 2022-05-18
forum: General Help
---

### Post by SeijiSensei on 2022-05-18
I would like to run a simple script to mount all my NFS shares upon logging in which requires root privileges. There are methods for running custom scripts at boot (via rc.local or systemd), but since Ubuntu doesn't bring up the network until after someone logs in, those methods won't work in this case. I can, of course, run the script manually with sudo, but I'm more interested in an automatic solution that runs upon logging in.  I searched Google for answers to this problem to no avail. Maybe it's just not possible?

---

### Post by TheFu on 2022-05-18
Would autofs not work? It isn't post-login, but it mounts stuff automatically on use and dismounts when all the files for the mount are closed.

My  [COLOR="#008000"]/etc/auto.nfs[/COLOR] file on the client looks like this:
```
/d/D1 -fstype=nfs,nconnect=2,proto=tcp,rw,async  istar:/d/D1
/d/D2 -fstype=nfs,nconnect=2,proto=tcp,rw,async  istar:/d/D2
/d/D3 -fstype=nfs,nconnect=2,proto=tcp,rw,async  istar:/d/D3
/VMs  -fstype=nfs,nconnect=2,proto=tcp,rw,async  romulus:/raid/media/VMs
```
The nfs-server is unchanged.

The /etc/auto.master contains this line:
```
/-      [COLOR="#008000"]/etc/auto.nfs[/COLOR] --timeout=60 --ghost
```

Restart autofs, Bob's your uncle.

Not exactly what you want, for that, you could modify your sudoers file (or sudoers.d/ ) to make the exact mount commands you'd like run, not need a the sudoer's password entered.  sudoers can allow specific users (or groups) to run a specific command or specific command with exact options, without any password entered. The Examples section of the sudoers file has that covered.  

And for lurkers, sudo isn't just to become root. Any userid can be switched into with it, if the permissions allow it. I've used the sudoers to allow our admin group access to different server deployment accounts on different machines. A single file, with machine specific settings, shared across 100 servers to be able to print to 3300 network printers in the enterprise.  We only allowed 1 exact command, with files to be printed as the option only option. The command was slightly different on each server, since they all didn't have access to print to the same printers using the specific software. I'm not explaining it well - doesn't matter.  hostname, username, groupname, command, command options and RunAs user can all be configured in extremely specific ways in the sudoers files.

---

### Post by SeijiSensei on 2022-05-19
I've had mixed success with automounting.

The real issue is how Ubuntu doesn't start the network until a user logs in. This makes sense for laptops with wifi, not so much for desktop machines on a wired network. There are probably ways around that, but I was trying for a simple solution first.

---

### Post by TheFu on 2022-05-19
I use autofs on my laptop.  I just need to be careful to close all files on the NFS storage before disconnecting from the wired ethernet.  I haven't had issues with sleeping nightly. It reconnects cleanly the next day, provided the network is connected where it was.  My laptops all have static IPs on known networks. 

For unknown networks, my brain is in a different mode and I don't attempt to access any NFS storage.

The only time I've had issues with autofs ... is with USB devices, not NFS.  Also, automounting often is confused to mean something similar, but not at all like autofs.

---

