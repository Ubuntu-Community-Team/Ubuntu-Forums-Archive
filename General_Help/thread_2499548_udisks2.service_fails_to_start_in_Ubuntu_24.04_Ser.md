---
title: "udisks2.service fails to start in Ubuntu 24.04 Server, screenhots from Cockpit."
date: 2024-07-30
forum: General Help
---

### Post by papriak on 2024-07-30
Today I booted the system I use for long-term backups.  Unlike last time, it's unable to start the udisks2 service when booted, nor when I click on "Start service".

I use Cockpit to manage the system remotely, and I don't know what steps to take to fix the issue.

I have attached the following screenshots containing what I believe is all the relevant information.


[IMG]https://ubuntuforums.org/attachment.php?attachmentid=294039&stc=1[/IMG][IMG]https://ubuntuforums.org/attachment.php?attachmentid=294038&stc=1[/IMG][IMG]https://ubuntuforums.org/attachment.php?attachmentid=294037&stc=1[/IMG]

---

### Post by currentshaft on 2024-07-31
Open terminal and run "journalctl -u udisks2.service" to see recent logs about it.

---

### Post by papriak on 2024-07-31
> **currentshaft said:**
> Open terminal and run "journalctl -u udisks2.service" to see recent logs about it.

Done, I uploaded the output to Pastebin.

[https://pastebin.com/g1zudGBZ](https://pastebin.com/g1zudGBZ)

---

