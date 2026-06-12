---
title: "Advice Needed: Filesystem for external USB drive"
date: 2006-12-18
forum: General Help
---

### Post by shane_on_u on 2006-12-18
I just purchased a 500gb usb drive for storing media files. I was hoping to get some advice on the appropriate filesystem to use. My other external drives have been formatted as ext3 but I've noticed that I'm losing a lot of gigs as a result. The data on these drives is important to me, but I would also like to retain as much space as I can. Should I be formatting these external drives as ext3? Or is some other filesystem (fat32? don't know if it's possible with 500gb) more appropriate for data storage. I don't plan to share these files with a windows system so windows compatibility is not an issue.

Any advice/opinions would be much appreciated.

---

### Post by bodhi.zazen on 2006-12-18
journaled file systems are more secure. They will take 5% of your disk space.

If you do not like this, try ext2

---

### Post by shane_on_u on 2006-12-18
Thanks. I just did some more searching on the forums and I came across a link that I missed the first time around. For reference, in case anyone else is interested,  I'll list it here:

[http://www.ubuntuforums.org/showthread.php?t=305986](http://www.ubuntuforums.org/showthread.php?t=305986)

I think I can live with the 5% and will stick with ext3. Thank you for the reply.

---

### Post by manducasexta on 2007-07-07
Thanks for posting the link!

---

