---
title: "Using Unison - a few questions"
date: 2016-06-13
forum: General Help
---

### Post by jub2 on 2016-06-13
I need to sync a few folders on my Ubuntu laptop with a few folders on my Windows desktop. 

I installed cifs-utils and unison-gtk, then mounted the Windows shared folders to a local mount point on the Ubuntu laptop:
```
[COLOR=#000000]sudo mount.cifs //winPC/documents/synced_files /mnt/winPC/synced_files -o user=jub2[/COLOR],uid=1000,gid=1000
```

I added "perms = 0" to the Unison preferences file.

This works for bi-directional syncing between folders.

Questions:
[LIST=1]
[*]I mounted the Windows shared folders to a local mount point because, as I understand it, without doing so, I would have to also run Unison on the Windows machine. Is this correct?
[*]If I have multiple Unison 'profiles' to sync, is there a way to batch them in the Unison GUI app? Or am I limited to selecting each profile individually and syncing?
[*]if I add the mount described in (1) to /etc/fstab, will this cause any issues when the Ubuntu laptop is started when not on the same network as the Windows desktop (i.e., when the mount cannot be executed)? If so, how to perform this mount automatically, but only when the Windows desktop is available on the same network?
[*]should the mounted Windows shared folders be umounted before shutting down the laptop, or does it not matter?
[/LIST]

Question 2 is pretty much resolved as I followed [this post's suggestion]("http://ubuntuforums.org/showthread.php?t=1623869&p=10152105#post10152105") to use symbolic links to the folders on both machines and edit the Unisom preferences file accordingly. Works great. 

Questions 3 and 4 are worked around because I created a script file that mounts the Windows shared folders, pauses while I run Unisom to sync, then unmounts the Windows shared folders.

---

