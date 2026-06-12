---
title: "Is there a way to get reliable MTP transfer in Trusty?"
date: 2014-04-23
forum: General Help
---

### Post by halfbeing on 2014-04-23
Hello,

Is there a way to get reliable MTP transfer in Trusty? Someone told me a while back that MTP support would be much improved in Trusty, but I can see no improvement at all. All I get are stalled transfers, freezes and whole MTP file systems disappearing from view. I have unplugged and rebooted my phone (an Xperia P running Android 4.1) countless times in a desperate effort to get something to happen, but I am unable to perform even the simplest copy and paste operations. If anything, things are worse than in Saucy. I have tried using Thunar. I have tried using Nautilus. Both are useless. Is there an alternative implementation of MTP that actually works? I'm getting desperate. People have suggested using alternatives such as rsync over wifi, but they really don't cut it for the projects I am working on.

---

### Post by efflandt on 2014-04-24
MTP never worked properly for me in 12.04 (although, it does work on my 13.10 laptop), so for Android apps I resorted to using **AndFTP** (which can sftp from the phone), **SSHServer** (if I want to ssh or sftp to my phone), or **ConnectBot** if I want to ssh from my phone, using my Linux openssh key. One issue with MTP in 13.10 was that you could not open files on the phone (images, etc.), you had to copy them to Linux first.

---

### Post by halfbeing on 2014-04-24
Thanks for the suggestions. But are you saying that in 13.10 you simply aren't getting the kinds of problems I'm getting, of transfers failing, MTP mounts disappearing from view etc.?

---

