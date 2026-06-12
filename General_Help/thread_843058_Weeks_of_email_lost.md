---
title: "Weeks of email lost"
date: 2008-06-27
forum: General Help
---

### Post by RayDeCampo on 2008-06-27
I'm on 8.04 (updated from 7.10) and using thunderbird for email.  I ran the latest updates for 2008/06/27 or so, I think there were mainly some SSL changes, I don't think thunderbird was included.  Anyway, restarted as the update dictated, everything seems fine, but when I open Thunderbird I have lost all emails since about 2008/5/18.  Same thing for my wife's account.  Also, when I started Firefox I got the update page again, which leads me to believe something similar happened with the Firefox settings.

I have been poking around in my home directory, looking for the lost email but none of the various Inbox files I have are dated past May 18th.  The current version of Thunderbird seems to be using ~/.mozilla-thunderbird/xxxxxxxx.default/ for the settings directory.

Anybody have any ideas?

---

### Post by schwascore on 2008-06-27
No real ideas on recovery, but you might want to consider using the IMAP protocol rather than the POP protocol for e-mail.  I'm assuming from the description of your problem that you are using POP, which downloads your e-mails to your computer and deletes them from your server.  IMAP, on the other hand, can download a copy to your computer at your request, but your e-mail remains on the server.  This not only frees you from your home computer/laptop but it also helps protect your e-mail from mishaps like what you described.

Just a suggestion...

---

### Post by RayDeCampo on 2008-06-28
Turns out that the issue was that the wrong partition was mounted on /home.  Last month I added a new larger hard drive and moved the /home partition to it.  For whatever reason, during this reboot Ubuntu reverted to the old /home partition.  A subsequent reboot mounted the partitions correctly.

---

