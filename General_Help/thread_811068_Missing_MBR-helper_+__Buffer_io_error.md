---
title: "Missing MBR-helper? +  Buffer i/o error"
date: 2008-05-28
forum: General Help
---

### Post by kennyken747 on 2008-05-28
Ok, I tried to install from CD and it was burned at 4x, disc-at-once too

came up with [B]Buffer i/o error on sda logical block1 ata1.00 {DRDY ERR} {UNC}
[/B]
Then, I used install-inside-windows option all installed well, but when  i rebooted
**Try(fd0) : invalid or null Missing MBR-helper**

Thanks in advance can anyone please help?

---

### Post by kennyken747 on 2008-05-28
Please?

---

### Post by pieisgood4589 on 2008-05-28
> **kennyken747 said:**
> Please?

Woah there- calm down. No need to bump after 20 minutes ;)

OK, according to my "highly reliable" sources, it's simply a hard drive related issue. Can you boot back into Windows succesfully?
The problem seems to be a direct media error. Could you try completely formatting the HD, clearing the Master Boot Record by booting from the Windows XP install CD, going into recovery console and typing in "fixmbr" and then re-install Ubuntu?

---

### Post by kennyken747 on 2008-05-28
Lol sorry Im just ready to get my Ubuntu fix,
but yeah i have no problem but do i reformat into NTFS or FAT or EXT?

Is there some other way to clear MBR because I lost XP install disc :(

and which recovery console, ubuntu's or windows'?

And im down to do it, it's just are you sure that it works, because it wouldnt be worth losing all my work on windows

and would it help me with the MBR AND the i/o prob or just the MBR one and I would have to re-install directly w/ wubi or could I just go again from CD

---

