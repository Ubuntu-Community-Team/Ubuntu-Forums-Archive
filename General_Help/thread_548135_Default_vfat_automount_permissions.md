---
title: "Default vfat automount permissions"
date: 2007-09-10
forum: General Help
---

### Post by ignavia on 2007-09-10
Yeah, yeah, I know, I should search. I did. And I found [this](http://ubuntuforums.org/showthread.php?t=129132). But it's not helping me.

Like the other posts I saw, I want to copy my photos to my PC and share them over the network. Problem is, they always copy as 700, because that's what vfat is mounting with as default. All I want to do is make vfat mount with 755 instead.

I tried an entry in fstab. My SD reader is sde, so I put an entry in fstab with /dev/sde1 mapping to /media/sdcard (though /media/disk-# was fine by me) with umask 022. I created the directory as root and chmodded it 777. After doing that, it ignores the fact that I inserted the card at all. Well, I can see the card in dmesg, but no automounting is occurring. 

What next?

---

### Post by ignavia on 2007-09-10
A solution... for me at least.

Went back to normal (removed fstab entry). Mounted card normally. Places -> Computer. Right-click SD reader and Properties, Volume tab, Settings, added "umask=022" to the 'mount options' box. Unmounted and remounted and voilà.

Now, this is an internal card reader that is never removed, and it is a per-card setting. If I were a professional photographer with a wallet full of cards, I'd have to set this on each.

Also, if you're using a removable card reader, like your camera, I don't know if it'll work.

Joe

---

