---
title: "Moving a LVM logical volume"
date: 2022-12-13
forum: General Help
---

### Post by georgesgiralt on 2022-12-13
Hello all,
I'm getting old, and can't remember if this is possible or not...
I've a system (Ubuntu 20.04.5 LTS) made with a single VG on two PV, one classical disk and one small SSD.
The SSD hold all the system's lv (Slash, /usr, /var, and so on), the HD only hold the /home LV which is too big to fit the SSD. 
So my VG0 vg has PV1 and PV2. 
PV1 only contains home LV
PV2 contains all other LVs.
I would like to export the PV1 and Home LV from VG0 and create a second VG (VG1) with the PV1 and Home LV **_WITHOUT destroying the data in the Home lv _**... 
Is this possible ? And if yes, how ? 
Many thanks in advance for your help and advice !

---

### Post by TheFu on 2022-12-13
Please post the commands and output from 
```
sudo pvs
sudo vgs
sudo lvs
```
so we have facts, not interpretations.
Use forum 'code-tags' or it will be unreadable.
An 'lsblk -e 7 -o name,size,type,fstype,mountpoint' would be helpful too in the output.

---

### Post by georgesgiralt on 2022-12-13
Found it. vgsplit. 
Thank you. 
Have a nice day.

---

### Post by georgesgiralt on 2022-12-14
Hello Guys,
I've done it. 
For the record, here is what I did (and it may serve others).
The VG had two PV, PV1 and PV2.
The logical volume I wanted to move (vg0/home) was on PV1 entirely. It was the sole LV on this PV (this is important, if you want to retain a functioning VG after ...) 
Vgsplit can't proceed if the VG is activated, so if it is the sole VG of the box, you have to use a live system to do the move. 
Here is the synopsys/ 
1) boot a live Ubuntu on the offending machine.
2) open a terminal on the live Ubuntu.
3) deactivate the VG you want to work on :
```
 vgchange -a n VG0 
```
4) triple check the VG and LV using lvs and pvs and blkid -o name,uuid.
5 ) split the VG :
```
 vgsplit --name home VG0 Test 
```
This will extract the PV containing the logical volume home from VG0 and create a new volume group named Test containing the PV1 onto which the lv was built. 
Et voilà ! 
NB : remember to modify the fstab file of the computer to accommodate the new VG and device for the /home file system...
Reboot to the "normal" operating system  and you're done.  
P.S. : if you want to revert the changes, you can use vgmerge .....
Edit : Since my retirement, I have difficulties remembering things that I used often during my work life.... Do not get old ;-)

---

