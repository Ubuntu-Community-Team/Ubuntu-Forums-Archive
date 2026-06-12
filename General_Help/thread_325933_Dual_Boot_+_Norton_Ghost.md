---
title: "Dual Boot + Norton Ghost"
date: 2006-12-26
forum: General Help
---

### Post by jonathan.lees on 2006-12-26
I just created a dual boot Ubuntu 6.10 / XP system. I used a combination of MS Remote Installation Services so that I could boot from the Ethernet card and Norton Ghost to create the image. After dumping the image to another machine and booting it will not load grub and refuses to boot. I guess using Norton was the wrong thing to do. Can anyone suggest what would be the best solution to use for ghosting a room full of PC's with a dual booting image.

thanks

---

### Post by tagra123 on 2006-12-26
> **jonathan.lees said:**
> I just created a dual boot Ubuntu 6.10 / XP system. I used a combination of MS Remote Installation Services so that I could boot from the Ethernet card and Norton Ghost to create the image. After dumping the image to another machine and booting it will not load grub and refuses to boot. I guess using Norton was the wrong thing to do. Can anyone suggest what would be the best solution to use for ghosting a room full of PC's with a dual booting image.

thanks

If you have a backup drive you can try   the dd command. It will copy everything.  

I will point you to another one of my post which shows ubuntu and partimage working to make a clone.

[http://ubuntuforums.org/showpost.php?p=1917499&postcount=40](http://ubuntuforums.org/showpost.php?p=1917499&postcount=40)

if you have the live cd you might be able to have grub find the partitions containing the partitions for you.

Search for grub on these forums.  I may have even posted and answer for this on. Anyway I think it will amount to reinstalling grub.  The problem is most likely something with the MBR -- or the drives being on different cables between the systems (WHAT WAS HDA  ON ONE SYSTEM MY BE HDC ON ANOTHER SYSTEM.).

This wasn't my best answer ever, but it should get you started in the right direction.


You could also look at reconstructor. It will let you create your own live cd with programs other than the defaults chosen by ubuntu.

---

### Post by jonathan.lees on 2006-12-27
thanks for that, I searched on Grub and found some useful threads too. I'll give them a go before I try partimage.

---

