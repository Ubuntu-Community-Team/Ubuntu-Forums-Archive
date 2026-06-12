---
title: "&quot;[FAILED] Failed to start Accounts Service&quot; during boot-up"
date: 2022-10-17
forum: General Help
---

### Post by snorlax212 on 2022-10-17
Hello. I'm using xubuntu 22.04 LTS. In > /etc/default/grub I set > GRUB_CMDLINE_LINUX_DEFAULT="" so my boot up is in verbose mode. Every time I boot my system (since update from 20.04 to 22.04) I have this message that dash past among other:
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=291141&stc=1[/IMG]
it says:
```
"[FAILED] Failed to start Accounts Service"
```
And every time I check it with 'systemctl status accounts-daemon.service':
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=291142&stc=1[/IMG]
I see nothing wrong here anytime. Why is that?
Also, as i understand, this boot log should be in > /var/log/boot.log files, but this one is empty, and /var/log/boot.log.1 has boot info dated 1year ago. I googled and someone noted that this parameter > GRUB_CMDLINE_LINUX_DEFAULT="" disable boot logging in this file. But it doesnt make any sense: when i see boot log during boot up I wanna read this in logfile. How can I enable boot logging but leave verbose mode unaffected?

---

