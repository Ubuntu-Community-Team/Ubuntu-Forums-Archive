---
title: "Linux Root filesystem has errors"
date: 2007-01-25
forum: General Help
---

### Post by Souljah on 2007-01-25
Hi guys,

When I start up ubuntu, in the boot up process while checking the root filesystem or files, it reports an error and a check is force. It's not fully compliant, by like 1.73%. How do I fix it? Is there checkdisk like windows has one? THanks.

---

### Post by frolle on 2007-01-25
Did you test your hdd for bad sectors?

---

### Post by Souljah on 2007-01-25
How can I do that via linux?

---

### Post by Souljah on 2007-01-25
I'm able to boot into Linux and windows just fine, it's just that it gives an error. So how do I fix it?

---

### Post by floke on 2007-01-25
Unless the error is giving you problems it might be that you don't have to worry too much about it. I've had disk errors before, but everything continued to work fine - eventually though Ubuntu told me that I should run some commands to fix them, which I followed and sorted it.

I think there's a command called fsck that you can use to check a disc - this will run automatically on your hard drive after every 30 mounts (i.e boot ups). Fsck should only be used on unmounted discs though, so you couldn't do it straight from the GUI after logging in.

Am interested to know how this would be done myself, so will keep watching this thread - hopefully someone will post the proper instructions :)

---

### Post by Souljah on 2007-01-25
Well judging from what you say, I guess I can boot from a live cd and run FSCK. I was told to run that as well. Don't know what it does but I'm willing to find out.

---

### Post by bodhi.zazen on 2007-01-25
could you be more specific with the error message you are getting ?

to run fsck:

```
fsck -rfv 
```Were /dev/hdxy is the partition to check. ? hda1

Run from a live Cd with the partition unmounted.

---

### Post by Souljah on 2007-01-26
All it says while checking the root file system during the boot up process is that Linux filesystem has errors, check forced. Be aware that "Linux" is the name given for it in windows. There's non contiguous files in the percentage of 1.73%.

---

### Post by Souljah on 2007-01-26
It gave me this information when running FSCK from the live cd:

```
root@ubuntu:~# fsck -rfc /dev/hda2
fsck 1.38 (30-Jun-2005)
e2fsck 1.38 (30-Jun-2005)
Checking for bad blocks (read-only test): done                        535
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

Linux: ***** FILE SYSTEM WAS MODIFIED *****
Linux: 112087/1921984 files (1.7% non-contiguous), 1237371/3839535 blocks
```

Does this mean that it was fixed?

EDIT: NVM, it was fixed. :) Thanks.

---

### Post by golem3 on 2007-02-13
thanks guys. You just saved my ***, not to mention my dying Ubuntu install. :) :) :) :)

---

