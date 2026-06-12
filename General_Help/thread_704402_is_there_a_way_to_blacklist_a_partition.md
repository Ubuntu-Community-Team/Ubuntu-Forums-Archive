---
title: "is there a way to blacklist a partition?"
date: 2008-02-22
forum: General Help
---

### Post by ibuclaw on 2008-02-22
Hi, since, no one seemed to answer my previous post (let alone read)

I'd like to ask if there is a way to blacklist a partition in ubuntu.

I had a mounting/unmounting problem with the /dev/scd0. And the only way I could think of resolving it was (the last thing that I wanted to do)
```

chmod 4755 /bin/mount
chmod 4755 /bin/umount

```

And now I have a bigger problem, anyone can mount and unmount whatever the hell they like!

One drive inparticular is the sda1 partition (windows), that in my /etc/fstab is disabled by default so no one can open it (except root):
```

# /dev/sda1
#UUID=0EDC5AC0DC5AA1AF /media/.sda1     ntfs    defaults,umask=007       0       1

```

Again, a quick reply would be appreciated.

Iain

---

### Post by kuja on 2008-02-22
I've never heard of any way to do it. Perhaps it might be worthwhile to change the perms back and figure out how to fix the real problem at hand?

---

### Post by astrotech226 on 2008-02-22
I found your other thread and looked through it.  I don't think what you are describing is possible.  If the directory under home is the only thing that was modified, there would be no reason for the new issues with mounting and cds.  Could there have been more modifications done outside of /home?

Can we start back from the beginning and look at a few things?  Your entry for sda1 is fine.  The defaults option includes nouser meaning you'd need to be root to mount it.

It looks like your permissions for mount are OK.  It should be suid and everyone can execute it.

Here's a simple test you can try.  Mount sda1 as root.  Then, as a normal user, try something like this:

```
mount -o remount /media/.sda1
```

You should get a message claiming only root can do that.  And when you say anyone can mount and unmount everything, does that mean cds and usb keys?  Or do you mean *every* partition.  If you have a partition for /boot, are you saying a normal user can unmount it?

---

### Post by ibuclaw on 2008-02-22
Sorry for the late response, I've been going up and down all day and I've had to cool off.

Ah, now you see, what I have a hunch on is that, despite it was done in the home directory, I think one of the users has a wine symlink to the "/" location of the filesystem.

So that's why it has spread to the whole system.

I've put harsher restrictions on sudo, so I think the issue is solved.

But now I'm back to the CD-ROM mounting issue. The only small itch is that the drive doesn't auto-mount/auto-unmount at "subuser" level.

Which can be annoying, if someone is repeatedly tapping the eject button, but the drive doesn't open.

---

### Post by ibuclaw on 2008-02-22
I've just read your post in the other thread too.

Yes, I do have a separate home partition.
And it may be worth a shot later on
QUOTE:```

dpkg --list | grep -e ^ii.* | sort | cut -d ' ' -f 3 | tr '\n' ' ' > $HOME/installedpackages .......... sudo apt-get install `cat installedpackages`

```.

I'm just having a feeble attempt at the moment and am re-installing everything on the system. (all 7,000+ packages...)
I am hoping on the archived binaries will override the tainted binaries and everything will be set back to normal.

Iain

---

