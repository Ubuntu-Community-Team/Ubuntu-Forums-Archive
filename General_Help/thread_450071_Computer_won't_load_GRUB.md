---
title: "Computer won't load GRUB"
date: 2007-05-20
forum: General Help
---

### Post by Nate7679 on 2007-05-20
I installed wubi on one of my computers to run ubuntu without having to install it, but now GRUB won't load and I can't load either Windows XP or ubuntu. I force shut-down the computer after it quit responding on me, and now whenever I boot it up the computer's boot splash comes up, then I get a flashing cursor, and then it reloads the computers boot splash. Is there a way to load windows from the live CD? I need to do this so I can uninstall Wubi from windows.
Alternatively, I could manually uninstall Wubi from the live CD, but I would need read/write privileges to my internal hard drive. What would be the best way to do this from the live CD?

Thanks

---

### Post by mbradlcu on 2007-05-21
I'm not sure how wubi works and I'm guessing you have Windows installed on your HD.. the wubi page indicated that it doesn't mess with the mbr but apparently something did... anyway could you try and fix your MS loader with the info found here: [http://www.ntfs.com/mbr-damaged.htm](http://www.ntfs.com/mbr-damaged.htm),, basically it's the following using the MS install CD:
```
FIXMBR 
```

as far as uninstalling wubi from the live CD,, the CD would need ntfs read/write kernel enabled.. even then I'm not sure this would fix you're MBR.

another possibility would be to actually install Ubuntu on a small partition if you have room and can resize your ntfs partition down a little,, the install process would write to the MBR and correct the grub issue.
have fun!

---

### Post by Nate7679 on 2007-05-21
I hope its not as big of a problem as a problem with the hard drives MBR. Im going to try booting windows by using the super grub disk. info on it can be found here:

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

Once I'm in windows I'll back up all my data and uninstall wubi, which should hopefully fix the problem

---

