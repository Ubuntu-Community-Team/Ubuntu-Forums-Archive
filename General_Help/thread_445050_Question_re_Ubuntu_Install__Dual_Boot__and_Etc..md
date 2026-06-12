---
title: "Question re: Ubuntu Install / Dual Boot / and Etc."
date: 2007-05-15
forum: General Help
---

### Post by tpupaz on 2007-05-15
So I put my first copy of Fiesty on my laptop and I must say I love it.

I made this machine dual boot with XP, but have decided I no longer want XP on it as its not needed...at all.

I installed a lot of stuff on my laptop, stuff I dont need, or stuff I got multiples of, my question is as follows

a) Because I want to reclaim all that HD space but dont want to mess or upset Grub, is a total reinstall the best idea now that I know what I want, need, and more on my Ubuntu system?

b) Anyone have any problems with Gmail and Evolution / and or Thunderbird? I had to delete all my accounts that were going to Gmail becasue none of them would show up in my email clients.

Thanks in advance

Tony

---

### Post by bscbrit on 2007-05-15
There is no need to re-install Ubuntu.  Simply reformat any drives that XP is currently using, and re-assign them in fstab.  (If you need details of how to modify fstab, come back here and ask.)  Remove the XP boot option from GRUB (sudo [youreditor] /boot/grub/menu.lst).  Done.

---

### Post by tpupaz on 2007-05-15
XP is using a 20 gb partition I made for it on the same drive as Ubuntu's ext3 partition.

Should I make the XP Partition ext3 with gPart and that could add it onto the linux side?

Is that feasable?

---

### Post by bscbrit on 2007-05-16
Yes, format it as ext3 and then add a command to fstab to mount it automatically at boot.

---

