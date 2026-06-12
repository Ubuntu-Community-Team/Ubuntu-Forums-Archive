---
title: "What name to use in activation of encrypted root partition?"
date: 2019-02-20
forum: General Help
---

### Post by jm672295 on 2019-02-20
I am trying to run the [Boot Repair]("https://help.ubuntu.com/community/Boot-Repair") tool on a system with an encrypted (LUKS) root partition. [This post]("https://dev-notes.eu/2016/09/mount-and-transfer-data-from-an-encrypted-filesystem-in-ubuntu/")  tells me to "activate the encrypted drive using the correct name". That  name should be given by /etc/crypttab in the live system.


  My /etc/crypttab in the live system has no entries.

  [B]
How can I identify/find the name I need?[/B]

     

(Note that I have also asked this on [askubuntu]("https://askubuntu.com/q/1119579/925683") where it hasn't gotten much attention)

---

### Post by TheFu on 2019-02-20
I don't know of anyway to lookup the name. It needs to be known.
Perhaps writing a script to try some names using cryptsetup status {name} would work, eventually?
```
:/proc/32402$ sudo cryptsetup status sda3_crypt
/dev/mapper/sda3_crypt is active and is in use.
  type:    LUKS1
  cipher:  aes-xts-plain64
  keysize: 512 bits
  device:  /dev/sda3
  offset:  4096 sectors
  size:    115175424 sectors
  mode:    read/write
  flags:   discards
```
If you used the automatic setup via the installer with LUKS and LVM, then sda3_crypt is a good guess.
If you get the name wrong:
```
:/proc/32402$ sudo cryptsetup status sda3_foo
/dev/mapper/sda3_foo is inactive.

```

and just for some extra clarity:```

$ more /etc/crypttab 
sda3_crypt UUID=2c1838d7-d5de-406f-9b14-aa1b21480f1e none luks,discard
```

---

### Post by jm672295 on 2019-02-21
The solution, as it turns out, is simple: The name I need is in the /etc/crypttab of the *installed system*, not the live system.

To get it, decrypt the root partition of the installed system, mount it and open /etc/crypttab there. A more detailed procedure is given by [this answer]("https://askubuntu.com/a/1119909/925683"), which worked for me.

---

