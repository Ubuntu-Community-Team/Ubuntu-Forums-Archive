---
title: "Xubuntu - Did I download a bad ISO"
date: 2008-02-12
forum: General Help
---

### Post by tom_the_drummer on 2008-02-12
When I put the disc in the tray and click "start Xubbuntu", after it starts loading and going through it's "checklist" I get LOADS of errors SQUASHHFS  then some text after.


Anyone got any ideas?


Thanks


Tom

---

### Post by apetresc on 2008-02-12
That's definitely a corrupt disk there.

Try running md5sum on the original .iso you burned. You can get the correct hash from the same place you downloaded the image.

If the hashes match, the download is fine, and the corruption is due to the burning.
If the hashes don't match, the download **isn't** fine, redownload and try again.

---

### Post by Sammi on 2008-02-12
There should be an option to check the CD for defect right there in the boot menu on the CD a bit beneath the "Start Xubuntu" option.

---

### Post by apetresc on 2008-02-12
> **Sammi said:**
> There should be an option to check the CD for defect right there in the boot menu on the CD a bit beneath the "Start Xubuntu" option.

Yes, that's the thing he's failing. It's just a matter of whether the download is corrupted, or the CD-burning is corrupted. *Something's* corrupted, he already knows that.

---

### Post by tom_the_drummer on 2008-02-12
How do I run md5sum?

Just finished the disk loading, and it starts up the desktop as just an orange screen - that's it.

---

### Post by tom_the_drummer on 2008-02-12
> **AdrianP said:**
> Yes, that's the thing he's failing. It's just a matter of whether the download is corrupted, or the CD-burning is corrupted. *Something's* corrupted, he already knows that.
I'm not failing it at that point. I can get to thatscreen, I get all the messages when I actually start xubuntu

---

### Post by kerry_s on 2008-02-12
try reburning the iso at 4x.

---

### Post by tom_the_drummer on 2008-02-12
Done that - It was originally burnt at 4x

Then I trid re-burning it at 48x so now me thinks its a dead iso

---

### Post by Sammi on 2008-02-12
Here's a neat trick you can try if you're used to using bittorrent.

Try downloading the Xubuntu iso from the official Xubuntu iso torrent right over the corrupt iso you've downloaded. Just start the download and choose the folder that your current corrupt iso is in as the download directory. Use any client (ktorrent, deluge, transmission, azureus). Bittorrent should check you current iso and be able to find the corrupt part of the file and redownload only that particular tiny little part of it.

Bittorrent really is a marvelous invention, that is able to do more than most people are aware of. It's not just for pirates :D

---

### Post by ajgreeny on 2008-02-12
You check the md5sum of the iso by navigating to the folder where the file is and simply issue the command ```
md5sum filename.iso
```The result will appear after a few seconds, depending on processor speed, and you can compare that with the md5sum that you can get from [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

---

### Post by tom_the_drummer on 2008-02-12
Have treied downloading the iso again, burning it a couple more times and I am still getting the same hundreds of errors thrown back at me.

Shame =[ There must be a reason

---

