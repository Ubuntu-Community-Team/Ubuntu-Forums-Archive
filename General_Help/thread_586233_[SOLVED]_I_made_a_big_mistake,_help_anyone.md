---
title: "[SOLVED] I made a big mistake, help anyone?"
date: 2007-10-22
forum: General Help
---

### Post by ZenithXI on 2007-10-22
After installing Ubuntu 7.04 I used it for a few days before returning to Windows (don't judge please). But after a few months I began running out of space on my HDD, so I thought I'd get rid of Ubuntu as I wasn't using it anymore.

 My friend said I should just delete the partition it was installed on. So after doing that, I restarted my computer only to find a GRUB boot error 17 & no OS at all. I still have the live CD if that helps. So can anyone instruct me on how to fix it? I would be so grateful.

---

### Post by Nunu on 2007-10-22
Oops.

Ok well basically when you install Linux along side windows, Linux overrides windows boot instructions. I think that you might need to reinstall windows. don't take my word for it yet. There might be another way of recovering your windows boot environment but not that i know of. Try running a repair installation from your windows CD. that might rebuild the boot instructions for windows, but again i am not 100% sure.

---

### Post by forestpixie on 2007-10-22
yea - put the win disc in and boot - let it do it's stuff. you'll get an option to install or repair - repair

once it's finished loading I believe you need to fixboot and fixmbr at the prompt

then reboot

---

### Post by mahousaru on 2007-10-22
Assuming you are on about XP.  Boot up to the install disk, goto recovery console mode and run 

fixboot

*Edit*
Beaten to it :p

---

### Post by ZenithXI on 2007-10-22
Thank you guys so much, glad to know that even windows users can feel the love from the open source community. In fact I think I'll give 7.10 a try, but this time I won't delete its partition.

---

### Post by forestpixie on 2007-10-22
can you mark thread solved please - and glad you're sorted

---

