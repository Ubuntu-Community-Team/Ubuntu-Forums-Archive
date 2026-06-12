---
title: "Ubuntu Live USB + Casper-rw Persistence + Dropbox"
date: 2014-12-28
forum: General Help
---

### Post by darkcammo on 2014-12-28
Hello,

I'm having a very specific problem with dropbox on Ubuntu 14.04 LTS. This particular installation is to a flash drive using casper-rw persistence. I used [this]("http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/") tutorial for installation.

The problem is that dropbox stores it's login credentials somewhere outside of the persistence, so every time I restart, the file is wiped and I have to re-enter my dropbox username and password. This isn't a hugely terrible problem, but midly irritating because every time I do it, dropbox sends me another welcome email.

So, my knowledge of how casper-rw works is next to none. Is there any way for me to include the missing dropbox file in the persistence? Or a way to tell dropbox to save that information in the persistence?

Thanks in advance for the help!

---

### Post by yancek on 2014-12-28
The dropbox directory should be in your /home/user directory per the site below.  Do you have it there?  Is anything in it?  Have you tested persistence by creating a directory/file and rebooting to verify persistence?

[https://www.dropbox.com/en/help/321](https://www.dropbox.com/en/help/321)

---

### Post by darkcammo on 2014-12-28
The issue isn't with the dropbox folder itself. The dropbox folder is still there when I reboot.

The issue is with dropbox's internal program files. It stores the file that remembers one's username and password outside of the persistence.

---

