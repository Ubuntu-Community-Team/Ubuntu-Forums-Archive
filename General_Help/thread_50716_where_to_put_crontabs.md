---
title: "where to put crontabs?"
date: 2005-07-21
forum: General Help
---

### Post by gammyhand on 2005-07-21
When I installed clamav it showed me how to make a crontab. The trouble is, I have set up ubuntu to empty the tmp folder on reboot and this is where that crontab was created. Where else can I put crontabs so they work and what is the command?

---

### Post by dave9191 on 2005-07-21
The crontab file is in /etc/crontab. You can add an extra line at the bottom of the file to get things to execute on certain days / times. It can be edited wtih any text editor. But you have to be root to edit it. 

Dave

---

### Post by gammyhand on 2005-07-21
[QUOTE=dave9191]The crontab file is in /etc/crontab. You can add an extra line at the bottom of the file to get things to execute on certain days / times. It can be edited wtih any text editor. But you have to be root to edit it. 

Dave[/QUOTE]
 Thanks :)

---

### Post by dave9191 on 2005-07-21
No probs :) 

Dave

---

