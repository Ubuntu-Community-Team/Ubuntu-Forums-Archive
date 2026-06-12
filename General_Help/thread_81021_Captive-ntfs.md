---
title: "Captive-ntfs"
date: 2005-10-23
forum: General Help
---

### Post by JHP on 2005-10-23
I just installed Breezy and Got Captive-ntfs installed (I had tired it on Fedora 4 but it wouldn't work).  So far I like ubuntu alot better.  However, when I mount with captive it is very, very, very slow.  I had read that captive can be slow at writing large files, but this is just opening folders.  To open the root of my ntfs partition it takes 10-15 minutes.  With the standard ntfs driver it is instant.  I need captive because i have a huge virus infection in windows that i need to remove and mcaffe won't work.  I am trying to use f-prot, but it dosen't recognize the ohter folders (timeout error?).

Any help is greatly appreciated.

Thanks
--JP

---

### Post by Kyral on 2005-10-23
I don't mean to sound evil/rude/mean, but Captive NTFS is NOT a good idea. You are just as likely to completely trash your NTFS partition even more than the virus infection has (Virus' can be cleaned without a reformat, corrupted filesystems can't under normal circumstances).

I'd reboot into Windows Safe Mode and grab aVast! Antivirus and try that. I used it for years before switching to Linux and it was very good. Also free. Its just a tad on the sensitive side....

---

### Post by shenki on 2005-10-24
[QUOTE=Kyral][...] Captive NTFS is NOT a good idea. You are just as likely to completely trash your NTFS partition even more than the virus infection has [/QUOTE]

I was just wondering, where did you learn that captive is likely to corrupt a NTFS partition? I'd be intrested in reading something to back up your claim.

I haven't used it under Ubuntu/Debian, but previous experiences indicated that it worked fine, although on the slow side of things as far as filesystems go.

---

### Post by brallan on 2006-04-23
ntfsprogs may be a better option, though I don't know if there's support in Breezy. Check out these in the Wiki:
[https://wiki.ubuntu.com/NTFSReadWrite]("https://wiki.ubuntu.com/NTFSReadWrite")
[https://wiki.ubuntu.com/Lkraider/NtfsFuse]("https://wiki.ubuntu.com/Lkraider/NtfsFuse")
[https://wiki.ubuntu.com/CaptiveHowTo]("https://wiki.ubuntu.com/CaptiveHowTo")

---

### Post by sinkxdie on 2006-04-23
Im looking for a way to write it without messing up my NTFS... Because I know that's gonna happen

---

### Post by shenki on 2006-04-23
ntfsmount from ntfstools is what you're looking for.

[http://wiki.linux-ntfs.org/doku.php?id=ntfsmount](http://wiki.linux-ntfs.org/doku.php?id=ntfsmount)

The project hompeage there describes how the driver impliments safe write support - basicly, it will ether suceeed in writing your file perfectly, or it will refuse to write your file, but either way it won't corrupt the ntfs volume.

to install, simply 
```
sudo apt-get install libfuse2 ntfsprogs
sudo ntfsmount /dev/hda1 /media/hda1 -o fmask=0111,dmask=0,succeed_chmod

```

See the link in brallan's post for further details.

This will only work under dapper, but if you're the kind of user who's intrested in getting ntfs write support, you should think about installing dapper anyway.

---

