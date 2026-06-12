---
title: "Ubuntu fail to boot"
date: 2024-06-28
forum: General Help
---

### Post by nickelth on 2024-06-28
Hello, I shutdown my server last week and try to boot after one day, but it failed to boot and kept reporting "watchdog: BUG: soft lockup - CPU#46 stuck for 23s! [irq/473-nvidia:1778]", and then stuck at "A start job is running for ...(various jobs)", I followed some advices from Internet and tried to append parameter "nomodeset" to /etc/default/grub, but it didn't work. Can anyone help me?

---

### Post by yancek on 2024-06-28
Other than adding 'nomodeset', what else have you tried?  It would have been simpler to add 'nomodeset' on boot if you see a Grub menu and hit the e key on the keyboard, you could have added it for a one time boot to test and if it worked, made it permanent.  Have you checked and tried the suggestions at the link below?

 [https://askubuntu.com/questions/1264859/watchdog-bug-soft-lockup-cpu6-stuck-for-23s](https://askubuntu.com/questions/1264859/watchdog-bug-soft-lockup-cpu6-stuck-for-23s)

---

### Post by nickelth on 2024-06-29
> **yancek said:**
> Other than adding 'nomodeset', what else have you tried?  It would have been simpler to add 'nomodeset' on boot if you see a Grub menu and hit the e key on the keyboard, you could have added it for a one time boot to test and if it worked, made it permanent.  Have you checked and tried the suggestions at the link below?

 [https://askubuntu.com/questions/1264859/watchdog-bug-soft-lockup-cpu6-stuck-for-23s](https://askubuntu.com/questions/1264859/watchdog-bug-soft-lockup-cpu6-stuck-for-23s)
Thanks for reply. I tried to add "nomodeset" and "[COLOR=#0C0D0E][FONT=ui-monospace]nouveau.modeset=0[/FONT][/COLOR]" in boot command, it didn't work. I also tried to update nvidia driver and enable nvidia-persistenced, but these methods failed because the system can not enable network service. I login in with recovery mode and found a process called [irq/473-nvidia] is using 100% CPU, and I coundn't kill it. I think this problem may related to nvidia driver, but I haven't find root cause.

---

### Post by nickelth on 2024-12-14
After several months I meet this problem again, but this time by unplug two of graphic cards physically, I solved this problem.

---

