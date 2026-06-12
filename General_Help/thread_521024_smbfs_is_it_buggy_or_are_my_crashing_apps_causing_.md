---
title: "smbfs: is it buggy or are my crashing apps causing it to hang?"
date: 2007-08-08
forum: General Help
---

### Post by ipyakuza on 2007-08-08
Hello to all, I've been using linux for a really long time but always wondered what the deal is with smbfs mounts.  On my home network I am running a nas with CIFS shares.  I have no problem mounting them but it always seems that given the right circumstances the mount tends to crash or become corrupted.  The only solution is to drop it and remount it then it works fine again.  Sometimes if an application crashes like gThumb or XMMS, it will cause the share to hang.  Other times the mount will last for days, weeks, etc. (depending on what type of traffic is passing over it and how much).  I cant seem to put my finger on the root cause.  Anybody else had this issue?  Thanks in advance.

---

### Post by tgalati4 on 2007-08-09
You could try installing fuse and then mounting those shares through fuse.  Since fuse is a user-space file system, it's less likely to get mangled by the kernel.  Try mounting the same share both ways and see which one lasts longer.

Are you routing through a switch or a hub?  If you are using an older hub, then your network traffic is subject to collisions which could corrupt a mount.  If you are using a switch, then the data traffic is separated and there are less collisions.  Sometimes routers just go bad or they overheat.  Sometimes cabling or interference is a problem.  Try some different network cables or rerouting the wires.

I have a P1, 166 MHz running DSL with samba shares for music and media files.  Up for 88 days it serves 6 other machines--wired and wireless.  No problems so far.

---

### Post by ipyakuza on 2007-08-12
Thanks for the input.  I will give fuse a shot and submit my results.  Right now my connections are running through a Cisco 2950 managed switch no hubs.  As part of my testing I actually went ahead and dropped on mp3blaster a text based mp3 player and it plays just fine with no issues to the smb mounts (for days on end).  Its only when im streaming songs off my NAS in an app running on xwindows (im using KDE but happens on gnome too) if that app falls over the whole mount goes to crap.  mp3blaster... i can run it forever with no issues.  Thanks again ill post results

---

### Post by ipyakuza on 2007-08-12
Questions.  Im using fusesmb and im a little baffled by the format for the fusesmb.conf file.  I have it at fusesmb.conf and whenever I run 'sudo fusesmb /mnt/public2' it mounts but it shows listed as not a directory and ?'s.  Here is my config:

; Global settings
;[global]
; Default username and password
username=user
password=pass

; List hidden shares
;showhiddenshares=true

; Connection timeout in seconds
timeout = 10

;Interval for updating new shares in minutes
interval = 10

; Don't list these servers and/or workgroups separated by commas
;[ignore]
;servers=SERVER,SERVER2,SERVER3
;workgroups=WORKGROUP,WG2


; share from NAS
[/192.168.1.2/Public]
username=user
password=pass


(NOTE: user and pass are correct but not listed here for obvious reasons)

the man pages seem to be a little sparse with a useful example.  Any feedback would be appreciated.  Thanks in advance!

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

### Post by ipyakuza on 2007-08-15
Thanks for the info.  I actually tried mount.cifs and same results.  I have tried mount -t smb, smbmount, smb4k all with the same results.  I agree with your assessment that smb is buggy.  I think with more research I am uncovering that my NAS might be the culprit.  WHen i mounted a windows 2k box to my linux box and shared out 100 mp3s they played fine no issues.  When i mounted the NAS (it uses a small linux kernel image and custom linux build) it works but hangs.  Unfortunatly because its an intel ss4000e nas i cant modify anything internally so im stuck. It supports CIFS shares and NFS mounts.  Im working with NFS and its really solid (so far).  Drawback, NFS uses UID permissions and that causes my local linux user not to be able to access the files.... sigh...  Ill still try some of the articles you posted.  Thanks again

---

