---
title: "Need to boot with nomodeset AMD"
date: 2014-03-15
forum: General Help
---

### Post by bryncoles on 2014-03-15
Hi All.  

I have Xubuntu installed on a netbook with AMD chipset.  I know everything works, because I have been playing with it for a few days.  I have just reinstalled the system due to some Borking I did, but I need to set the Kernel parameter for nomodeset for it to boot.  

How can I show Grub at boot?  

Holding shift does not work.  Holding Space does not work.  Holding escape does not work.  Any ideas?

Thanks all!

---

### Post by phidia on 2014-03-15
From the [official ubuntu wiki]("https://help.ubuntu.com/community/Grub2"): 
                                > Hold down (right) SHIFT to display the menu during boot. In certain cases, pressing the ESC key may also display the menu.

Perhaps you were using the left shift key? Hope that helps.

---

### Post by bryncoles on 2014-03-15
Hi Phidia.  

Thanks for helping me!  I think I tried both keys (but yes, I was definitely bias towards the left key!)  I am fixed now!  ^_^

Any chance you know how to edit the Grub menu to show for a 5 second tie out please...?

---

### Post by phidia on 2014-03-15
Settings that can be edited are in /etc/default/grub  
Look under the Configuring GRUB 2 section [here]("https://help.ubuntu.com/community/Grub2/Setup#File_Structure").

---

### Post by bryncoles on 2014-03-16
Fantastic!  You are a star!

^_^

---

