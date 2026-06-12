---
title: "Encry...!@1n!@3n123 ...tion"
date: 2007-03-02
forum: General Help
---

### Post by SirMADOG on 2007-03-02
I am looking for ways to secure my data on my Ubuntu computer. 

I would like something to be attached to my login similar to a windows environment where all my files are encrypted to my password and if root were to change my password my data would be lost. What kind of options are available?

---

### Post by Yoooder on 2007-03-02
Personally, I have an encrypted filesyste in a file.  I can mount the filesystem and use it to store whatever I want, and when I unmount it again it is unreadable.

I can't give you a full walkthrough (my setup is very needs-specific).  But here's the beginning of things:

**Prerequisites:** (apt-get install these)
 - losetup
 - cryptsetup

1) Make a file to hold the filesystem.  Make it large enough for your needs:
> dd if=/dev/zero bs=1G count=5 of=FileNameGoesHere
This will make a 5GB file.  You can play with the size (if you want 1GB then use bs=1G count=1, if you want 500MB then use bs=1M count=500, etc...)

2) Tie the file you just created to a loopback device.  You can actually use a crypto loopback device which is a shorter setup, but cryptoloop is going away in favor of device-mapper encryption (just a newer technology).
> losetup /dev/loop0 FileNameGoesHere

At this point the file you created is just like a new harddrive (with a device name of /dev/loop0)

You can use it to store files if you format it BUT IT'S NOT ENCRYPTED JUST YET.

3) Use cryptsetup to encrypt your new (virtual) disk.  Using the below command it will ask you for a Password.  This is used to unlock the encrypted device itself, so it should be unique and STRONG.  A single password is *ok* however, it is crackable.  I personally use 6 of my passwords strung together to form an extremely strong Passphrase.  If you crunch the numbers, you will find that to get a decent level of protection you'll want to have a passphrase of ~25 characters that aren't just everyday words.  By a "decent level of protection" I mean that it would take several years to crack via brute force assuming 300,000 attempts per hour--kind of overkill, but it's important you understand that no matter how strong your encyrption is it's only ever as strong as your key!
> cryptsetup -y create GiveItANameHere /dev/loop0

Anyways, at this point you will have an encrypted device name /dev/mapper/GiveItANameHere (the same thing you entered above) that can be mounted, formatted, and used as normal.

Here's the catch:  You'll have to do some reading into both losetup and cryptsetup to get it to be easily mountable after a reboot.  There's not too much to it, but you really should read into it (versus letting me give you all the answers).  You can then add fstab entries to allow you to mount it with just a couple commands, you can take those commands and put them in a script if you like--I'll leave your level of integration to you.

btw) this is more manual than what you've asked for.  I know how to tie this setup to a login, but I highly discourage it.  That would mean that if your user account is hacked everything is in the open.  By not tying it to a login you add a significant level of security.

---

