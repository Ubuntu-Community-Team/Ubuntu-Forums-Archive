---
title: "Ubuntu install..ubuntu errors :("
date: 2008-01-14
forum: General Help
---

### Post by leveliv on 2008-01-14
I am using ubuntu 6.10 ..well trying to anyways


anyways I boot from the disc and right off the hop I get an xserver error. Saying I have no screens so I reconfigure xserver using VESA and all the other defaults. and finally get into the liveCD portion which is running noticeably slow  which my guess is because I am using VESA. Anyways it installs on my Harddrive. and tells me to restart and I get a "Loading GRUB stage 1.5Read Error" forcing me to restart...I get this everytime. 

Specs 

Abit Fatal1ty AN8 (non sli) 
EVGA 8600GT
512 RAM
100GB Maxtor and 40GB MAxtor 

(ubuntu was installed on the 40GB which I think is my slave) I think the 100s a Master.

---

### Post by Nexusx6 on 2008-01-15
This error usually indicates that your BIOS is causing your boot problems. You're going to have to get the latest copy of BIOS from your manufacture and flash yours. If that doesn't fix the problem I think there is a grub-install command that'll refresh grub. Lastly, try unplugging the HD that doesn't have Ubuntu loaded on it, and make sure the Ubuntu HD is the one that's first boot.

If you come to a solution, mark your subject as [SOLVED] and post how you went about it for the sake of others. If not, keep us updated on the situation and we'll try to see you though :KS

---

