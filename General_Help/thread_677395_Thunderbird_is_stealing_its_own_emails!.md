---
title: "Thunderbird is stealing its own emails!"
date: 2008-01-24
forum: General Help
---

### Post by Bionic Apple on 2008-01-24
I have Thunderbird 2.0.0.6 on Windows and Ubuntu and it is great.  Except, there is one major problem.  I can't read emails on Linux Thunderbird that the Windows Thunderbird got and vice versa.  I think it might have to do with the Gmail settings, but I am not sure.  Could it be because I was using POP instead of IMAP (I just changed it to IMAP because Gmail recommends it for Thunderbird 2)?

---

### Post by sekinto on 2008-01-24
If you have Gmail you have to uncheck the "delete messages from server after download" option.

---

### Post by Bionic Apple on 2008-01-24
In Thunderbird or Gmail?  I can't find it in either, unless your are talking about the POP option in the Gmail settings.  That doesn't help then, because I use IMAP.

---

### Post by Xbehave on 2008-01-24
you could use a shared profile on one of the partitions
to use the windows profile would be easy
to use the linux profile just install ext2 drivers and the rest is easy

---

### Post by FuturePilot on 2008-01-24
That's the way POP works. Once you download the new emails you can't download them again.

---

### Post by michaelzap on 2008-01-24
Gmail POP is not like regular POP, unfortunately. With ordinary POP email you could set one (or both) of your client programs to leave the email on the server and you could download the same emails to different clients that way. But Gmail POP will not redownload the same emails to another client, no matter what your settings are.

Try using IMAP instead. Gmail's IMAP support is very good, and you can check from multiple clients using IMAP with no problems. You could also use POP on one client and IMAP on the other if you want to mix it up (just don't use POP on two clients).

You can force Gmail to redownload all of your email to one of your clients, or you can get just the last 30 days, but these kludges are designed just for occasional fixes and not regular use (see the Gmail forums for more info).

---

### Post by Bionic Apple on 2008-01-24
Alright, thanks guys.  So I guess I should just switch to IMAP and my problem goes away?  Wow, that's pretty easy.

---

### Post by michaelzap on 2008-01-24
You might appreciate [this guide]("http://www.howtogeek.com/howto/internet/setting-up-gmail-imap-support-in-thunderbird-2x/") to setting up Gmail IMAP in TB.

---

