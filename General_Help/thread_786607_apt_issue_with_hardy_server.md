---
title: "apt issue with hardy server"
date: 2008-05-08
forum: General Help
---

### Post by trmentry on 2008-05-08
I installed Hardy server.  Once it was up I did the following:

```

apt-get install ubuntu-desktop konsole wireshark tshark likewise-open likewise-open-gui

```

it said it had something like 890 packages to download.  When I left work it was still downloading.

When I got back this morning I have the following on my screen.

> 
W: No using locking for read only lock file /var/lib/dpkg/lock
E: Unable to write to /var/cache/apt/
E: The package lists or status file could not be parsed or opened.


Thought maybe my drive was full.  But no.  Its not even close.  still have 10g free on the VM.  (This is a VM I'm installing on ESX server.)

when I try and kick it off again, I get the same errors.

I'm guessing I can remove the lock file, but wanted to see if others had any other ideas.

thanks

---

### Post by trmentry on 2008-05-08
hrmm... the plot thickens.

```

root@server:/var/lib/dpkg# rm lock
rm: cannot remove 'lock': Read-only file system

```

Now that is odd, as we just left the vm running lastnight when we went home.

---

### Post by trmentry on 2008-05-08
Well I rebooted the VM and kicked off my apt-get and its finishing up the last few downloads.

Does anyone have any ideas how a filesystem goes to read-only spontaneously?

---

