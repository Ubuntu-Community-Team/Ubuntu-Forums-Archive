---
title: "Trouble Installing Ubuntu 8.04   Root file not defined"
date: 2008-06-02
forum: General Help
---

### Post by cherian on 2008-06-02
I am new to Linux/ububtu.


I tried to install Ubuntu on to Hp dv2000 running on Vista. At first I couldn't install since it was telling that there is a disk error. I corrected it using Vista and tried again. It worked. I deleted Vista and put only Ububtu. It worked for few hours. Then the system froze and I had to shut it down. When I restarted It failed to boot. I put the CD back. While Installing I got the error message in Step 4  Root File Not Define. The menus( new partition etc ) were not highlighted. So I cannot fully install it. I tried numerous times but no use. I think I ruined the laptop.

Any help/ideas/advices

Judy

---

### Post by logos34 on 2008-06-02
relax, I can't see how you could have ruined the laptop (or even the HDD for that matter)

Boot up the live cd again, open system>admin>gparted

delete all the partitions.  wipe it.  start the installation again and select 'guided--use entire hard disk'

And for future reference, if you're dual booting with vista, use only the latter's disk tools to shrink/resize it.  Otherwise trouble

---

### Post by cherian on 2008-06-02
Yes I did do that. It says no device found. Re-booted . Same story again.

---

### Post by logos34 on 2008-06-02
Check the Bios--maybe the settings got altered.  hard disk detect should be on 'LBA' or 'Auto'

---

### Post by cherian on 2008-06-03
Yes Checked Bios, I am not that familiar with it. Under Diagnostics  I tried to run diagnostics its says no IDE detected

---

### Post by cherian on 2008-06-08
Any help please, still I can't fix it

---

