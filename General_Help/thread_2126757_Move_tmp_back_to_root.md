---
title: "Move /tmp back to root"
date: 2013-03-18
forum: General Help
---

### Post by Wtwine on 2013-03-18
Hi 

I moved /tmp to RAM to improve performance by adding the following to fstab:

```
# Move /tmp to RAM
tmpfs /tmp tmpfs defaults,noexec,nosuid 0 0
```

However, this turned out to be a bad idea for me (poor performance and can't install some packages in R because of the way it uses /tmp), so I want to move /tmp back to root.

How do I do that?

The following link refers with same query posted by somebody else (but no answers): [http://ubuntuforums.org/showthread.php?t=1158145](http://ubuntuforums.org/showthread.php?t=1158145)

---

### Post by dino99 on 2013-03-18
mkdir tmp

as everything into ram is lost after reboot of course (so nothing to move)

---

### Post by Wtwine on 2013-03-18
That was easy!  Just commented out the line in fstab which moved /tmp to RAM, then mkdir tmp in terminal, and rebooted.  Thanks!

---

### Post by c2tarun on 2013-03-18
Isn't that a bad idea for a computer which doesn't shuts down frequently? Suppose I need to burn a DVD it'll store everything in /tmp I guess. Also if burning takes lot of time and meanwhile I started my virtual box and start playing Scrabble on WinXP then it'll need more RAM. This will cause SWAP partition to be used, too much swap, system heat up and slow. I may be wrong, but if anyone can explain please share that how is mounting /tmp to RAM is going system's performance.

---

### Post by vanadium on 2013-03-18
If you have plenty of RAM and hardly ever need SWAP, then /tmp in RAM may speed up applications that use /tmp to write temporary data. If you end up in a scenario where lots of /tmp data is written, and you are running a lot of processes, then indeed it will have a negative impact, because swap kicks in earlier than if /tmp would not have been in RAM.

---

### Post by rnerwein on 2013-03-18
> **Wtwine said:**
> Hi 

I moved /tmp to RAM to improve performance by adding the following to fstab:

```
# Move /tmp to RAM
tmpfs /tmp tmpfs defaults,noexec,nosuid 0 0
```

However, this turned out to be a bad idea for me (poor performance and can't install some packages in R because of the way it uses /tmp), so I want to move /tmp back to root.

How do I do that?

The following link refers with same query posted by somebody else (but no answers): [http://ubuntuforums.org/showthread.php?t=1158145](http://ubuntuforums.org/showthread.php?t=1158145)
hi
your problems are the mount options. ---> nosuid, noexec .... will never work for /tmp. the idea is OK but you have to look at the permissions (example: some aps are looking not only for the user and group - they are evem looking for the permissions - especially for the t (is the sticky bit) bit is set.
ciao

---

### Post by Wtwine on 2013-03-20
After I moved /tmp back to root, I have hit another snag.
Today I did an update, and when I did dist-upgrade, I got this error message:
> mount: /tmp not mounted or bad option
E: Problem executing scripts DPkg: Pre-Invoke 'mount -o remount,exec /tmp'
E: Sub-process returned an error code
Why is /tmp not mounting when I boot, and how do I resolve this?

---

### Post by dino99 on 2013-03-20
thats simple, ubuntu settings does not know about your choice. Changing the default settings need a bit more than moving /tmp :(

---

### Post by schragge on 2013-03-20
IIRC, dpkg caches preinst/postinst scripts in */tmp* and launches them from there. If */tmp* is on a separate partition and mounted *noexec*, the partition needs to be remounted *exec* by APT before invoking dpkg. When you were moving /tmp to RAM, you probably added something like this in */etc/apt/apt.conf* or in some file under */etc/apt/apt.conf.d/*:
```

DPkg::Pre-Invoke {"mount -o remount,exec /tmp";};
DPkg::Post-Invoke {"mount -o remount /tmp";};

``` Since your */tmp* isn't on a separate partition anymore, remove these lines from the file.

It's also a good idea to make */tmp* world-writable, but set the restricted deletion flag:
```
sudo chmod +rwxt /tmp
```

---

### Post by Wtwine on 2013-03-20
After deleting those lines in apt.conf, I managed to upgrade successfully after rebooting.  I also changed the permissions on /tmp as advised.
Thanks!

---

### Post by Wtwine on 2013-03-21
Not so fast! It seems I am still having issues  with mounting /tmp.  Some applications that use /tmp are still not  working properly after moving /tmp back to root.  When I moved it to  RAM, it was with noexec option, so after moving it back to root I tried to remount in root with exec,  but got the following error:

```
sudo mount -o remount,exec /tmp
mount: /tmp not mounted or bad option
```

Why is this, and how do I fix it?

In case this is helpful, > df returns:

```
tmpfs             698584      912    697672   1% /run
```

And the tmpfs line in /proc/mounts is as follows:

```
tmpfs /run tmpfs rw,nosuid,relatime,size=698584k,mode=755 0 0
```

Any advice would be greatly appreciated!

---

### Post by schragge on 2013-03-21
As */tmp* is now just a directory on the root partition, the only way to mount it is with *mount --bind*. But your root partition (/) is already mounted *exec*, so there's no point in trying to remount */tmp* with this option.

If applications still have problems with */tmp* then check its permissions and ownership:
```
namei -l /tmp
```

---

### Post by Wtwine on 2013-03-21
Ok.  This is the output I get:
```
namei -l /tmp
f: /tmp
drwxr-xr-x root root /
drwxrwxrwt root root tmp
```

Does this look right?

---

### Post by schragge on 2013-03-21
Yes, it's the same on my system. What applications still have problems with your */tmp* setup, and what error messages do you get?

---

### Post by Wtwine on 2013-03-21
Well, for one, xscreensaver carousel which displays pictures from a folder under /Documents, no longer shows pictures since moving /tmp back to root - just the screensaver logo in place of the pictures.  I assume this is because it uses /tmp for displaying the images in the rotating carousel.

---

### Post by schragge on 2013-03-21
So, where does *carousel* get its images from? I believe you can configure it with *xscreensaver-demo* and it will save configuration data in *~/.xscreensaver*. You can see what image file xscreensaver is going to use with
```
xscreensaver-getimage-file --name [COLOR=blue]directory[/COLOR]
```

---

### Post by Wtwine on 2013-03-21
Yes, I have set the directory in the xscreensaver GUI as /home/<user>/Pictures.  It worked fine before I tampered with /tmp/.

---

### Post by Wtwine on 2013-03-21
Ok, problem solved.  I discovered that somehow a /tmp directory with root permissions had been created in the my user directory, in addition to the one in root.  Don't know how that happened, but when I deleted it, to screen saver problem disappeared.

---

