---
title: "boot kind of fails - all messages say primary filesystem read-only"
date: 2007-08-12
forum: General Help
---

### Post by shuffdog on 2007-08-12
I was playing planarity, and I was about to solve a level when a everything froze, numlock key, mouse, screen and everything, and the virtual terminals weren't coming up.  I let it go for awhile, but I eventually cold booted, and since then every boot has given me errors like
*fatal server error:  could not create lock file in /tmp/.tX0-lock*
and a lot of
*/usr/bin/startx: line 132: cannot create temp file for here document: read-only filesystem*
It ends up in a Gnome Display Manager error screen, where i can press a key and get a terminal.

My only clue so far is that, the root filesystem is read-only.

I have tried putting in **mount -n -o remount, rw /** because of a suggestion to do that, here:
[http://ubuntuforums.org/showthread.php?p=2301520](http://ubuntuforums.org/showthread.php?p=2301520)
That technically worked, and I can start X and all that, but after rebooting it keeps coming back as read-only again.

if i put in **mount** it always gives me this for root:
```
/dev/sdb5 on / type ext3 (rw)
```
the fstab entry (too lazy to type the UUID) is this:
```
<filesystem> <mount point> <type> <options>                            <dump> <pass>
#/dev/sdb5
UUID= ...    /             ext3   defaults,noatime,writeback=false,rw  0      3
```
and the mtab entry is this:
```
/dev/sdb5 / ext3 rw 0 0
```

I have run memtest86+ because this guy seemed to have luck with that:
[http://ubuntuforums.org/showthread.php?t=77593](http://ubuntuforums.org/showthread.php?t=77593)
but nothing turns up.

And I kind of want this to be over : (
Anybody know what else I should try?

---

