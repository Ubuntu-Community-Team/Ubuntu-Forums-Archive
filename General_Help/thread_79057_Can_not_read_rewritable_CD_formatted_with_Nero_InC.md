---
title: "Can not read rewritable CD formatted with Nero InCD"
date: 2005-10-19
forum: General Help
---

### Post by anton123 on 2005-10-19
Hello,

I have stumbled over a new issue today; I can not read my rewritable CD formatted with Nero InCD. That same CD I was able to read in Ubuntu 5.04. Am I dumb or is Ubuntu actually going worse with each release? It is unclear to me.

I just checked all my other CD's and they are unreadable also. I just see the autorun.inf, OpenHTML.exe files on one CD and autorun.inf, udfrinst.exe on the other one.

---

### Post by anton123 on 2005-10-19
Is anyone else experiencing this problem?

---

### Post by chaumurky on 2005-10-19
Doesn't InCD do 'packet writing' or 'UDF' format? I haven't used it in years but it sounds like a compatability issue. Strange that it used to work in Hoary. I wonder what's changed.

---

### Post by Cariboo1938 on 2006-12-01
> **anton123 said:**
> Hello,
I have stumbled over a new issue today; I can not read my rewritable CD formatted with Nero InCD. That same CD I was able to read in Ubuntu 5.04. Am I dumb or is Ubuntu actually going worse with each release? It is unclear to me.
I just checked all my other CD's and they are unreadable also. I just see the autorun.inf, OpenHTML.exe files on one CD and autorun.inf, udfrinst.exe on the other one.Hi anton, Maybe the response is obsolete...but I'm working on this UDF / packetwriting issue in Ubuntu 6.10 (Edgy 64bit) and I'm still looking everywhere for solutions, so I ran into this thread.
What helped me to read a Nero/InCD formatted disk was to run the two commands in a trminal```
sudo umount /media/cdrom0
sudo mount -tudf -orw,noexec,nosuid,nodev,user /dev/hda /media/cdrom0
```After that I can read the pre-formatted disk [COLOR="Red"]but I still can't write to it.[/COLOR]
Attention tho the mount points and the name of you drive.
In my case the drive is mounted in /media and the device name is hda.

---

