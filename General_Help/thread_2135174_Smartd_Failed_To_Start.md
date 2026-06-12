---
title: "Smartd Failed To Start"
date: 2013-04-13
forum: General Help
---

### Post by streat on 2013-04-13
Can anyone assist me in automation do Smartd with SATA drives exclusively? All modifications I have tried result in "smartd daemon failed to start" ubuntu 12.04

---

### Post by gordintoronto on 2013-04-13
What is it that you want to do? Disk Utility can display the Smart data, and you don't need a daemon to use it. Have you read what is displayed by: man smartd

---

### Post by streat on 2013-04-13
Ideally I would like to have all SATA drive scanned automatically on a schedule and have errors reported via email. These functions are all within the abilities of smartd but I cannot get it to start for the life of me utilizing the devicescan configuration recommended even with the -d sata addition to the configuration file

---

### Post by gordintoronto on 2013-04-13
Did you read: man smartd

Did you modify /etc/smartd.conf

Did you use the -d option?

---

