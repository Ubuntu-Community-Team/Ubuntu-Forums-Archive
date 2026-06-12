---
title: "removing dual boot"
date: 2015-07-17
forum: General Help
---

### Post by Robing Goodfellow on 2015-07-17
I have a laptop, two disk system with a 240 GB SSD and a 125 GB SSD. Trusty resides on the 240 and Precise on the 125. I wanted to thoroughly test Trusty before I committed to it which I now have, so I want to get rid of Precise on the 125 and move my /home to it (most likely, still haven't decided on what I'll use the 125 for). I've looked around, done some reading and I am not without experience, but don't have time to recover from something stupid, so I'm just checking myself to make sure I've got this right. The 125 is sda and the 240 is sdb. I figured I would:

```
mkfs.ext4 /dev/sda
update-grub
```

and then when I decided what to do with the 125 I could deal with the partitions and mounting, which is no problem.

Any issues with this plan? Is it really that simple or am I missing something? The data from the 125 is already backed up, so no worries there. My concern is mucking up Trusty on the 240.

regards, Richard

---

### Post by sudodus on 2015-07-17
I suggest that you

1. Backup also the current trusty system before editing any partitions.

2. install grub into the head of the 240 GB SSD with trusty,

3. and check that the computer can boot from it without help from the other drive.

After that you can do whatever you want with the other drive (without risk).

See this link: [Reinstalling GRUB 2](https://help.ubuntu.com/community/Grub2/Installing#Reinstalling_GRUB_2)

---

### Post by Robing Goodfellow on 2015-07-17
Worked great. Used my original plan, but first did 


sudo grub-install /dev/sdX  # Example: sudo grub-install /dev/sda

---

### Post by sudodus on 2015-07-17
I'm glad it worked, and thanks for sharing your solution :-)

---

