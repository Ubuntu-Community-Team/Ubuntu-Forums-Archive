---
title: "When do mounted filesystems count for the space?"
date: 2013-05-18
forum: General Help
---

### Post by Carllacan on 2013-05-18
Hi!

I wasn't sure of how to ask this, so the title is a bit confusing, sorry.

My question iis as follows: I mounted, on /mnt two filesystems. One was a big NTFS and the other a not-so-big ext4. Inmediatly I received a warning telling me that the free space on / was running out. I realized that this was because it was counting the files on the mounted ext4 filesystem as part of /. Strangely, however, this didn't happen with the NTFS filesystem, nor it happened when I unmounted both of them and mounted them again on / (instead of in /mnt).

So, just out of curiosity: why did it just happen when the ext4 mounted on /mnt and not with the NTFS or the two of them on /?

Thank you.

PD: Suggestions on how to better phrase the question in the title would be thanked.

---

### Post by prodigy_ on 2013-05-18
Really sorry, but about half of your post doesn't make sense. You can't use the same directory (/mnt) as the mount point for two different file systems simultaneously. Likewise, you can't use / as the mount point for anything but root file system which is already mounted by the time you log on.

Could you remount those file systems somewhere and then post the output of **mount** and **df -h** commands?

---

### Post by mcduck on 2013-05-18
The files on mounted filesystems *do not count* as used space on your root filesystem. (just like the available space on mounted filesystem doesn't increase the available space on root)

There probably is some other explanation for the warning you got. Are you absolutely sure it was about /, and not about one of the filesystems you mounted. Also ow large is your root, and as prodigy_ mentioned, since you can't mount two filesystems into same location could you clarify the details a bit?

(Also, at least on some older Gnome version, Gnome's own disk usage warnings *did* falsely account the size of ~/.gvfs into used space, although that would only apply had your drive been automounted by Gnome and not by yourself. )

---

### Post by Carllacan on 2013-05-19
Yeah, sorry, I did an incredibly poor explanation. When I said they were mounted on / i meant that their mountpoints were on /, namely they were /DATA and /common. My apologies for the confusion.

Now, look at this:

[IMG]http://s2.subirimagenes.com/imagen/8444763screenshot-from-2013.png[/IMG]


According to that, the size of / is almost 400 gb, when actually on / there is mounted a 10 gb partition. And, inside /, there is a 500 gb fs mounted on /DATA, which should be counted apart from /, isn't it? And, by the way, /tmp and /boot are also partitions independent of /, so they shouldn't be listed there either.

And even if it is just Gnome falsely reporting /DATA as part of / I'm getting "Root filesystem is running out of space" warnings and other problems, such as Dropbox not being refusing to sync due to lack of space. What can I do?

Thank you, everyone.

---

### Post by prodigy_ on 2013-05-19
GUI apps are great for regular work but garbage for troubleshooting. Like I said before, you should open terminal and run some commands:
```
sudo parted -l # the list of all partitions on all local drives
mount # the list of all currently mounted file systems
df -h # total free and used space for all mounted file systems
```

Post the output here if you'll still have any questions.

---

### Post by mcduck on 2013-05-19
You really should't use the disk usage analyzer for this kind of purposes, it's intended for analysing *where* the disk space is being used, not how much available space there is on a specific filesystem.

It is possible to use it to check a certain filesystem, but to do that you must make sure you only scan that one filesystem, not the whole root, and that you exclude any mounted volumes, network drives etc from the scan. Simply using a tool such as "df" from command line, or the System Monitor if you want a GUI, would be much easier way to get the information you are looking for.

edit: also you only posted a thumbnail of the scan results, so its impossible to figure out what's going on there. Just run "df -h" in a terminal for better view of used/available space on each of your drives and partitions.

---

