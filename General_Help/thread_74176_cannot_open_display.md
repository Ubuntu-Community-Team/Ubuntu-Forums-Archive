---
title: "cannot open display"
date: 2005-10-11
forum: General Help
---

### Post by GhodMode on 2005-10-11
I recently switched from RedHat (Fedora Core). I installed xampp (lampp) and created a webadmin user that I want to use only for administration and configuration of xampp. Here are my results from Gnome Terminal:

```
su - webadmin
Password:
webadmin@ubuntu:~$ gvim /opt/lampp/htdocs/index.html
E233: cannot open display
``` 
In the olden days, I think this would be fixed using [FONT=Courier New]xhost +*hostname_or_ip*[/FONT], but this doesn't work and I've read that this method may have been deprecated.

So, I want to be able to use the X server from any session which originated on localhost. If I must set the permissions per user, then I will. But it doesn't seem to be related to the user, either, because I can [FONT=Courier New]su -[/FONT] to my own user and get the same error message.

Any help would be greatly appreciated.

-- Vince

---

### Post by perlmonger on 2006-01-19
I've  got the same problem. I've fixed this many times on solaris by 'setenv DISPLAY ip_address:0.0' but for bash you would use export instead of setenv. This doesn't work in Ubuntu. What gives. I see you didn't get any replies but maybe the bump will get us both some help.

---

