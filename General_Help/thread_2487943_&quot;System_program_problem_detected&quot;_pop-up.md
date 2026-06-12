---
title: "&quot;System program problem detected&quot; pop-up between reboots"
date: 2023-06-18
forum: General Help
---

### Post by a-k-i-r-a on 2023-06-18
Hello everyone o/

I've been receiving the same error every time I reboot Ubuntu and start any application (Tested with VLC, Firefox, Gimp...):
[CENTER][IMG]https://ubuntuforums.org/attachment.php?attachmentid=292398&stc=1[/IMG]
[/CENTER]
without any other info about the error itself. After I close the warning it does not prompt the message again and the system behaves normally apparently...Until I reboot it again and the same message appears after I launch an app.

Until now I've tried narrowing down the issue by checking the logs in /var/log and what I found in common between reboots is that syslog contains the following lines with the time more or less close to the time that the error is displayed:[CENTER][IMG]https://ubuntuforums.org/attachment.php?attachmentid=292397&stc=1[/IMG]
[/CENTER]
 ```
Jun 18 17:19:47 pedro-Inspiron-3584 ubuntu-appindicators@ubuntu.com[1761]: **unable to update icon for software-update-available**
Jun 18 17:19:47 pedro-Inspiron-3584 ubuntu-appindicators@ubuntu.com[1761]: **unable to update icon for livepatch**

```

So I've run Software Update and also sudo apt update && sudo apt dist-upgrade without any errors but the message between reboots still persists. I'm currently using Ubuntu 22.04.2 LTS. Could someone give me a tip on how to troubleshoot this issue?

---

### Post by Holger_Gehrke on 2023-06-18
Look in '/var/crash'. That's where crash reports are stored. Sometimes a report gets stuck in there and isn't removed and then you get these recurring 'system program problem' messages. Read the report and if it's not something catastrophic that absolutely needs attention, remove it.

Holger

---

### Post by a-k-i-r-a on 2023-06-19
Thank you, it worked :). Basically I had tried to mount my phone a few days back using the jmfpfs tool which generated a report that was stored in /var/crash. After deleting it I rebooted several times and the message is no longer being displayed.

---

