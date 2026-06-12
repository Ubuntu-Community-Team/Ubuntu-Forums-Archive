---
title: "Uninstalling Ubuntu...the easy way?"
date: 2007-02-15
forum: General Help
---

### Post by quick90 on 2007-02-15
Hi, currently i am dual booting windows and ubuntu. What i want to do is get rid of ubuntu for various reasons. I installed acronis OS selector after ubuntu and currently it boots up before grub, so if i hit windows i skip grub altogether. using  acronis disk management couldn't i just simply delete the linux partitions and forget about resetting the mbr and use the acronis os select to automatically select windows (which it can do) and not have to worry about grub? i deleted suse in the summer and screwed my whole pc up do i don't want to mess with the mbr again. thanks, braden

---

### Post by jesus5511 on 2007-02-15
I think if you delete the Linux partition then Grub won't work because of the files associated with it in the boot directory of Ubuntu, I'm no expert though.

---

### Post by n00bish on 2007-02-15
If you really want to get rid of ubuntu, you can reformat the partition ubuntu is taking up and make it as blank space.  Then, if you have a windows XP cd, you can put that in your system, start recovery mode, enter to a terminal and type "fixmbr" and that should reinstall your  windows ntloader bootloader.

---

### Post by quick90 on 2007-02-15
Yes i get that grub won't work, but will i still be able to boot up windows using acronis os selector since it boots up before grub

---

