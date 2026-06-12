---
title: "Messed ubuntu server 16"
date: 2021-01-14
forum: General Help
---

### Post by haraldsnow on 2021-01-14
Hello, after locales change and reboot I am at this strange situation:

When I try to login to ubuntu from ssh or from keyboard on the computer the connection is closed immediately. 
When I type wrong pass it trows wrong password message. When I try to reach the computer via sftp it says protocol error. 
Before server the server crash i have tried to understand that - [autospawn] core-util.c: xdg_runtime_dir (/run/user/0) is not owned by us (uid 110), but by uid 0!
And obviously messed.
Boots "normal", all services are running.

Can you please give some advice how to "unbrick" without reinstalling.

---

### Post by TheFu on 2021-01-14
Restore from backups.

---

