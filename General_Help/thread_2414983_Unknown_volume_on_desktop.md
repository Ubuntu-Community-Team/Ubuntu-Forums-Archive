---
title: "Unknown volume on desktop"
date: 2019-03-18
forum: General Help
---

### Post by Syncope on 2019-03-18
Hi, this may not be a big deal, but in Xubuntu 18.04 and now 18.10, occasionally I see a wild volume randomly popping out on my desktop (see img). It always just says volume and size, which varies from time to time but is always around XXX KB. I'm just curious what might be causing that, because I don't remember encountering this with older releases, yet I saw this on both of my laptops in recent past. It's just little unsettling. Should I be worried? Is it just some kind of cache? Could it be hackers? Could it be the governments? 
[IMG][IMG]https://i.imgur.com/57XDgRf.png[/IMG][/IMG]

---

### Post by Dennis N on 2019-03-18
It's an icon for what Xubuntu considers as a "Removable Device" which includes partitions that are not mounted in fstab but could be manually mounted in the file manager, and USB sticks you plug in. 4.1 kB is rather small, so hard to tell what it is. You could open it and see what you find.

---

### Post by Syncope on 2019-03-18
I am well aware of what that icon stands for, as I'm naturally using removable devices. I'm just saying it makes no sense to me, as no devices were plugged in. When I try to mount it, there's simply an error message saying "Failed to mount "Volume". The given volume was not found".

---

### Post by vidar-vidnes on 2019-03-29
Hi

I have the same issue and opened a similar thread app. at the same time, [https://ubuntuforums.org/showthread.php?t=2415085](https://ubuntuforums.org/showthread.php?t=2415085)
 Have you found an solution?

did a few log checks but could not find any solution.

---

### Post by npkala888 on 2019-09-12
Had the same issue on my xubuntu 19.04. Here is how it disappeared for now, in desktop settings, icons tab, select show hidden icons and it just disappears!

---

### Post by demesmaeker2 on 2019-12-12
Same issue here.
Icon name => "4.1 KB Volume"
xubuntu 19.10
 **[[COLOR=#000000]npkala888[/COLOR]]("https://ubuntuforums.org/member.php?u=1574861")**[[COLOR=#000000][/COLOR]]("https://ubuntuforums.org/member.php?u=1574861") method fixed the issue.
I installed tens of new packages lately, so I'm not sure which one is related to the intruding Icon (if any).

---

### Post by barryp3uk2 on 2020-04-15
Hi,

I have this since I did a clean install of 20.04 beta  from 18.04.

"4.1KB Volume" It can't be mounted or opened. Same error message: "Failed to mount "Volume". The given volume was not found"

**[[COLOR=#000000]npkala888[/COLOR]]("https://ubuntuforums.org/member.php?u=1574861")'s** method also worked for me. Thanks!

---

### Post by ledlamp on 2020-04-23
It's because of snapd!

Snap packages are mounted as loop devices from squashfs files. It seems when a package is updated, the old loop device is left unmounted and Xfce shows this unmounted device on your desktop.

Snap packages are updated automatically which is why these seem to randomly appear over time.

I am interested in a solution to make Xfce not display these unmounted loop devices. This might be a snap issue, maybe it fails to delete the old loop devices sometimes. I just tested by installing a snap ("hello"); it was mounted from /dev/loop9. Then I removed it, and a volume flashed on the desktop for a moment. I think this was during the time between the loop device being unmounted and then deleted; /dev/loop9 doesn't appear in lsblk anymore. But I have this "96 MB Volume" which is /dev/loop5 and not mounted to anything, so for whatever reason snapd didn't delete this block device when it automatically updated whatever it was for.

---

### Post by coffeecat on 2020-04-23
Back to sleep, old thread.

@ledlamp, it's not clear whether you are offering a solution, or asking a question. If you need help, please start your own thread. This stale thread has long been abandoned by the OP.

---

