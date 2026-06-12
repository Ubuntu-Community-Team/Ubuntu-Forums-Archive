---
title: "Several Permissions Denied on Kubuntu"
date: 2007-11-01
forum: General Help
---

### Post by Sabretooth on 2007-11-01
I did a clean install of Kubuntu Gutsy and this problem has been plaguing me since. I've received several "Permissions Denied" errors. Here are the ones I can lay down right now:

1. I have an 80GB Windows Drive. To have it mount at startup, I added it to fstab and it worked, but after (I think) three restarts, it was gone. I'm sure it must be because of something I've done, though I don't know what! Now everytime I try to mount it, it's giving me a Permissions Denied error, even if I go through root (in Dolphin, I mean).
**Solved**: That was the result of some extra messing around in fstab. All clear now.

2. In Konsole, when I'm running a program via Terminal, I see this:
```
Error: "/var/tmp/kdecache-shirke" is owned by uid 1000 instead of uid 0.
Error: "/tmp/kde-shirke" is owned by uid 1000 instead of uid 0.
Error: "/tmp/ksocket-shirke" is owned by uid 1000 instead of uid 0.

```
shirke is my username, just so you know. There are several errors like this, and I haven't noticed a particular pattern in them.

3. Everytime I exit Dolphin, I see this:
> Unable to save bookmarks in /home/shirke/.kde/share/apps/d3lphin/bookmarks.xml. Reported error was: Permission denied. This error message will only be shown once. The cause of the error needs to be fixed as quickly as possible, which is most likely a full hard drive.

This is driving me nuts!

---

