---
title: "gparted gives 'Device does not exist' error..."
date: 2006-07-03
forum: General Help
---

### Post by mod187 on 2006-07-03
I am trying to install 6.06 on another machine. When I try to resize the partition using gparted, it finds all of my drives correctly. The drive I want to resize is a 120GB, with 100 GB free. It currently has an XP install on the drive. I am trying to resize the drive, so I can dual boot. 

When I select the drive, click on resize, it will not let me change the size at all. When I check the information of the drive, it tells me 'device dev/hda1/ doesn't exist'...

I have defragged the drive, and checked for errors. All is OK. This drive is master on ide1.

Anyone have any ideas on what may be causing this? Is there any other info I need to provide for this question?

Thanks for your help...

Matt

---

### Post by mod187 on 2006-07-05
Well, I figured it out.

I selected the drive and clicked on 'Manage Flags'. It listed several items, the first being 'Boot', and it was the only item that was checked. I took the check out of this box, resized the drive, and everything worked fine. I went back after and put the check back in the box.

I hopes this helps if anyone else has this problem...

Matt

---

