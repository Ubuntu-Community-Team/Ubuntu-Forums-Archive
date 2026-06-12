---
title: "ALT+S not working in Windows Remote Desktop accessed through Remmina"
date: 2015-05-29
forum: General Help
---

### Post by Rock 'n' Linux on 2015-05-29
Hello,

I am using the Remmina Remote Desktop client to access a Windows 2008 R2 server at work, which has a standard Microsoft Office environment.  For some reason, the ALT+S shortcut used  to send an e-mail in Outlook stopped working.  The exact symptom is that the ALT key press is sent (as there are some tooltips popping up), but nothing happens when the "S" key is pressed.  I am not aware of any other shortcuts not working.

Since this problem does not exist when accessing the same server from a Windows client, I assume that something in Ubuntu is capturing the "ALT+S" shortcut.  The problem is that I cannot find the culprit as nothing happens when pressing ALT+S in Ubuntu either, and the short-cut is not listed in the general keyboard short-cuts settings.

I am not sure since when this error occurs, but I believe it may have only started since the upgrade to 15.04.  Unfortunately, I am not certain as didn't use Ubuntu very regularly with remote desktop before as the timezone setting that was sent to the Windows server was not working and all times were shown in UTC, which made everything very cumbersome as I work with a lot of appointments in Outlook.  Since this issue was fixed in 15.04, I started using Ubuntu almost exclusively, also to access the remote Windows server.

A few pieces of information on my system:

- Standard Ubuntu 15.04 (fully updated, 64 bit).  Installed first with 8.10 Intrepid and always upgraded since.  Dual boot with Windows 8.1 Pro 32 bit (always upgraded since Vista Home Premium).
- Language of Ubuntu is English, keyboard is German.
- PC is an 18.4" Acer Aspire 8930G laptop from 2009 with 128 GiB SSD and 1.5 TiB HDD, which has a full-size keyboard.
- Remmina is at version 1.1.1-1ubuntu1 (nice version number!)
- libfreerdp is at version 1.1

Would any other information be useful?

Does anybody have any hints how I could find out what is capturing ALT+S?

Thanks!

---

### Post by cmcanulty on 2015-05-29
I find many keyboard combinations don't work for me when accessing both win 7 and ubuntu machines remotely, they instead apply to the local laptop I am on

---

### Post by Rock 'n' Linux on 2015-05-29
Thanks.  Based on your post, I tried other shortcuts and found that ALT-TAB did not work either.  So I searched for others having problems with ALT-TAB, and found the solution.  It is so easy that I am unsure how I searched for at least an hour before and did not find it.

Simply press the right control key.  Or click the keyboard icon in the popup menu at the top of the screen.  It seems to be persistent as well, so this issue is solved!

---

### Post by cmcanulty on 2015-05-29
OK cool thanks that will help me a lot

---

