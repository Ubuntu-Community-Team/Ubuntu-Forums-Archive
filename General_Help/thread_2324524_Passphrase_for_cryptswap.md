---
title: "Passphrase for cryptswap"
date: 2016-05-14
forum: General Help
---

### Post by fltrx on 2016-05-14
After some moving of partitions, my Ubuntu Mate still boots, but strangely it asks for a passphrase for the cryptswap1 volume. I don’t enter anything and hit enter and it works. As I understand it, the swap partition only needs a random passphrase on every boot process. But how can I make the prompt disappear and Ubuntu figure out a passphrase without user interaction?

---

### Post by a_guenther on 2016-07-29
I have the same problem, and figured out it seems related to a bug described here: [https://bugs.launchpad.net/ubuntu/+source/ecryptfs-utils/+bug/1453738](https://bugs.launchpad.net/ubuntu/+source/ecryptfs-utils/+bug/1453738)
I followed a workaround described here in the end: [https://askubuntu.com/questions/341979/what-to-do-about-the-disk-drive-for-dev-mapper-cryptswap1-is-not-ready-yet-or](https://askubuntu.com/questions/341979/what-to-do-about-the-disk-drive-for-dev-mapper-cryptswap1-is-not-ready-yet-or) and here: [http://punygeek.blogspot.com/2012/10/ubuntu-1204-how-to-solve-disk-drive-for.html](http://punygeek.blogspot.com/2012/10/ubuntu-1204-how-to-solve-disk-drive-for.html)

It works for me half way: During bootup, I get not asked for the cryptswap password anymore, but the swap isn't activated neither.
Everything seems fine, after "sudo swapon /dev/sdXX" I have the swap active:
```
free -m
              total        used        free      shared  buff/cache   available
Mem:           3829        1645         374         531        1809        1354
Swap:          3814           0        3814

```

 But the next step, "sudo ecryptfs-setup-swap" gives me
```
WARNING:
An encrypted swap is required to help ensure that encrypted files are not leaked to disk in an unencrypted format.

HOWEVER, THE SWAP ENCRYPTION CONFIGURATION PRODUCED BY THIS PROGRAM WILL BREAK HIBERNATE/RESUME ON THIS SYSTEM!

NOTE: Your suspend/resume capabilities will not be affected.

Do you want to proceed with encrypting your swap? [y/N]: y

INFO: Setting up swap: [/dev/sda8]
/dev/sda8 is already marked as no-auto
swapon: stat of /dev/mapper/cryptswap1 failed: No such file or directory

```
And indeed, I don't have /dev/mapper/cryptswap1. After this line, the swap doesn't work anymore:
```
free -m
              total        used        free      shared  buff/cache   available
Mem:           3829        1650         408         491        1770        1388
Swap:             0           0           0

```

After that, I continued as descibed with /etc/crypttab and /etc/fstab, adding noauto. In crypttab, the original line had offset=1024, not sure if I have to really change it to 8, but both was not helping for me.

I created as described /etc/init/cryptswap1.conf, but I guess again the problem is I don't have /dev/mapper/cryptswap1. So, after a reboot I seem to have no running swap (no entry in swapon -s)

Anyone who can help me? How do I generate /dev/mapper/cryptswap1, or in what should I change these lines?

My system: Kubuntu 16.04...

---

### Post by a_guenther on 2016-08-02
Found somewhere in the solution:
Using in /etc/crypttab instead of the UUID the sdX-value of the partition did the job for me. I have after a reboot the swap running and don't get asked for the password before the login. And I guess/hope the swap is really encrypted (probably not a huge problem for me if not, but why not...). Is there a way to check this?

---

