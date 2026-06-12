---
title: "Help: My Hardrive (windows7) Won't boot. Using Ubuntu to fix it?"
date: 2017-01-12
forum: General Help
---

### Post by ghostlander on 2017-01-12
So, I turned on my computer today and after the MSI logo screen it sits there. I went in to the MSI menu and looked at the loading order, it says the hardrive is still there BUT, it's not lit up like my external hardrive or CD drive are when they are plugged in. 

I tried re-plugging the sata and power cords, rebooting, nothing. I'm thinking maybe something about my windows MBR is not working? 

I'm curious how I can either repair windows, repair the MBR, or maybe even restore to an earlier point? Using my Ubuntu OS that's working from a USB stick. 

I would rather not lose everything on my hardrive meaning I need to take the time to back up everything. 


Any help at all would be massively appreciated.

---

### Post by yancek on 2017-01-12
It is highly unlikely that you will be able to repair whatever problem you have on your proprietary, closed source microsoft operating system.  Your best option is to use the windows installation DVD with the Repair option.  There is a program called ntfsfix available with Ubuntu which might be able to repair some minor problem with the ntfs filesystem.  Boot your windows media and try running chkdsk for starters.

If you have data on the windows drive, you can mount the partition(s) from the Ubuntu usb and  copy it to another drive.

Had you made any changes just prior to this problem?  Have you tried looking at the support.microsoft site or a windows forum for a solution?

---

