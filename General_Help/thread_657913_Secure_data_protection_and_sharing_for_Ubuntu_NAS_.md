---
title: "Secure data protection and sharing for Ubuntu NAS device?"
date: 2008-01-04
forum: General Help
---

### Post by njparton on 2008-01-04
Hi all, I'm looking for some advice for my particular situation - I can't quite decide which route to take.

I run my ubuntu box as a headless NAS device. It works brilliantly and it serves shares to Windows clients via samba and my ubuntu desktop via NFS over my 

gigabit LAN nicely.

It contains a large RAID 1 array via a 3ware card which is partitioned into 2 roughly equal ext3 partitions. One partition holds day to day data such as 

music shares, video etc etc.  The second partition holds more sensitive data such as financial info, personal photos, letters etc.

I'd like to encrypt the 2nd partition to protect against both unathorised access and physical removal (theft) of the device. This partition is currently set 

up in samba to only share to one specific username to one specific client IP address. The mount is also owned by the same user and group and other permissions have been removed. That should protect against casual unauthorised access in the short term (?) but I'd like to go further.

I've done some research on encrypting partitions and/or using truecrypt (which I use in windows).  However, as the NAS is headless I don't have access to it during boot up so I can't enter any passwords etc at that stage (as auto mounting an encrypted ext3 partition via fstab would require).

The NAS device runs during the daytime and is usually shutdown overnight to save power (thinking green here). I administer it via ssh (or VNC via xming/vino if I need the GUI).

I'd like to avoid having to log into the NAS each time the partition needs mounting following a shutdown, so if scripts are needed, a way of executing them from windows would be advantageous.

All my computers are connected via a gigabit switch, which is in turn connected to a 10/100 wired router to the internet.

Is there a way I can set the 2nd partition up to ask for a username and password in Windows each time someone tries to access it, but if it was stolen then the data would be protected via encryption? 

Many thanks up front for any advice.

---

### Post by kidders on 2008-01-05
Hi there,

Most of the time, when I encrypt filesystems, I put the keys on an external device of some kind (eg a small USB device, an 8cm CD, etc.) and tweak the boot-up scripts so Linux tries to find them, or fails silently in the event the keys aren't available. That way, as well as preserving a non-interactive boot process, there is scope for using very complex keys.

That much protects private data while the computer storing it is turned off. (Encryption doesn't protect against anything else.) While it's in use, you have to rely on your Linux box's ability to resist unauthorised access, to keep it safe.

In my opinion, simple solutions are often the best choices. My recommendation would be not to remotely share the encrypted data at all, to be honest. If you can't trust your network environment (which seems to be the case), I suggest configuring your Linux box so it's impossible to access your encrypted files from a remote location, forcing your users to SSH into your box & tunnel a Samba/NFS/etc. connection over SSH. That way ...[LIST]
[*]You get to write reassuring-looking things into your config files, by disallowing all access except to 127.0.0.1.
[*]At the cost of a performance hit, you get heavy encryption on all connections, even when you're using protocols that don't support good encryption.
[*]You get a single point of control (ie your SSH server) from which you can manage and monitor access to your personal stuff.
[*]Also, the solution would be universal ... it should work with all file sharing protocols and all client OSs, so if you change the way you do something in the future, you won't need to worry about security.[/LIST]The normal routine for accessing services over a tunnel goes something like this...[LIST=1]
[*]Let's say you're using a Windows box, and you want access to the secure Samba share. You might run puTTY.
[*]You would log into your Linux box & bind port 139 on a network interface local to the client to port 139 on the server's loopback interface.
[*]Start -> Run -> \\local.ip.addr.here\sharename should then give you access to your private data, over a secure connection, so no authentication information, etc. gets broadcast for everyone to see.[/LIST]Anyhow, that's a pretty standard way of safely giving remote access to sensitive data. It should also work quite well over the internet, so you could access your data from work, for instance, as though it were stored locally on the client machine.

I hope that helps a little. It isn't quite the direction you seem to prefer, but out of all the possible approaches, it's what I would probably do in your position, so I thought I'd give it a shot.

---

### Post by njparton on 2008-01-05
Many thanks for your detailed reply.  I'll give it another read over tommorrow when I'm in the right frame of mind to take in the detail (I've been plumbing all day...) :)

---

