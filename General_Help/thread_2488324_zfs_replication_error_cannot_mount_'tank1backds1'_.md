---
title: "zfs replication error: cannot mount 'tank1/back/ds1': Insufficient privileges"
date: 2023-07-01
forum: General Help
---

### Post by qombi on 2023-07-01
Hello I am attempting to replicate between two ubuntu lts 22.04 servers. I verified ssh auth is working. 

I added zfs permissions to each server for the zfs user: 

source: 
```

 zfs allow tank
---- Permissions on tank1 ----------------------------------------------
Local+Descendent permissions:
        user zfs compression,create,destroy,hold,mount,mountpoint,receive,rollback,send,snapshot

```
destination: 
```

zfs allow zp0
---- Permissions on tank1 ----------------------------------------------
Local+Descendent permissions:
        user zfs compression,create,destroy,hold,mount,mountpoint,receive,rollback,send,snapshot

```
from destination pull:

```
 
ssh zfs@10.3.3.38 zfs send tank1/ds1@autosnap_2023-07-01_00:00:05_daily | zfs receive tank1/back/ds1

```

---

### Post by qombi on 2023-07-01
if I try a simple unmount of all mounted zfs datasets I get permission denied as well

```

zfs unmount -a
cannot unmount '/tank1/back': permission denied

```

```

zfs allow tank1/back
---- Permissions on tank1  ----------------------------------------------
Local+Descendent permissions:
        user zfs compression,create,destroy,hold,mount,mountpoint,receive,rollback,send,snapshot

```

from the zfs allow man page: 

mount	subcommand	Allows mounting/umounting ZFS datasets

---

### Post by qombi on 2023-07-01
```

zfs allow tank1/back
---- Permissions on tank1/back -----------------------------------------
Local+Descendent permissions:
        user zfs compression,create,destroy,mount,mountpoint,receive,rollback

```

---

### Post by MAFoElffen on 2023-07-01
First, please post all commands and output on the Forum within CODE Tags... You can do that in two ways. First via typing them in manually like this:

[noparse]```

Type in or
    Paste your
    Commands or
    output in
here

```[/noparse]

Or the second way, which is to use the advanced editor, which in the edit menu, the "#" Icon will add Code tags to the post wherever you have the cursor. If you select text to highlight with your mouse, it will wrap the CODE tags around that highlighted text... Doing it this way is a Forum Policy. Let's keep you out of trouble here. Raw output and commands posted outside of or no using CODE tags can cause havoc with the Forums filters and software. Please go back to your previous posts and edit them, to keep you off the Moderators radar...

Second, past your commands directly from terminal window were they were executed, so we may see at what elevation they were executed, and the exact error that was returned. Why, because all those commands should be executed in an elevated state as root or with sudo... Since I manage all my servers from ssh, from a Graphical terminal session on my management console, it is easy to copy/paste from those sessions.

If you had tried to execute those commands from a command prompt as a user, would would get those error message as posted, but... I cannot tell, as per the way you posted them. It there was another problem, the returned error would be different, as with they were busy or other errors.

It would help me and a few of the others that specialize with help with support for ZFS, if you ran the UbuntuForums 'system-info scirpt, using the "--details" startup option, and posted the URL of where the reports get uploaded to:
```

wget -N -t 5 -T 10 https://github.com/UbuntuForums/system-info/raw/main/system-info && \
chmod +x system-info && \
./system-info --details

```
Here, as an example one one I just ran on one of my ZFS based servers: [https://paste.ubuntu.com/p/KbZkqF8XrQ/](https://paste.ubuntu.com/p/KbZkqF8XrQ/)

Ignore the warning that says some required utilities are not installed and type <C><Enter> to continue. You can see from the above posted report of mine, that the posted report info has been sanitized by the script to censor any possible sensitive details, so is safe to be posted to a pastebin. You can also see where that kind of ZFS volume manager information is helpful to diagnosing your problem.

Even though the replicated pools can be different in basic structure, since ZFS replication depends that both replicated pools have the same explicitly enabled features matching on both pools, please post the output of this from both servers, so that we can compare them:
```

sudo zfs get all | grep --color=never '[a-z]@[a-z]\|[a-z]:[a-z]'

```
Please verify that both server can ssh between each other and have valid generated ssh keys as the root user. Even though ZFS will give a user the permissions to do zfs-send and zfs-receive using zfs allow, verify that the command being used are via the root user. Because of this, please verify that you have ssh configured in  as "PermitRootLogin yes"...
```

grep "PermitRootLogin" /etc/ssh/sshd_config

```
Next, please post the exact 'zfs send <poool_or_datapool_snapshot_name> | zfs recieve <pool_or_dataset_snapshot_name>' command that you used and it's output... For example
```

sudo su
zfs send -v tank/usr/home/dru/test@testbackup | ssh -v root@10.0.2.15 zfs receive -v backups/test

```
Note that for testing and diagnostics, that you will be using the "-v" option on all to see the verbose output of shh, zfs-send, and zfs-recieve to check for any errors...

---

### Post by qombi on 2023-07-01
Thanks for the information, I edited my post. Your post led to me learning that zfs allow mount doesn't work. Linux requires root to mount. After running the replication command from the backup server as root, pulling over a non-root user, it worked without issue.

---

### Post by MAFoElffen on 2023-07-02
LOL. That is what I suspected. Both 'zfs <command> <options> <dataset>' and 'zpool <command><options><pool>' require elevated permissions to work..

So is this "Solved" now?

---

