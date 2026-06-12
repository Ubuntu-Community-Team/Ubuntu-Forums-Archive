---
title: "Secure Delete Tools"
date: 2008-01-10
forum: General Help
---

### Post by Sutur on 2008-01-10
Hi, just installed the secure delete tools. The manual pages are great but I'm a little confused about the **sfill** command.

Is there a way to use sfill to wipe over all free space on a specific disk, and **not** delete any existing files and directories?

I've used the *rm -rf* command a lot in the past and I thought it might be wise to securely wipe areas of the disk that report to be empty, but are actually laden with unlinked files.

Help appreciated.

---

### Post by the_cog on 2008-01-12
I am interested in this as well.

I found this:
[http://www.mirrors.wiretapped.net/security/host-security/secure-deletion/secure-delete/secure-delete-README.txt](http://www.mirrors.wiretapped.net/security/host-security/secure-deletion/secure-delete/secure-delete-README.txt)

But I would like to see some examples.

Thanks

---

### Post by Sutur on 2008-01-12
Thank you cog that was a very interesting read.

I followed his link to [Anonymizing UNIX Systems]("http://freeworld.thc.org/papers/anonymous-unix.html#1"), which was nothing short of *fascinating*.

However, I noticed a possible leak in it's security strength:

When he explains how to crypt your home folder, it theoretically works very well, but let's say for example, that someone were to remove the disk on which the home folders for the users in question were stored.

Couldn't that someone put that disk into another UNIX OS, log in as root, and bypass all the encryption? Or is it fully encrypted even to ROOT?

---

### Post by HermanAB on 2008-01-12
Hmm, people are always interested in securely deleting stuff.  Unfortunately, the bottom line is that it is impossible.  Anyone who says otherwise, is selling snake oil.

The only way to 'delete' a file completely is to encrypt it, then go on a nice holiday and forget the key.  The only way to properly encrypt a file without danger that there are plain text copies of it elsewhere is to use an encrypted file system.

So, if you are not use encryption and you have sensitive data, then you should read up on dm-crypt and cryptsetup.

If you have a hard disk full of incriminating crud, get a big hammer, or take it out onto a range for target practice.

Cheers,

Herman

---

### Post by Sutur on 2008-01-12
> **HermanAB said:**
> Hmm, people are always interested in securely deleting stuff.  Unfortunately, the bottom line is that it is impossible.  Anyone who says otherwise, is selling snake oil.

The only way to 'delete' a file completely is to encrypt it, then go on a nice holiday and forget the key.  The only way to properly encrypt a file without danger that there are plain text copies of it elsewhere is to use an encrypted file system.

So, if you are not use encryption and you have sensitive data, then you should read up on dm-crypt and cryptsetup.

If you have a hard disk full of incriminating crud, get a big hammer, or take it out onto a range for target practice.

Cheers,

Herman

I don't think it's quite as black and white as that.

It depends heavily on how badly someone wants to retrieve the data, and how much of it they want to retrieve.

If you take a hammer to your hard drive, it's possible that a surprising amount of data you thought was secure could probably be recovered by someone who really, *really* wants some traces of your data.

But then for someone to go through the work it would take to recover it, you would need some seriously sought-after data - [**this**]("http://www.datadev.com/pd87001.html") might do the trick though ;-)

I always thought that it was a poor idea though, surely for 20K you could buy a homemade rocket, attach your HDD, and send it into outer space!

---

