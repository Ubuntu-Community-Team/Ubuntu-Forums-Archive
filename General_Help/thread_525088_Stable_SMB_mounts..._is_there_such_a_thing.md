---
title: "Stable SMB mounts... is there such a thing?"
date: 2007-08-13
forum: General Help
---

### Post by ipyakuza on 2007-08-13
Thanks to anybody reading this thread.  I have been facing a dilemma for quite some time now (a few years actually) regarding SMB mounts from linux to Windows Shares or CIFS NAS shares.  I am very fluent with mounting smb filesystems and have no problem accessing remote shares from a Windows host or a NAS that hosts CIFS shares.  The problem:  I can't ever seem to get a stable or consistently reliable mount that doesnt hang when I am streaming music.  From RH9, Ubuntu 6.06 to 7.04 across 4 different machines I run into this issue where the mount works, files are accessible but if I am streaming a file (such as viewing an image in a thumbnail viewer or playing music across the share and the app crashes it leaves my mount in a useless state unless i remount it.  I have done this between a Windows XP box to my linux box, a Windows 2000 box to my linux box and an Intel 4400 NAS to my linux box (CIFS shares).  I have tested with XMMS, mp3blaster, Amarok, Rythmbox, and a few others (cant remember which).  If i jump back and fourth between files too quickly it seems like there might be a caching issue or buffering issue over the smb mount that causes it to crash.  Sometimes (very seldom it happens on its own) just by playing music and not hopping around the playlist. I have done mount - smbfs, mount.cifs smb4k, fusesmb and none of them seem to work properly or remain stable.  Also compiled samba 3.0.25b from scratch to see if that helps but the release logs dont seem to show anything relating to fixing the issues I am running into.  I have also used different switches (to ensure its not my network gear / switch causing issues)  Any ideas???  Thanks in advance.

---

### Post by moffa on 2007-08-13
> **ipyakuza said:**
> Thanks to anybody reading this thread.  I have been facing a dilemma for quite some time now (a few years actually) regarding SMB mounts from linux to Windows Shares or CIFS NAS shares.  I am very fluent with mounting smb filesystems and have no problem accessing remote shares from a Windows host or a NAS that hosts CIFS shares.  The problem:  I can't ever seem to get a stable or consistently reliable mount that doesnt hang when I am streaming music.  From RH9, Ubuntu 6.06 to 7.04 across 4 different machines I run into this issue where the mount works, files are accessible but if I am streaming a file (such as viewing an image in a thumbnail viewer or playing music across the share and the app crashes it leaves my mount in a useless state unless i remount it.  I have done this between a Windows XP box to my linux box, a Windows 2000 box to my linux box and an Intel 4400 NAS to my linux box (CIFS shares).  I have tested with XMMS, mp3blaster, Amarok, Rythmbox, and a few others (cant remember which).  If i jump back and fourth between files too quickly it seems like there might be a caching issue or buffering issue over the smb mount that causes it to crash.  Sometimes (very seldom it happens on its own) just by playing music and not hopping around the playlist. I have done mount - smbfs, mount.cifs smb4k, fusesmb and none of them seem to work properly or remain stable.  Also compiled samba 3.0.25b from scratch to see if that helps but the release logs dont seem to show anything relating to fixing the issues I am running into.  I have also used different switches (to ensure its not my network gear / switch causing issues)  Any ideas???  Thanks in advance.

I've watched several hours of video from one computer to another using smbfs without any problems. Have you checked your router / hub for issues?

---

### Post by ipyakuza on 2007-08-14
Hello, thanks for the reply.  Yeah i have 8 different switches and tried a few of them Cisco, Netgear, generic, etc.  None of them seem to make a difference.  The mount seems to be fine for days on end.  Its only if i hammer it by rapidly jumping around files.  For example, if I use amarok and add 100 songs from the mount to the playlist, i can rapidly click on various songs making the music player request streaming different files.  Also if i just play a single song (say a 2 hour trance mix) and jump around the song (fast forward and rewind) it seems to eventually crash.  You dont have to do it a lot even if you just click on one song, listen to it for a few seconds then jump to another song eventually after some 5 to 50 songs it hangs.  Same results from rockbox or mp3blaster.  Funny thing is last night I tried again mounting a share with 100 songs from my finances windows 2000 machine and i had no issues.  Now i am starting to think that this is an issue with my NAS.  Does anyone out there have the Intel SE4000 NAS?  If so, do they experience similar behaviour?  Thanks

---

### Post by ipyakuza on 2007-08-14
error

---

### Post by DugieHowsa on 2007-08-15
--------------------------------------------------------------------------------

I have found that smbfs is very buggy. You may have better luck with cifs.

I had been having trouble mounting a Windows Share. I tried to mount using smbfs. I tried to mount using cifs. In the end, some one showed me this link:

[https://bugzilla.samba.org/show_bug.cgi?id=1920](https://bugzilla.samba.org/show_bug.cgi?id=1920)

Summary: "smbfs is unmaintained and known to be severely broken." That was posted back in 2004, so needless to say probably not much has happened with smbfs in the last 3 years.

So here is the man page for mount.cifs that lists all the options:

[http://www.die.net/doc/linux/man/man8/mount.cifs.8.html](http://www.die.net/doc/linux/man/man8/mount.cifs.8.html)

Many people here have also listed many good posts, giving several good examples, on how to properly utilize cifs:

[http://ubuntuforums.org/showthread.php?t=288534](http://ubuntuforums.org/showthread.php?t=288534)

This post solved the particular problem I was having:

[http://ubuntuforums.org/showthread.php?t=483184](http://ubuntuforums.org/showthread.php?t=483184)

In summary: USE CIFS. DO NOT USE SMBFS.

---

