---
title: "Deniable Encryption"
date: 2015-03-14
forum: General Help
---

### Post by TinKode on 2015-03-14
Hello. For some time I've been playing around with a quite old build of ubuntu 9.04 attempting to convince myself that I can apply what is so-called "deniable encryption" to my private
data. As far as I understood such condition is met when the ciphertext (added to a headerless block of data) is indistinguishable against pseudo-random noise found on a hard drive.

Now, maybe is because of the old build or because of the fact that I was running from a live cd but in either case I'm not able to bring this to an end.
I tried **losetup** with AES encryption (**-e aes**) , but then the **ioctl: LOOP_SET_STATUS: Invalid argument **arises. Somewhere was suggested patching the kernel as these functions are not recognized, but the */usr/../crypto* wasn't really found in there. Then it came that **-e AES256** shall be used, but the same thing happened, errors on errors. Out of curiosity I decided to do a simple -E 1 (XOR) and of course it worked but then again, in making the filesystem , the partition table was not found (also somewhere reporting a 0-sized partition).

This is sort of an example of the idea:

```
dd if=/dev/urandom of=/dev/sda bs=4K

losetup --offset $RNDOFFSET --sizelimit 5G -e aes -k 256 /dev/loop0 /dev/sda

mkfs.ext4 /dev/loop0

mount /dev/loop0 /mnt/secret
```

I like the idea of the offset mounting but then a problem would be when doing dual bots. What I would like is to have Windows as the main OS, then having an extended unallocated partition where the encrypted data resides. I don't know if Windows would be able to write into this partition, but that would mean the unallocated partition would be a non contiguous area.

Anyways with these ideas thrown here, if someone could bring a bit of help, I would be very grateful...:p


Thanks for reading.

---

### Post by Bucky Ball on 2015-03-14
Welcome. I'd be taking any valuable data off that machine if it is online as 9.04 is wildly out of date, unsupported and hasn't had any updates, most importantly security updates, for four years. Install a supported release.

If the machine is not online, carry on. ;)

---

### Post by TinKode on 2015-03-15
> **Bucky Ball said:**
> Welcome. I'd be taking any valuable data off  that machine if it is online as 9.04 is wildly out of date, unsupported  and hasn't had any updates, most importantly security updates, for four  years. Install a supported release.

If the machine is not online, carry on. [IMG]http://ubuntuforums.org/images/smilies/icon_wink.gif[/IMG]

Thanks for your reply, but I do not really get your point. If by being online you mean connected to Internet, then that is not the case. Anyway, first you suggest to install a supported release, then the next suggestion contradicts the first one , because as per your saying, if the machine is not online, i shall carry on, ignoring my current ubuntu version.

All in all it seems that with Fedora linux I can get something working though not exactly as I wanted (like -k option not recognized).

---

### Post by Bucky Ball on 2015-03-15
What I am saying is you are running an unsupported, vulnerable machine. If you are online, it hasn't had security updates for four years so the machine is vulnerable. I would take it offline.

I am also saying that if the machine is not online, then none of this matters as no-one can get to your machine in any case (because it's not online).

Thirdly, I am saying if you want the machine to be online, upgrade to a supported release that DOES get updates, including security updates. You will not get much (any) support for a release that old and out of support. I hope that is now clear. ;)

---

### Post by Bucky Ball on 2015-03-15
What I am saying is you are running an unsupported, vulnerable machine. If you are online, it hasn't had security updates for four years so the machine is vulnerable. I would take it offline.

I am also saying that if the machine is not online, then none of this matters as no-one can get to your machine in any case (because it's not online).

Thirdly, I am saying if you want the machine to be online, upgrade to a supported release that DOES get updates, including security updates. You will not get much (any) support for a release as old out-dated as 9.04. 

Summing up. 9.04 is old, dead, unsupported and the software is archaic. But if the machine is offline and you don't care about any of that and the fact you will get little support for it here as no-one has used it for years, then carry on. 

I hope that is now clear. ;)

Please see [here]("http://ubuntuforums.org/showthread.php?t=2229730").

---

### Post by HermanAB on 2015-03-15
The whole point of encryption is to make data look like random noise.

---

