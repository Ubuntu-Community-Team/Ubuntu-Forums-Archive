---
title: "can a VM handle all my needs?"
date: 2008-05-04
forum: General Help
---

### Post by android6011 on 2008-05-04
I am in the market for a laptop, and I want to find one that will run ubuntu flawlessly as possible so that I can use it as my primary OS, however I find it almost impossible to ditch windows completely. I was wondering if I have a windows in a VM installed with a couple gigs of memory will I still be able to run games (not high end games) and use all my other programs without noticing any performance problems? What are the potential problems i might face? any information would be very helpful. Thanks

---

### Post by NightwishFan on 2008-05-04
From what I know Virtual machines have no 3d support for games, but most other apps should run. A dual boot would be required for "Windows" gaming. You could try your luck at wine, it keeps getting better and better, and 1.0 is due soon.

---

### Post by Aearenda on 2008-05-04
Main difficulty could be suspend/hibernate. I think I'd do it the other way around - run Windows as shipped, and Ubuntu in a VM, given your needs. 

VMs have slower disk access than native, but almost everything else is equivalent in speed, apart from 3d video acceleration.

---

### Post by android6011 on 2008-05-04
thanks, so if im not looking for gaming, the vm should be just fine? office and everything will run ok?

---

### Post by Aearenda on 2008-05-04
Everything depends.... it's not possible to give a straight yes/no answer.

If you want to run a business on Excel, using massive spreadsheets, it may not suit you. But it might be acceptable to me!

Laptop drives also constrain disk throughput compared to desktops.

In practice, yes, I think you will be ok so long as your laptop has enough RAM and a recent CPU - don't try it on an Asus eee!

I have a Dell 530 with 2Gb RAM, and I use Windows XP in VirtualBox to run my scanner. It is still way faster doing this than Windows XP on my 1Ghz Pentium-M laptop, which I used to think was just fine.

Some laptops have more troubles than others running Ubuntu, mainly through the lack of manufacturer assistance in getting ACPI and video to work properly. System76 and more recently Dell have supported Ubuntu systems. It would be a good idea to come up with a shortlist and then search for them by name in these forums to see how they go.

---

### Post by android6011 on 2008-05-04
[QUOTE=Aearenda;4883176]Everything depends.... it's not possible to give a straight yes/no answer.

i understand that but i guess i dont just mean stuff in the VM, like i know the memory in the system i used before really impacted it, but when i had a vm open before ubuntu was almost didnt even respond, with a couple gigs, ubuntu should still be fine though right?

---

### Post by Aearenda on 2008-05-04
Yes, that's right - I have 512Mb allocated to my XP vm, and the rest is used by Ubuntu, it doesn't notice the difference. Both Ubuntu and XP run fast (but I'm using a Core 2 duo desktop with multiple SATA drives - may be different on a laptop).

---

