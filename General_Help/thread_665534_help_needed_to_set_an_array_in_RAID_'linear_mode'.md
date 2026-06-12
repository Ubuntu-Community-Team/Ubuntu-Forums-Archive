---
title: "help needed to set an array in RAID 'linear mode'"
date: 2008-01-12
forum: General Help
---

### Post by Saponsky09 on 2008-01-12
I installed gutsy on my old desktop with a 40GB disk.  It has three partitions, one for /, another for /home and the other for swap.  Then I added another disk to it which used to be in another desktop running windows xp.  I want to format the last disk and then make an array in RAID 'linear mode' to join it to my /home partition.
  I'm confused in the steps, i guess it's 1-format the second disk.  2-make the RAID array in linear mode. 3- mount the array to /home???
  Please correct me because I'm wild guessing here.  Also I want the array to be available when i boot.  I will appreciate any ideas and corrections, thanks for your time/attention.

---

### Post by fjgaude on 2008-01-12
I could be wrong but I don't think you can successfully do what you are planning. You can't boot from a software raid linear, a race issue I do believe. Maybe I'm wrong...

Maybe others here will say otherwise.

---

### Post by Saponsky09 on 2008-01-12
Are you sure? I think it's possible, I've seen some posts about some tweaks you can make to make the array available at boot. Anyways thanks for your help dude!

---

### Post by fjgaude on 2008-01-13
Available at boot but not boot from.

---

