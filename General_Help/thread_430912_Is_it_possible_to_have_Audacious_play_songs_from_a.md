---
title: "Is it possible to have Audacious play songs from a SMB share?"
date: 2007-05-02
forum: General Help
---

### Post by Scotty562 on 2007-05-02
I have my xbox setup as network attached storage and I can play songs through Rhythembox, but when I try to play a song from the SMB share on the xbox it gives me an error.  Does audacious simply not support this or am I missing something?

---

### Post by Theimon on 2007-05-05
What's the error message?

---

### Post by Scotty562 on 2007-05-05
Unable to play files

The following files could not be played. Please check that:
1. they are accessible (they are, I can play them with Rhythembox)
2. you have enabled the media plugins required.

---

### Post by DagMan on 2007-05-05
Is Rhythmbox also playing them over the samba share?

Also, If it's any help, I can play songs from a network mounted sshfs using audacious as well as watch video using mplayer.  If samba isn't working out for it, then maybe the xbox can use sshfs or something else that will work for it.

---

### Post by Theimon on 2007-05-05
> **Scotty562 said:**
> Unable to play files

The following files could not be played. Please check that:
1. they are accessible (they are, I can play them with rythembox)
2. you have enabled the media plugins required.

Does Audacious have the right codecs/plugins to play the files?

---

### Post by Scotty562 on 2007-05-05
> **DagMan said:**
> Is Rhythmbox also playing them over the samba share?

Also, If it's any help, I can play songs from a network mounted sshfs using audacious as well as watch video using mplayer.  If samba isn't working out for it, then maybe the xbox can use sshfs or something else that will work for it.

Yes, Rhythembox is playing over the samba share.  I have no idea what shfs is, I'll have to look into it. I can watch videos over the share as well. The xbox is running a modified version of Debian which makes me feel that it isn't so much the xbox's fault. Rather, it's my fault for not having the software set up correctly. Thanks for the info, I think you're on the right track.

> **Theimon said:**
> Does Audacious have the right codecs/plugins to play the files?

I think so, if I copy the music file from the share onto my desktop it will play it.

---

### Post by DagMan on 2007-05-07
Everything indicates that your codecs are fine then.  It's sort of a strange problem though, perhaps if you see some buffer settings in Audacious then messing around with them will make a differance.

sshfs is a network filesystem not too unlike samba.  It's a network filesystem using ssh to send the data.  That you're having this problem though, I'm not sure using sshfs would make a differance as it's going to also end up being a mount point for another computer's stuff.  It requires kernel support and if you want to try it it may very well be already compiled in... I don't know much about debian let alone linux running on other platforms.  I recall that previously just enabling support and compiling the kernel was fine but that I ran into a problem and most recently I googled the project page and found that the module can be compiled by itself without a kernel recompile.  Additionally a fuse group is created and you'de have to add your user to it and log them out and back in.  You'de be googling for the fuse module by the way.  Don't know if these search links expire or not [http://ubuntuforums.org/search.php?searchid=19650525](http://ubuntuforums.org/search.php?searchid=19650525)

...In case you want to try but like I said, it seems that if you have problems with the one way then the other probably won't solve it.  It sounds more like Audacious has a limitation.

---

### Post by Farhan on 2007-10-06
> **Scotty562 said:**
> Unable to play files

The following files could not be played. Please check that:
1. they are accessible (they are, I can play them with Rhythembox)
2. you have enabled the media plugins required.
i seem to have the same problem with audacious. did anyone figure it out? like other mp3 files are playing fine and files on samba are being played with totem and rhythmbox. weird really. maybe audacious doesn't support file supported over samba network?

---

### Post by mondscheinkind on 2007-12-08
i have the same problem and have no idea to get it solved... that makes no fun..

---

### Post by Scotty562 on 2007-12-09
I never did find a solution :(. I just stopped using Audacious and started using Rhythmbox.

---

### Post by ericdegen on 2007-12-11
I'm intrigued - I have never been able to get any file player (rhythmbox, vlc, etc) to play over SMB shares on the desktop "connect to server" option, but if I mount them in the fstab via smbfs the same file plays.

I'm connecting to a Buffalo Tera station, and some windows servers. Right now this is just an irritating problem, but I's love to have a solution.

---

