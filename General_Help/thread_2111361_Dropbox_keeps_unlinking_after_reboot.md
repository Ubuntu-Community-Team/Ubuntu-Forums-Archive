---
title: "Dropbox keeps unlinking after reboot"
date: 2013-02-01
forum: General Help
---

### Post by lekevinio on 2013-02-01
Hi,

I'm having a problem with Dropbox.

I have the following setup

1 HDD
4 partitions:
Linux, Swap, Windows, Data (ntfs)

I have my dropbox folder on /media/kingkong/Data/Dropbox
Every time I reboot Ubuntu Dropbox says that the Dropbox link is missing and I need to relink it.

I don't want to have Dropbox in my Home folder because windows can't find it than.

I've tried to create a link of /media/kingkong/Data/Dropbox to /home/kingkong/Dropbox but then it says that the system link is broken after I restart my system.

Any idea?

---

### Post by Enigmapond on 2013-02-01
I always had DropBox issues. I suggest you use instead. Ubuntuone...much more stable and sync's very well. Just a suggestion..:)

---

### Post by LewisTM on 2013-02-01
Something like that happened to me recently. Dropbox would ask for linking the computer at every login.

The solution was to wipe to user installation of Dropbox. Dropbox silently installs itself in your home folder, you need to delete that, things like [FONT="Courier New"]apt-get remove dropbox[/FONT] won't work. The following terminal commands solved it.
```
dropbox stop
rm -rf ~/.dropbox*
dropbox start -i
```
Dropbox setup and linking should start, hopefully for the last time.

Cheers!

---

### Post by lekevinio on 2013-02-02
> **Enigmapond said:**
> I always had DropBox issues. I suggest you use instead. Ubuntuone...much more stable and sync's very well. Just a suggestion..:)

I want to use Dropbox because me and some of my classmates have a shared folder. And my Android phone uploads all the photo's and movies to it. And I would love to keep that. And I already have 10 GB storage for free, by sharing folders.


> **LewisTM said:**
> Something like that happened to me recently. Dropbox would ask for linking the computer at every login.

The solution was to wipe to user installation of Dropbox. Dropbox silently installs itself in your home folder, you need to delete that, things like [FONT="Courier New"]apt-get remove dropbox[/FONT] won't work. The following terminal commands solved it.
```
dropbox stop
rm -rf ~/.dropbox*
dropbox start -i
```
Dropbox setup and linking should start, hopefully for the last time.

Cheers!

I just tried this and at first it looked like it was working. But once again it says that the link is missing. :(
I can relink it every single time but if it could do it automatically that would be great.
Maybe by using a login script?

---

### Post by ejstans on 2013-02-17
I had a similar problem, it looked like the disk wasn't mounted when Dropbox looked for it.

I followed the steps here to mount the disk on startup and the error stopped
[https://help.ubuntu.com/community/AutomaticallyMountPartitions]("https://help.ubuntu.com/community/AutomaticallyMountPartitions")

---

### Post by lekevinio on 2013-02-21
> **ejstans said:**
> I had a similar problem, it looked like the disk wasn't mounted when Dropbox looked for it.

I followed the steps here to mount the disk on startup and the error stopped
[https://help.ubuntu.com/community/AutomaticallyMountPartitions]("https://help.ubuntu.com/community/AutomaticallyMountPartitions")

Thanks :)
I'm going to try the Systemwide Mounts this weekend.
Looks great. :D

---

### Post by TechGeekT on 2013-04-05
> **ejstans said:**
> I had a similar problem, it looked like the disk wasn't mounted when Dropbox looked for it.

I followed the steps here to mount the disk on startup and the error stopped
[https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)


GOD guided me straight to your answer. Thanks so much!! That helped. Dropbox is no longer asking me to relink.

---

