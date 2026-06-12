---
title: "Proper way to mount external drives in fstab?"
date: 2014-08-25
forum: General Help
---

### Post by raptir on 2014-08-25
I am using Plex media server and have an external drive that is formatted NTFS. Initially, Plex could not see the drive as the system only gave access to my user account and those permissions could not be changed since it is an NTFS disk. I figured out how to get the drive working with Plex by explicitly identifying the device in my fstab with the *permissions* option. It works great, but this is a laptop that does not always have the external drive connected. When I boot without the drive connected, the system delays boot while it waits for the drive and I have to hit *s* to skip.

I have read a couple different opinions on how to remedy this situation, and I'm wondering what is the "correct" way to do so.

[LIST]
[*]Add the option *noauto*. This would require manual mounting but that wouldn't be the end of the world since I could just stick a script on my desktop.
[*]Add the option *nofail*. I'm not completely sure what this does.
[*]Add the option *nobootwait*. This sounds like it does what I need it to, but I read a post that specifically said not to do this as it could cause serious issues during boot.
[/LIST]

My ideal situation would be that...

[LIST=1]
[*]The system would not delay boot if the external drive is not connected
[*]The disk would still automount if it was connected during boot
[*]The disk would still automount if it was connected after the system was already online
[/LIST]


What would be the best way to achieve this?

---

### Post by nerdtron on 2014-08-25
> **raptir said:**
> 

I have read a couple different opinions on how to remedy this situation, and I'm wondering what is the "correct" way to do so.

[LIST]
[*]Add the option *noauto*. This would require manual mounting but that wouldn't be the end of the world since I could just stick a script on my desktop. 
[*]Add the option *nofail*. I'm not completely sure what this does. 
[*]Add the option *nobootwait*. This sounds like it does what I need it to, but I read a post that specifically said not to do this as it could cause serious issues during boot. 
[/LIST]



If you have another external disk formatted with NTFS (even a usb thumbdrive), and you know the syntax on the fstab, why not try each of these options and see if they works. There's no harm in experimenting when you have no data to lose.

---

### Post by sotiris2 on 2014-08-25
Why don't you show us the post where it said nobootwait can cause serious issues during boot? My undestanding is that this would be the case if set for a partition that is actually used in the boot process since it wouldn't wait for it. Also there can be an issue with fsck. Basically with nobootwait it may not wait for fsck to finish checking the disk and continue booting, causing some programs to fail. But since this is an ntfs partition I don't think this can happen (fsck doesn't do ntfs) and even for ext4 partitions you can disable checking by setting the last number in the entry to 0.

---

### Post by CaptainMark on 2014-08-26
If I get what you're saying (the system won't boot when the drive isn't plugged in because it's listed in the fstab) then you just need to use the noauto option in the fstab entry, this won't stop it from automounting, it means that the drive is mounted how fstab tells the system to do it, only if it's present and ignore it if it isn't.

From the fstab 5 man page ```
noauto do not mount when "mount -a" is given (e.g., at boot time)
```

---

### Post by raptir on 2014-08-26
> **sotiris2 said:**
> Why don't you show us the post where it said nobootwait can cause serious issues during boot? My undestanding is that this would be the case if set for a partition that is actually used in the boot process since it wouldn't wait for it. Also there can be an issue with fsck. Basically with nobootwait it may not wait for fsck to finish checking the disk and continue booting, causing some programs to fail. But since this is an ntfs partition I don't think this can happen (fsck doesn't do ntfs) and even for ext4 partitions you can disable checking by setting the last number in the entry to 0.

[http://askubuntu.com/questions/14365/mount-an-external-drive-at-boot-time-only-if-it-is-plugged-in](http://askubuntu.com/questions/14365/mount-an-external-drive-at-boot-time-only-if-it-is-plugged-in)

It was in the second answer here. Since it was in a question about external drives I assume it was relevant, but he obviously could have been misinformed. 

> **CaptainMark said:**
> If I get what you're saying (the system won't boot when the drive isn't plugged in because it's listed in the fstab) then you just need to use the noauto option in the fstab entry, this won't stop it from automounting, it means that the drive is mounted how fstab tells the system to do it, only if it's present and ignore it if it isn't.

From the fstab 5 man page ```
noauto do not mount when "mount -a" is given (e.g., at boot time)
```

Interesting. The way I read the man page I thought noauto would not mount at boot time (since it says "do not mount... (e.g., at boot time) ;)). It looks like noauto is the way to go. It still mounts if it is connected but does not delay startup if it is not. It will also automount correctly when plugged in. Thanks!

---

### Post by CaptainMark on 2014-08-26
I've used this for ages with no problems, I think it means (but I'm not 100%) the system will not automount it at boot but your desktop manager will be independent from this option, so when you log in, the file manager will still attempt to mount it.

---

