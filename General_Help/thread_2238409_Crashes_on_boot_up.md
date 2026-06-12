---
title: "Crashes on boot up"
date: 2014-08-07
forum: General Help
---

### Post by linux_dream on 2014-08-07
Hi guys! 
It's been around 2 days since I get crashes on boot up and I haven't figured out what's wrong.
As far as I remember I only did "sudo apt-get update" and "sudo apt-get upgrade" in the last 2 days in the terminal. 
If I click on "report problem", something automatically crashes, I think it's the bug report itself that crashes.
Here's a screenshot: [IMG]http://i.imgur.com/pbsi0a5.png[/IMG].
Any idea how I could investigate what's wrong with my system? As I said, this happens every single time I reboot the computer.
Thanks!

---

### Post by Jesse_Campton on 2014-08-07
Try removing the crash logs and see if that fixes it when you reboot. ```
[FONT=Ubuntu Mono]sudo rm /var/crash/*[/FONT]
``` Referenced here: ([http://askubuntu.com/questions/365358/im-getting-a-lot-of-system-program-problem-detected-error-dialogs-is-there-a](http://askubuntu.com/questions/365358/im-getting-a-lot-of-system-program-problem-detected-error-dialogs-is-there-a)), among a few other places.

---

### Post by linux_dream on 2014-08-07
> **Jesse_Campton said:**
> Try removing the crash logs and see if that fixes it when you reboot. ```
[FONT=Ubuntu Mono]sudo rm /var/crash/*[/FONT]
``` Referenced here: ([http://askubuntu.com/questions/365358/im-getting-a-lot-of-system-program-problem-detected-error-dialogs-is-there-a](http://askubuntu.com/questions/365358/im-getting-a-lot-of-system-program-problem-detected-error-dialogs-is-there-a)), among a few other places.

Thank you very much, that worked!!!
Sorry that I didn't know about it!

---

### Post by Jesse_Campton on 2014-08-07
Welcome please mark thread as solved.

---

