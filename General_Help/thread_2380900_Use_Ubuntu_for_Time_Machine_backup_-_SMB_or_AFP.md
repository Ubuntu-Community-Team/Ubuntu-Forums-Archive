---
title: "Use Ubuntu for Time Machine backup - SMB or AFP ?"
date: 2017-12-23
forum: General Help
---

### Post by freeflyjohn on 2017-12-23
[B]Question:
[/B]Will Apple Time Machine work with Samba on Ubuntu 16.04 ?
[B]
Background:[/B]

I bought a Dell T30 server a few months ago have been playing around trying to set everything up.

I now have everything working (Network file sharing using SMB, SSH with keys, Remote Desktop using Screen Sharing, Plex Media Server, Nextcloud with https) with the exception of Time Machine.

I am now on my second Ubuntu installation attempt, during my first installation attempt I did have Time Machine working.

At that time I had SMB and AFP installed but I 'think' it was AFP that got Time Machine to work (my Mac OS was not up to date at this point).

This is the procedure I used to get AFP working with Time Machine...

[https://askubuntu.com/questions/516134/use-ubuntu-network-share-for-apple-timemachine-backups](https://askubuntu.com/questions/516134/use-ubuntu-network-share-for-apple-timemachine-backups)

For my second installation attempt I have only installed SMB but Time Machine is no longer seeing the network drive.

After Googling I cannot find a straight answer as to whether SMB will work with Time Machine and have read that AFP is being/has been phased out by Apple.

I have since updated my Mac OS which is now running macOS High Sierra 10.13.2 and my server is running Ubuntu 16.04.

My Samba version is 4.3.11-Ubuntu and I think the latest is 4.7.4, but I don't now how to update my Samba to the latest version (if this is the way to get Time Machine working with SMB?).

So should SMB work with Time Machine and if so how ?  If not, do I need to install AFP and will it work with my latest Mac OS and will it continue to work if AFP is being phased out ?

---

### Post by Opayq on 2018-01-12
Two weeks later, did you manage to get it working? Planning to use Ubuntu Server to host my Time Machine backups as well.

---

### Post by jakkuk on 2018-05-12
Long story short: you need Samba 4.8 due to new Apple extensions to SMB protocol. Read about fruit vfs extensions.

Howtos:
[http://jakkul.blogspot.com/2018/05/how-to-get-mac-time-machine-backups.html](http://jakkul.blogspot.com/2018/05/how-to-get-mac-time-machine-backups.html)
[https://www.reddit.com/r/homelab/comments/83vkaz/howto_make_time_machine_backups_on_a_samba/](https://www.reddit.com/r/homelab/comments/83vkaz/howto_make_time_machine_backups_on_a_samba/)

---

