---
title: "root thunar doesn't show unmounted partitions in side panel like user thunar does."
date: 2014-04-04
forum: General Help
---

### Post by Dreamer Fithp Apprentice on 2014-04-04
Thunar started as an ordinary user shows unmounted filesystems in the side panel. Click on them and they are mounted automatically and then opened. No password required. I like that.

Thunar started as root doesn't show unmounted filesystems in the side panel at all.

I didn't see anything special in /home/user/.config/thunar to account for this and I haven't put anything about mount sans password in /etc/sudoers. The filesystems are not listed in fstab. This is 13.10 using plain Openbox.

So why is this?  And more importantly, how can I make thunar as root behave the same way thunar as user does?

---

### Post by xeonix on 2014-04-04
check the process gvfs-gdu-volume running?

```
ps -e | grep gvfs-gdu-volume
```[FONT=Ubuntu Mono]
[/FONT]

---

### Post by Dreamer Fithp Apprentice on 2014-04-04
Thank you, Xeonix. In lxterminal, both```
ps -e | grep gvfs-gdu-volume
```and```
sudo ps -e | grep gvfs-gdu-volume
```only return a new prompt.

The thing that really puzzles me is neither the behaviour of thunar as user, nor thunar as root, but that, not only are they not the same, it's the user invoked thunar that seems to have added powers. Seems backwards.

FWIW, I just tried copying /home/j/.config/Thunar/accels.scm over /root/.config/Thunar/accels.scm and rebooting. That didn't make any difference that I've detected. Does thunar hide any other config files anywhere?

And starting thunar in a terminal, plain or with either sudo or gksudo and then closing it with a mouse click to the x in the title bar shows no error messages in the terminal:```
me@saucy:~$ sudo thunar
[sudo] password for me: 
me@saucy:~$ thunar
me@saucy:~$ gksu thunar
me@saucy:~$
```

udisks does not appear to be installed because:```
me@saucy:~$ sudo apt-get install udisks
[sudo] password for me: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  liblvm2app2.2 libsgutils2-2
Suggested packages:
  sg3-utils mdadm
The following NEW packages will be installed:
  liblvm2app2.2 libsgutils2-2 udisks
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 588 kB of archives.
After this operation, 2,145 kB of additional disk space will be used.
Do you want to continue [Y/n]? n
Abort.
me@saucy:~$
```

and gnome-mount isn't in the repository, so I'm not sure how user's thunar is doing this.

---

### Post by steeldriver on 2014-04-04
Does thunar use gvfs? I thought it had its own removable volume management subsystem (thunar-volman)

FWIW I don't think it's a thunar thing particularly - afaik nautilus behaves the same. The whole idea behind these 'user mount' addons is to allow non-root users to mount local removable drives (including local hard drives / partitions) on the *local *desktop. In the case of gvfs-mount, the daemon runs in userspace and root doesn't even get read permission to the resulting mount point.

---

### Post by Dreamer Fithp Apprentice on 2014-04-04
Thanks, Steeldriver.
> **steeldriver said:**
> Does thunar use gvfs? I thought it had its own removable volume management subsystem (thunar-volman) . . .  In the case of gvfs-mount, the daemon runs in userspace and root doesn't even get read permission to the resulting mount point.It doesn't seem to work that way for me, so I suppose that is evidence you are correct in saying gvfs-mount isn't used. I say it doesn't work that way for me because if I click on the link for an unmounted partition in user's thunar, in addition to mounting the partition under /media/username/partition-label (and, I suppose, creating the /media/username and /media/username/partition-label directories along the way) and opening it, the link instantly appears in root's thunar as well. It seems as if only user's thunar can see the unmounted partitions but once mounted, root's thunar can see and access them as well, seeing them in the same mountpoint - /media/username/partition-label. There is a directory /media/root but it is empty.

Been reading a bit elsewhere so I decided to check on udisks2. Seems I DO have that installed. But```
ps -e | grep gvfs-udisks2-volume
```and```
sudo ps -e | grep gvfs-udisks2-volume
```still just return a prompt.

Could it be I need to add root to some group?

I'll read up on this "thunar-volman" a bit. Maybe that will suggest something.
Synaptic says it IS installed.

==============
Funny, I thougt I'd posted this but I don't see it. So:

I also tried this on the strength of analogy:```
me@saucy:~$ ps -e | grep thunar-volman-udisks2-volume
me@saucy:~$ sudo ps -e | grep thunar-volman-udisks2-volume
[sudo] password for me: 
me@saucy:~$
```but as you can see it got the same result.

In searching for possibly relevant information I've found that thunar has some "hidden settings". Oh, lovely. I just hate obscurantism. Anyway, the way to access them appears to be through xfce4-settings-editor, a part of the xfce4-settings package. So I installed that and invoked the editor as root. Everything that seemed like it could possibly be relevant was already enabled.

I found an old bug, marked fixed, at launchpad, that was similar. So I reported this there, since it's beginning to seem like a bug rather than a bad setting. I thought it was going to be a Thunar bug but it showed up as a Ubuntu bug. Anyway, it's here:
[https://bugs.launchpad.net/ubuntu/+source/thunar/+bug/1302875](https://bugs.launchpad.net/ubuntu/+source/thunar/+bug/1302875)

If anyone else experiences this or something very similar, I'd appreciate it if you'd stop by that page and click the "Does this bug affect you?" link, etc. They don't tend to take bugs reported by only one person very seriously. Thanks.

But that doesn't mean I'm giving up on finding a work-around if anyone has
suggestions.

---

