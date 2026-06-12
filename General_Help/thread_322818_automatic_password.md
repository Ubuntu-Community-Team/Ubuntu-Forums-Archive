---
title: "automatic password"
date: 2006-12-21
forum: General Help
---

### Post by Lukich on 2006-12-21
Hi.  Due to the fact that I have a lot of data that I need to shuffle between different drives, I constantly need to check my disk space and every time I launch the utility it asks me for a password.  I was wondering if there's a way to modify the start up script for this utility so that it would somehow read the password automatically?
Thanks a lot,
Luka

---

### Post by aysiu on 2006-12-21
What utility is it?

---

### Post by Lukich on 2006-12-21
It's disk utility in the Administration section.  The line to launch it is:
gksu disks-admin

---

### Post by yopnono on 2006-12-21
> **Lukich said:**
> It's disk utility in the Administration section.  The line to launch it is:
gksu disks-admin

Use ```
df
``` in the terminal

---

### Post by xopher on 2006-12-21
Or gnome-system-monitor for that matter.

If you want to have the free space displayed on your desktop at all times, try conky, or if you prefer a bit easier app, gdesklet has many desklets that do this.

---

### Post by aysiu on 2006-12-21
First, find out where the launcher is for *disks-admin*. Let's just say, for this example, it's /usr/bin/disks-admin. You can find out by typing ```
locate disks-admin
``` We're also going to assume your username is *lukich*.

You want to edit the /etc/sudoers file using this command: ```
sudo visudo
``` Then, at the end of the file put in this line: ```
lukich ALL = NOPASSWD: /usr/bin/disks-admin
``` And then save. I'm not sure if you need to do something to refresh stuff ( log out, reboot), but this should make it not prompt you for a password for that command any more.

---

### Post by Lukich on 2006-12-21
Thank you very much!

---

### Post by aysiu on 2006-12-21
> **Lukich said:**
> Thank you very much!
So it worked?

---

