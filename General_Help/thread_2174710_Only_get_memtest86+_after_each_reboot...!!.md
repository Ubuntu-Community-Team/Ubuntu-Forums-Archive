---
title: "Only get memtest86+ after each reboot...!!"
date: 2013-09-15
forum: General Help
---

### Post by EagleEyedOne on 2013-09-15
Within last week I 'upgraded' to 13.04 raring ringtail from 12.10 which worked great. Put the laptop to sleep by 'suspend' without power connected and it never woke up this afternoon. Laptop had enough battery, but by time I could plug to wall, the battery light had gone out. Now after plugging in and powering up, I'm only getting memtest86+ to run after each reboot. Let the test run 100% and result is passing all tests. Disconnected power and battery for 10 minutes and tried reboot but get same thing. I get a blip of the purple Ubuntu screen and it runs right into the test.

Any suggestions to get past the test? Is my OS/data mortally wounded now..? Thanks for any commentary!

---

### Post by jamesisin on 2013-09-15
You might try booting into the live CD and running update-grub.

---

### Post by Quackers on 2013-09-15
Run an fsck on the drive or more accurately your root partition. It doesn't like running out of power which may have happened.

---

