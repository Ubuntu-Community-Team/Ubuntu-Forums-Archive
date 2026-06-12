---
title: "Edgy debootstrap"
date: 2006-12-29
forum: General Help
---

### Post by DaveQB on 2006-12-29
Actually seems a problem with chroot, but not sure what the problem is. See here:

```

root@jlh:/mnt# mke2fs  -j /dev/sdc1
mke2fs 1.39 (29-May-2006)
.....
Writing inode tables: done
Creating journal (32768 blocks): done
Writing superblocks and filesystem accounting information: done
This filesystem will be automatically checked every 25 mounts or
180 days, whichever comes first.  Use tune2fs -c or -i to override.

root@jlh:/mnt# mount /dev/sdc1 usb

root@jlh:/mnt# debootstrap --arch i386  edgy usb file:/mnt/iso/ubuntu
I: Retrieving Release
I: Retrieving Packages
I: Validating Packages
I: Resolving dependencies of required packages...
I: Resolving dependencies of base packages...
I: Checking component main on file:/mnt/iso/ubuntu...
I: Retrieving libatm1
I: Validating libatm1
W: Failure trying to run: chroot /mnt/usb mount -t proc proc /proc

root@jlh:/mnt# cat usb/debootstrap/debootstrap.log
ar: /mnt/usb/: File format not recognized

zcat: stdin: unexpected end of file
chroot: cannot run command `mount': No such file or directory
root@jlh:/mnt# debootstrap --arch i386  edgy usb file:/mnt/iso/ubuntu
I: Validating Packages
I: Resolving dependencies of required packages...
I: Resolving dependencies of base packages...
I: Checking component main on file:/mnt/iso/ubuntu...
I: Validating libatm1
W: Failure trying to run: chroot /mnt/usb mount -t proc proc /proc

root@jlh:/mnt# chroot /mnt/usb mount -t proc proc /proc
chroot: cannot run command `mount': No such file or directory
root@jlh:/mnt# echo $?
127


```

I read somewhere on my searches that exit code 127 for chroot means it could not find the command.  So I tested out chroot on its own, on a random directory.

```

root@jlh:/mnt# chroot /var/chroot/
chroot: cannot run command `/bin/bash': No such file or directory

```

Its an empty dir.

I tried running debootstrap but using sid and a sid http URL and it started working, grabbed 20MB of packages before I killed it.  Would fail the chroot part, I am sure.

So is my chroot broken?

This is an Kubuntu Edgy amd64 system.

PS I tried following the many 32bit chroot tutorials out there, similiar results.

---

### Post by DaveQB on 2006-12-29
Ok I let the Debian Sid debootstrap finishing downloading etc.  It didnt seem to try to chroot on its own; completed successfully.  So I did a simple

```

chroot /mnt/usb

```

And it was successful!

Any idea's ?

---

### Post by DaveQB on 2006-12-31
Any idea's people ?

---

### Post by pseudonym on 2007-01-01
> **DaveQB said:**
> Any idea's people ?
I've only just started using chroot but my guess is that the warning - ```
W: Failure trying to run: chroot /mnt/usb mount -t proc proc /proc
``` is just some unnecessarily verbose nonsense that you shouldn't be concerned about. Maybe it has to do with the fact you pointed debootstrap to a usb drive, I don't know. But if everything's set up and working now, I wouldn't worry about it.

After all, you're going to have /proc (among others) bind mounted to your chroot after it's set up, so I don't know what debootstrap was trying to do there.

One other thing - running 'chroot /var/chroot/' will fail if you haven't already run debootstrap and pointed it to /var/chroot, because there's nothing there to 'chroot' into. :)

HTH :)

---

### Post by DaveQB on 2007-01-01
Nah its not working, well at least not with Ubuntu Edgy.  Had to use sid and a Debian repo to get it anything to work, but prefer to use Ubuntu if I can, hence this thread.

The whole debootstrap process halts when this error occours and the dir is so empty compared to when I used sid repo.

Thanks anyway.

---

### Post by pseudonym on 2007-01-01
I hope I'm not headed for this when I set my chroot up :(

I had one set up on etch but the problem I had was with schroot -  my /home wasn't being unmounted cleanly because of it and it caused recovery mounts on the XFS filesystem each time I booted up. Not a good look. :(

---

### Post by DaveQB on 2007-01-01
That would be bad.

The sid debootstrap didn't complete entirely either.  Well it did, but then chrooting into it and trying to finish off setting it up (ie kernel and grub etc) I had permission denied errors on /dev/null, yet it was mounted fine and had 666 perms on it!?!

---

