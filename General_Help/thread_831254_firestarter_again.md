---
title: "firestarter again"
date: 2008-06-16
forum: General Help
---

### Post by ramboza on 2008-06-16
I know this problem has been discussed 1000 times, but still no solution.
How can i open firestarter GUI without a password promt? Note that it's asking for the user's password, not the root's one.
Thank you.

adding user ALL=NOPASSWD:/usr/sbin/firestarter to /etc/sudoers won't work.

Still asking for [sudo[ password for user when sudo firestarter from terminal

---

### Post by nikgare on 2008-06-16
Why would you want it to open without a password?

Nik

---

### Post by dmizer on 2008-06-16
the firestarter gui must run as root, thus requiring a password to open it.

keep in mind though ... that your firewall is active on boot, even if you do not have your firestarter gui open.

---

### Post by Anduu on 2008-06-17
There is absolutely no need to have Firestarter running.It is a gui used to modify your firewall settings.Run it,type your password,do what you need to do and get out.

New users shouldn't be monkeying around with such critical things as the sudoers file.You are asking for trouble.

---

### Post by ramboza on 2008-06-17
I know the iptables is running without starting the firestarter. But it's very usefull monitoring tool. Network activity, traffic, attacks etc. So i'd like it to sit in the tray all the time...

---

