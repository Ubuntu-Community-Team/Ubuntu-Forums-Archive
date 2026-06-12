---
title: "Problem(s) with shared encrypted partition in 12.10"
date: 2013-03-18
forum: General Help
---

### Post by sbougerolle on 2013-03-18
I've got a desktop box (64-bit, Intel core duo) with multiple Linux installations, to which I've just added Ubuntu 12.10.  The main Linux setup is on /dev/sda2 and has an encrypted /home partition /dev/sda3 (standard dm-crypt, no LUKS).  Ubuntu will not load this at boot time no matter what I do, and I've tried lots of things... read on...

The relevant crypttab line is:
```
sda3_crypt /dev/sda3 none cipher=aes,hash=plain
```

and corresponding fstab entry (temporarily relocated to /mnt/tmp instead of /home for obvious reasons):
```
/dev/mapper/sda3_crypt /mnt/tmp           xfs     defaults        0       2
```

It asks for the passphrase at login, then hangs until I skip mounting.  The log shows this error:
```
[COLOR=#ff8c00] * sda3_crypt (starting)..
Cannot read requested amount of data.
device-mapper: rename ioctl on sda3_crypt_unformatted failed: No such device or address
Command failed
 * sda3_crypt (started)...   
    ...done.
[/COLOR]
```

I know there's no basic problem with the setup because I can start it by hand just fine (cryptsetup -h plain -c aes create sda3_crypt /dev/sda3).  It seems to be something peculiar to the boot environment, and it's doubly confusing since bootup mounts a different encrypted partion with no problems (see below).  I *could* just work around this and shoehorn in a boot script containing that manual command, but I'd prefer to do it right.

_Also_... while wrestling with this I thought I'd try setting up a separate encrypted partition (sdb8) in Ubuntu using LUKS and reading that in my main setup (sda2, on which I installed cryptsetup-1.6.0).  That doesn't work either; the Ubuntu side works fine, but calling cryptsetup on that from the other gives me weird read/table ioctl errors.  

I have no idea why either of these problems is occurring, except that it does seem something peculiar to Ubuntu (Debian manages to share a partition ok).  Any insight, anyone?

---

### Post by sbougerolle on 2013-03-19
Ok, I found my own fix.

In /lib/cryptsetup/cryptdisks.functions, in the function do_noluks, there's a line:
```
#PARAMS="$PARAMS --key-file=$key"
```

Commenting this out solves the problem.  It still takes the pass phrase even without explicitly specifying a pipe as input.

The key-file arg works fine when called with luksOpen instead of create, for some reason that should probably be looked into by the appropriate maintainer.

---

