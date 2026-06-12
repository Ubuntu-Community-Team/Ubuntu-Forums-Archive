---
title: "Ubuntu 12.04 prompts for password twice, hangs on second attempt"
date: 2014-04-14
forum: General Help
---

### Post by Rhemat on 2014-04-14
Heya all,

I woke up my computer today, and it just went to a black screen.  I went to tty1, and tried to startx (that failed), then rebooted (sudo shutdown -r now).  After that, it booted up normally, and typed in my password.  Then it greeted me with the exact same login in screen, and after typing the password in a second time, it says logging in, but never logs in.

I tried a solution I found here:

[http://askubuntu.com/questions/319697/unable-to-log-in-and-unable-to-reset-the-password]("http://askubuntu.com/questions/319697/unable-to-log-in-and-unable-to-reset-the-password")

I used the first solution, which has you remove Xauthority (it didn't exist), and then remove ./config/autostart.  However, I am still plagued by this problem.

Any help would be appreciated as I do not want to have to reinstall everything again.  Thanks in advance.

---

### Post by Rhemat on 2014-04-14
I was able to resolve it.

I should have removed the .Xauthority in my own home directory.  After doing so, reboot, and log in works.

Hope this helps other people as well.

---

