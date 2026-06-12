---
title: "Empty fstab but Ubuntu seems fine"
date: 2008-05-22
forum: General Help
---

### Post by UnicycleBloke on 2008-05-22
I'm using Ubuntu 7.10

Short version:
I've managed to remove all entries from /etc/fstab, but the PC boots just fine and appears normal. I'm a bit confused by this, because I thought fstab was essential. True, I can't see my Windows partition now, but is the root filesystem autoloaded or something?

Long version: 
One of my hard disks is very old and has been complaining for some time (via SMART) that it would soon die. No problem with that, but I decided to keep it for now as a second disk. 
Anyway, it now appears to have finally died, and the PC would not boot - it spent forever trying to mount or repair the filesystem on the dead disk. 

I removed the disk, but then got an error during booting which I took to mean I should remove the corresponding fstab entries, and was dumped at the command line. I attempted to use sed to comment out the offending line, and managed (somehow - I even tested the command before redirecting the output to fstab <grrr>) to turn fstab into an empty file. [I accept that I was a complete idiot for not backing up the file first.]

So I rebooted the PC, expecting trouble, and everything is fine. This is probably normal but I would like to understand what is going on a bit better.

Thanks


Al

---

### Post by geirha on 2008-05-22
If your ubuntu system is located on a single partition, I can imagine it could still work. The root-filesystem is mounted very early in the process, in order to run the init-script that will in turn run all the appropriate /etc/rc?.d scripts.

A minimal /etc/fstab should have these two lines:
```

proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro 0 1

```
where you change /dev/sda1 to whatever device your ubuntu is on. Use "sudo fdisk -l" to find it.

As for sed, doing something like ```
sed 's/foo/bar/' file > file
``` i.e. reading and writing to the same file like this, does not work as expected. Instead you should use the -i option ```
sed -i 's/foo/bar/' file
```

Secondly, there are cli-editors, like vim and nano. nano is probably the easiest, so editing with "sudo nano /etc/fstab" would be much safer all together (Ctrl+X in nano exits and saves).

---

### Post by UnicycleBloke on 2008-05-22
> **geirha said:**
> 
As for sed reading and writing to the same file does not work as expected.

Hehe. Live and learn.

Thanks for your help. I should have noted down the contents of fstab after sed effectively did a cat, but it was full of long and indigestible UUIDs - nothing so simple as your example. Can barely use vim or emacs - perhaps I should learn just enough to get by in an emergency.

While I'm asking, why does Ubuntu name the disks sda, sdb, ... instead of hda, hdb, ... ?

Cheers.

---

### Post by geirha on 2008-05-22
> **UnicycleBloke said:**
> Hehe. Live and learn.

Thanks for your help. I should have noted down the contents of fstab after sed effectively did a cat, but it was full of long and indigestible UUIDs - nothing so simple as your example. Can barely use vim or emacs - perhaps I should learn just enough to get by in an emergency.


In that case, I'd recommend running "vimtutor" in a terminal. It will guide you through the basics of vi/vim.

> **UnicycleBloke said:**
> 
While I'm asking, why does Ubuntu name the disks sda, sdb, ... instead of hda, hdb, ... ?

Cheers.

Technically, it's not ubuntu that names them, it's the kernel. The change came in a kernel version between gutsy's kernel and hardy's kernel. Not sure what the reason was, but probably to get a more unified naming scheme.

---

