---
title: "Attempting to move /home to another partition"
date: 2007-05-02
forum: General Help
---

### Post by gjtoth on 2007-05-02
Here's what's transpired so far:

* I did a fresh install of Feisty. During the install, Feisty gave me the option to create another partition on the drive, which I did and Feisty was installed on the blank partition leaving the old Beta Feisty on the other partition intact -- Boy did THAT come in handy as I forgot to back up a couple of directories! The FRESH INSTALL Feisty is on HDA3 whilst the old system is on HDA1.

* After I was certain I had everything I needed from the old system partition, I booted up GParted and formatted that partition in Ext 3.

* Copied my current /home directory over to the HDA1.

I've attempted to follow the instructions here and at PsychoCat's however, here's where I'm stuck. My fstab looks like this:

# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>

proc /proc proc defaults 0 0
#Entry for /dev/hda3 :
UUID=e30f5fa4-1e53-415a-b883-05de046a3162 / ext3 defaults,errors=remount-ro 0 1
#Entry for /dev/hda6 :
UUID=479adf52-64b9-48d5-8c42-13362a913725 none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/hdd /media/cdrom1 udf,iso9660 user,noauto 0 0
/tmp/app/1/image /tmp/app/1 cramfs,iso9660 user,noauto,ro,loop,exec 0 0
/tmp/app/2/image /tmp/app/2 cramfs,iso9660 user,noauto,ro,loop,exec 0 0
/tmp/app/3/image /tmp/app/3 cramfs,iso9660 user,noauto,ro,loop,exec 0 0
/tmp/app/4/image /tmp/app/4 cramfs,iso9660 user,noauto,ro,loop,exec 0 0
/tmp/app/5/image /tmp/app/5 cramfs,iso9660 user,noauto,ro,loop,exec 0 0
/tmp/app/6/image /tmp/app/6 cramfs,iso9660 user,noauto,ro,loop,exec 0 0
/tmp/app/7/image /tmp/app/7 cramfs,iso9660 user,noauto,ro,loop,exec 0 0

How do I tell it to make the HDA1 /home my home and not the HDA3?

I've done a search and the only thing I get are instructions telling folks to do:

/dev/hda1	/home		ext3		nodev,nosuid,errors=remount-ro

....which doesn't work with the new drive naming convention.

Any takers?

---

### Post by dcstar on 2007-05-02
> **gjtoth said:**
> Here's what's transpired so far:

* I did a fresh install of Feisty. During the install, Feisty gave me the option to create another partition on the drive, which I did and Feisty was installed on the blank partition leaving the old Beta Feisty on the other partition intact -- Boy did THAT come in handy as I forgot to back up a couple of directories! The FRESH INSTALL Feisty is on HDA3 whilst the old system is on HDA1.

* After I was certain I had everything I needed from the old system partition, I booted up GParted and formatted that partition in Ext 3.

* Copied my current /home directory over to the HDA1.

I've attempted to follow the instructions here and at PsychoCat's however, here's where I'm stuck. My fstab looks like this:

# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>

proc /proc proc defaults 0 0
#Entry for /dev/hda3 :
UUID=e30f5fa4-1e53-415a-b883-05de046a3162 / ext3 defaults,errors=remount-ro 0 1
#Entry for /dev/hda6 :
UUID=479adf52-64b9-48d5-8c42-13362a913725 none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/hdd /media/cdrom1 udf,iso9660 user,noauto 0 0
/tmp/app/1/image /tmp/app/1 cramfs,iso9660 user,noauto,ro,loop,exec 0 0
/tmp/app/2/image /tmp/app/2 cramfs,iso9660 user,noauto,ro,loop,exec 0 0
/tmp/app/3/image /tmp/app/3 cramfs,iso9660 user,noauto,ro,loop,exec 0 0
/tmp/app/4/image /tmp/app/4 cramfs,iso9660 user,noauto,ro,loop,exec 0 0
/tmp/app/5/image /tmp/app/5 cramfs,iso9660 user,noauto,ro,loop,exec 0 0
/tmp/app/6/image /tmp/app/6 cramfs,iso9660 user,noauto,ro,loop,exec 0 0
/tmp/app/7/image /tmp/app/7 cramfs,iso9660 user,noauto,ro,loop,exec 0 0

How do I tell it to make the HDA1 /home my home and not the HDA3?

I've done a search and the only thing I get are instructions telling folks to do:

/dev/hda1	/home		ext3		nodev,nosuid,errors=remount-ro

....which doesn't work with the new drive naming convention.

Any takers?

You just need a /home directory on your new root partition, and there is no reason whatsoever why you can't mount it with the following fstab line (assuming hda1 is an ext3 filesystem):

```
/dev/hda1	/home		ext3		defaults 0 0
```

---

### Post by gjtoth on 2007-05-04
I figured out why it wasn't working.  When I copied the directory over, it changed the owner to root.  /home needs to be owned by root, apparently.  However, my /home/xxxxx directory must be owned by me.

I've tried sudo chown -R /dev/hda1/home/gary gary but the response I get is "Invalid user"  Yet I type whoami it shows ME!  

Any ideas?

---

### Post by psusi on 2007-05-04
You got the command parameters backwards.  It is chown [user] [file].

---

### Post by gjtoth on 2007-05-04
> **psusi said:**
> You got the command parameters backwards.  It is chown [user] [file].

It's still showing root as the owner.  I'm going to try creating a directory on the drive as me then copy the contents of my current /home into it. 

Thanks for the help.

---

### Post by kleam on 2007-05-04
I was just in another forum thread and I saw this link, I hope this helps you. 

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

Im not a guru in the linux, but it should be aroudn the same path as you and might help a little


-Kleam



Also, here is a link to the thread:

[http://ubuntuforums.org/showthread.php?t=390871](http://ubuntuforums.org/showthread.php?t=390871)

---

### Post by gjtoth on 2007-05-04
> **psusi said:**
> You got the command parameters backwards.  It is chown [user] [file].

That did the trick!  Thanks to everyone's help, I've got my /home directory on a separate partition.  NOW... how do I get at the OLD /home directory on the system partition so I can remove it?

---

### Post by psusi on 2007-05-06
You didn't rename or remove it before mounting the new partition in /home?  Then you will need to boot into rescue mode and unmount /home, then rm -fr /home/*

---

