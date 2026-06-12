---
title: "Path to locate errors Logs?"
date: 2020-08-13
forum: General Help
---

### Post by candylovergirl on 2020-08-13
Hello,

Installing Ubuntu 20.04 LTS I got an error, where the logs are stored?

Thanks
Camelia

---

### Post by Holger_Gehrke on 2020-08-13
For errors that happened during package installation or later there should be log files on the installed system in /var/log/installer. If the error happened earlier in the installation process - during partitioning for example - I don't think the installer has anywhere it can write to to leave a log ...

Holger

---

### Post by candylovergirl on 2020-08-13
> **Holger_Gehrke said:**
> For errors that happened during package installation or later there should be log files on the installed system in /var/log/installer. If the error happened earlier in the installation process - during partitioning for example - I don't think the installer has anywhere it can write to to leave a log ...

Holger

Thank you @Holger_Gehrke ):P

Camelia

---

### Post by Impavidus on 2020-08-13
Errors (or other logs) can also be stored on the live usb. I may have to look up the details, but I think that was new in 20.04.

---

### Post by candylovergirl on 2020-08-14
> **Impavidus said:**
> Errors (or other logs) can also be stored on the live usb. I may have to look up the details, but I think that was new in 20.04.

I do not have a live USB! I have installed Ubuntu from an CD that I create from an ISO

Thanks
Camelia

---

### Post by TheFu on 2020-08-14
Google found these reputable links about ubuntu log files.[LIST]
[*][https://ubuntu.com/tutorials/viewing-and-monitoring-log-files](https://ubuntu.com/tutorials/viewing-and-monitoring-log-files)
[*][https://help.ubuntu.com/community/LinuxLogFiles](https://help.ubuntu.com/community/LinuxLogFiles)
[/LIST]

---

