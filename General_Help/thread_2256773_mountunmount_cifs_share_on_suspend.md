---
title: "mount/unmount cifs share on suspend"
date: 2014-12-14
forum: General Help
---

### Post by anorthernsoul on 2014-12-14
I've got a computer running Ubuntu 14.04. I use it mostly as a video player, so when I'm not using it I'd prefer it to suspend. The problem comes when I bring it back up and the cifs share isn't available. According to this Ask Ubuntu question ([http://askubuntu.com/questions/363688/nautilus-hangs-up-on-mounted-shares-after-suspend](http://askubuntu.com/questions/363688/nautilus-hangs-up-on-mounted-shares-after-suspend)) the best way to deal with this is to unmount when going down and remount when coming back up. I made some alterations to the script provided and ended up with this:
```
#!/bin/sh
#My custom script


case "$1" in
        hibernate|suspend)
                #umount shares
                /bin/umount -t cifs -a
                ;;
        thaw|resume)
                #mount shares
                 mount -a
                ;;
        *) exit
                ;;
esac

```

I named it 99custom, put it into the /usr/lib/pm-utils/sleep.d/ folder and made it executable, but I'm having some problems with it. It actually keeps the computer from suspending. The screen goes blank for a second but comes back and the network goes down but then reconnects. Those are the only two visual cues I can see. It seems to actually run the commands, but it's hard to judge just what's going on because I'm not sure about whether it's actually suspending or not. As it seems to execute the commands in either descending or ascending order depending on whether it's coming up or going down I've changed the name and broken it up into two scripts that just do the mounting or unmounting, but no matter what I do or what order I put them in the result is the same. Is this the proper way to deal with this problem, and what am I doing wrong? Any help would be greatly appreciated.

---

### Post by papibe on 2014-12-14
Hi anorthernsoul. Welcome to the forums ):P

My guess is that there may be still processes that are using the file system, so the umount command tries to unmount, but either get 'system busy' or timeout.

If you know there's no important process that is using the share (e.g. a backup), you may try to "force" the umount by using the -f option:
```
/bin/umount -t cifs **[COLOR="#FF0000"]-f[/COLOR]** -a
```
Hope it helps. Let us know how it goes.

Come here often and have fun.
Regards.

---

### Post by anorthernsoul on 2014-12-14
Thanks for the help and the warm welcome papibe. Unfortunately your suggestion hasn't helped. It's still keeping me from suspending.

---

### Post by Kljuka on 2014-12-26
Hi anorthernsoul. I've been having the same problem for a loooong time and still haven't found a solution. You can check it here (maybe you find a solution):
[http://ubuntuforums.org/showthread.php?t=2224655](http://ubuntuforums.org/showthread.php?t=2224655)

I really hope you (and I) find a solution to that problem.

It seems others are also having this problem:
[http://askubuntu.com/questions/417874/cifs-vfs-server-xxx-has-not-responded-in-120-seconds](http://askubuntu.com/questions/417874/cifs-vfs-server-xxx-has-not-responded-in-120-seconds)

---

### Post by anorthernsoul on 2015-01-12
Unfortunately I haven't been able to find a solution for my issue. This was a deal breaker for this computer, so I had to go back to Windows.

---

