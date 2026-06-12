---
title: "Kontact/Kmail Bogged Down"
date: 2013-09-11
forum: General Help
---

### Post by zerubbabel on 2013-09-11
Over the past couple of days, Kontact and gradually become so slow as to be unusable. New mail arrives, but whenever I click on an unread item, I see the message viewing pane turn blue and display "Retrieving Folder Contents, please wait..." and I wait, and I wait, and I wait. It can take ten or fifteen minutes before the message appears. I have logged out and back in, with no improvement, rebooted with no improvement, I've run the Nepomuk Cleaner with no improvement. I have installed all available updates, with no improvement. I don't know what else to do. 

I really love Kontact and hate the thought of having to migrate back to Thunderbird/Lightning, but I can't live with this glacially slow response time. Any advice would be greatly appreciated.

By the way, I am using KDE 4.11.1 on Kubuntu 13.04 (amd64) with all updates applied.

---

### Post by zerubbabel on 2013-09-11
Surely someone must know something about this... 
After a fresh reboot, running only Kontact and Jitsi, I clicked on the first unread message and 15 minutes later I'm still waiting for it to be displayed. Meanwhile:
mysqld is at 13%, akonadiserver at 10%, Kontact at 6%, continuously.
also, virtuoso-t is using 3 to 6 % cpu

---

### Post by zerubbabel on 2013-09-11
Finally found a fix in this thread:
[http://forum.kde.org/viewtopic.php?f=154&t=117207&p=290895&hilit=+kontact+akonadi+4.11.1#p290895]("http://forum.kde.org/viewtopic.php?f=154&t=117207&p=290895&hilit=+kontact+akonadi+4.11.1#p290895")

---

