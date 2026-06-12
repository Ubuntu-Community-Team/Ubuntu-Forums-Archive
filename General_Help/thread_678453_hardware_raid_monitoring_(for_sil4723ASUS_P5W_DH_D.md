---
title: "hardware raid monitoring (for sil4723/ASUS P5W DH Deluxe)?"
date: 2008-01-25
forum: General Help
---

### Post by stbub on 2008-01-25
I've plugged a pair of identical hard disk and it seems to work as a raid 1.  However, what good is a raid if you are not notified of a drive failure?

So, I've been searching and haven't found anything on the Silicon Image sil4723, as far as monitoring the status of the raid.

My motherboard is a P5W DH Deluxe.

---

### Post by funkelauge on 2008-04-25
Same problem here. Same hardware.

I did a lot of search in google and ubuntuforums but I haven't found a way to read SMART information from my RAID drives behind Sil4723 Controller :-(

If any P5W DH deluxe user has been able to get the SMART information from their RAID drives behind Sil4723 Controller please report!

As it is now I boot every now and then to Windows where the EZ Backup Manager would notify me if Array state is critical. It's shitty to have to depend on Windoof!

Cheers, DAve

---

### Post by fjgaude on 2008-04-25
Seems from memory the only way you can tell the condition of a raid array is when you boot up. You press a function key to permit entering the Sil mode that setup the raid in the first place. From there it shows how the drives are arranged and their health.

---

