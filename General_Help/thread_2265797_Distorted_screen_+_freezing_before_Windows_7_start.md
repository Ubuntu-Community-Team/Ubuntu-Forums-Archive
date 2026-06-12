---
title: "Distorted screen + freezing before Windows 7 startup?"
date: 2015-02-17
forum: General Help
---

### Post by michael260 on 2015-02-17
Hello all.
Recently I installed Ubuntu alongside Windows 7 Home Premium, and the first time I did this, Windows 7 froze at the launcher with a very distorted screen[See the attached image]. So I had to completely reinstall Windows 7, I attempted to install Ubuntu again, and everything is working fine now, but my question is, is it possible that this scenario could happen again, and if so how would I prevent it, and finally my last question is what is this screen, or what is it caused by? 
Anything that has to do with this will be appreciated.
Thanks.
[Attached image]
[ATTACH=CONFIG]260050[/ATTACH]

---

### Post by nadarockyraccoon on 2015-02-18
Honestly, as long as you don't change the windows partition again everything should be fine. I've never run into this specifically, however I have had some issues with windows not liking it's partition to be resized, especially if it has a lot of data, you try to make it's partition too small, or it has a high level of fragmentation (most common cause). Some versions of XP Pro just break if the partition is resized regardless. If you do re install linux don't mess with the windows partition, just resize/delete the linux partition(s) and you shouldn't have any issues. As far as what this screen is, it looks like something ubuntu would do when the ati driver glitches out, but if you are sure you booted into windows it's just strange and I hope you never see it again.

---

### Post by michael260 on 2015-02-18
Thanks for the reply, but what I did was was completely wipe the hard drive, and then I reinstalled Windows and then Ubuntu, it seems to be working now, but I get that screen for a split second, but anyway, I won't be touching the Windows partition in the future.

---

