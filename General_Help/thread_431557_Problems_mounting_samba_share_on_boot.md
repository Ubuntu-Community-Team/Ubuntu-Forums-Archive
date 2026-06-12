---
title: "Problems mounting samba share on boot"
date: 2007-05-03
forum: General Help
---

### Post by affected on 2007-05-03
Hi,
I have a linux box as a fileserver running samba, and I have the samba share mounted via fstab on my desktop, running Kubuntu feisty. It works, mostly, but sometimes the share is not mounted correctly on boot: sometimes, if I try to ls the mount dir, the prompt hangs for a while and then gives me an input/output error. I can fix the problem by mounting the share in a different directory, but I can not unmount the directory it was first mounted in, I just get an error saying the device is busy, even though I can't think of anything that would be accessing the directory. Sometimes on boot the share works just fine. One reproducible thing that seemed to cause the problem was having Amarok running when I shut the system down, but I put that in the exclusion list in session manager, so it doesn't load on boot. (My system saves the session I'm running when shutting down and loads the same session again upon boot.) For a while I thought I had it all sorted out, but now I notice the problem still persists, and I'm unable to find a cause for it. Maybe something reserves access to the mount point I have set in fstab before it can be mounted, but I've no idea what that could be.

This is the fstab syntax I use for mounting the share:
//server-ip/share /media/mountpoint/ smbfs credentials=/credentialsfile,uid=myuser,gid=myuser,file_mode=0640,iocharset=utf8,codepage=cp850 0 0

edited to remove some details of course.

I'd appreciate any help, this problem is quite annoying.

---

### Post by DugieHowsa on 2007-06-27
You should try using cifs.  This post states that smbfs is unstable and no longer under active development:

[https://bugzilla.samba.org/show_bug.cgi?id=1920](https://bugzilla.samba.org/show_bug.cgi?id=1920)

Summary: "smbfs is unmaintained and known to be severely broken." That was posted back in 2004, so needless to say probably not much has happened with smbfs in the last 3 years.

The following is also a very good post on how to configure cifs and gives a few examples on how to automatically mount cifs shares at boot.

[http://ubuntuforums.org/showthread.php?t=288534](http://ubuntuforums.org/showthread.php?t=288534)

---

