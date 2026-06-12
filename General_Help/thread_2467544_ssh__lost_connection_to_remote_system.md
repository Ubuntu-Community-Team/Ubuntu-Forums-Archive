---
title: "ssh  lost connection to remote system"
date: 2021-09-30
forum: General Help
---

### Post by Old Jimma on 2021-09-30
Hello:

I've been using ssh with rdiff-backup to backup data from a client (running 20.04) to a server (running 20.04).

There is ore than enough space (>1TB) on a hard drive that is mounted on the server to store the data on the client.

However, the server itself has only 250Gb of storage.

Here is what is happening:

[LIST]
[*]**I get a message on the server that the connection to the client is lost**, and 
[*]**I find that the directory where the mount point is has filled up with data.**.. and consumed almost all of the 250Gb of storage on the server.
[/LIST]

I'm pretty sure the mount is set up correctly: 
[LIST]
[*]the server "user" owns the mount point and the directory /mnt/dirname , and
[*]the sever "user" has read, write, and execute privileges at the mount point.
[*]
[/LIST]

The command issued on the server to run rdiff-backup is routine:
> rdiff-backup clientname@ipaddress::/home/clientname /mnt/dirname


I am certain that ssh was working: Immediately before issuing the rdiff-backup command, I issued:
> ssh clientname@ipaddress
and I saw the clients home directory there... with all the usual directories.

**What did I do wrong?**

Thanks, 
Old Jimma

---

### Post by CharlesA on 2021-09-30
Hi there,

You have two colons in the command you posted. I don't know if this is a typo or not, however.

> ```
rdiff-backup clientname@ipaddress::/home/clientname /mnt/dirname 
```

Have you verified the directory you are copying files to is actually mounted on the server? I've run into issues where I thought something was mounted, but it was not mounted.

You can verify the mount via a couple of ways by running these commands on the server.

```
mount
```

This will return all your mountpoints, which might be hard to filter as it can be a huge list.

```
mountpoint /path/to/mountpoint
```

This will return one of two things, either "/path/to/mountpoint is not a mountpoint" or "/path/to/mountpoint is a mountpoint"

---

