---
title: "Cifs mounted drive shows wrong usage and free space"
date: 2015-03-06
forum: General Help
---

### Post by CaptainFuzzyFace on 2015-03-06
I have a 500gig NAS drive attached to my router (Talktalk Huawei HG-635).

I have then put it in the fstab of my PC (Ubuntu 14.04 64bit) and several Raspberry Pi's for everyone to share. We can all write to it, but it always shows that there is only 63.3MB of free space (see attached screen shot). In fact it has 98.2Gig in use and about 400Gig free. We can write large amounts of data to it if we ignore the warning, but not individual files larger than 63.3MB as it objects.
[ATTACH=CONFIG]260498[/ATTACH]
How do I get this drive to show the correct usage and free space?

The entry in fstab is as follows
# Talk Talk Super Router
//superrouter/talktalk/JMicron-152D8888_usb1_1 /media/NasDrive-Media cifs credentials=/home/martin/.smbcredentials 0 0

Thanks.

---

### Post by TheFu on 2015-03-07
Other users here have reported this issue with Win8 space reports for both samba and Windows cifs shares. If that is what you see too - seems like a Win8 MSFT bug. [https://social.technet.microsoft.com/Forums/en-US/8bd3dab7-eb71-4ffb-90de-32d7f756cf69](https://social.technet.microsoft.com/Forums/en-US/8bd3dab7-eb71-4ffb-90de-32d7f756cf69)

If not, we can try to troubleshoot.

---- 
So you aren't running Windows with this at all.
I did a little looking with a 14.04 server running samba and clients running thunar and pcmanfm.

Thunar reports the correct total and available storage for the mounted file system ... but not for any linked file systems (wide-links samba setting).

pcmanfm reports (0 bytes) for the "size on disk" and the Total Size of files seems to be based on running a du -sh which includes symlink storage too.

Not sure I like either of these results.  Much prefer using CLI tools like df and du myself. Those do not lie.

Thinking more ... perhaps this is not a samba issue, but it is a gvfs issue?  I dunno - just a thought.
I have a few cifs mounts on different machines here.  Both du and df seem to work correctly to NFS, CIFS with either samba or windows as the cifs server.  
Using pcmanfm to a Windows cifs server - looks like a du -s is run again. Meh.
Using thanar to the same Windows cifs server - reports size = 0 bytes.

Using the fstab should be using a real mount.

Is the storage really a NAS or is it connect to the router via USB?

---

