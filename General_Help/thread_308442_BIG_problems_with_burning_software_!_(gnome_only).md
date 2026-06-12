---
title: "BIG problems with burning software ! (gnome only)"
date: 2006-11-28
forum: General Help
---

### Post by Axx83 on 2006-11-28
Hi everyone, I've tried all these progs today but no one succeded at burning a normal data cd and erase a cd-rw, in the end I tried sudo gnomebaker and it worked but I had these results in the terminal:

[SIZE="2"]** (gnomebaker:4894): CRITICAL **: dbus_g_proxy_connect_signal: assertion `DBUS_IS_G_PROXY (proxy)' failed

** (gnomebaker:4894): CRITICAL **: dbus_g_proxy_connect_signal: assertion `DBUS_IS_G_PROXY (proxy)' failed

** (gnomebaker:4894): CRITICAL **: dbus_g_proxy_call: assertion `DBUS_IS_G_PROXY (proxy)' failed

** (gnomebaker:4894): WARNING **: gbcommon_close_temp_file - Temporary file descriptor [/tmp/GnomeBaker-root/gnomebaker-TCR9IT] could not be closed

** (gnomebaker:4894): CRITICAL **: dbus_g_proxy_connect_signal: assertion `DBUS_IS_G_PROXY (proxy)' failed

** (gnomebaker:4894): CRITICAL **: dbus_g_proxy_connect_signal: assertion `DBUS_IS_G_PROXY (proxy)' failed

** (gnomebaker:4894): CRITICAL **: dbus_g_proxy_call: assertion `DBUS_IS_G_PROXY (proxy)' failed

** (gnomebaker:4894): CRITICAL **: dbus_g_proxy_call: assertion `DBUS_IS_G_PROXY (proxy)' failed[/SIZE]

I like gnomebaker the most but I don't want to run it in terminal everytime...where is the problem ? Windows with Nero (needless to say) works like a charm as it always did.

My mobo is nvidia geforce 6100/nforce 430 from gigabyte, amd athlon 64, normal and  quite cheap dvd rewriter double layer eide, sata II hard drive.

Will I have to install K3b ? Does it brings problems to load all kde in Ubuntu 6.10 ?

Thaaaaaaaaaaaaaaaaaaaaaaaaanks

---

### Post by Teamgeist on 2006-11-28
Before you try K3b, I suggest you give Brasero a shot.

[http://www.getdeb.net/getdeb.php?file=brasero_0.5.1-1getdeb1_i386.deb](http://www.getdeb.net/getdeb.php?file=brasero_0.5.1-1getdeb1_i386.deb)

Download the file, right-click on the package and choose "Install with gedebi" (<-- very first option on top of the menue)

Brasero works like a charm here.

---

### Post by Axx83 on 2006-11-28
I tried Brasero, it works even worse unfortunately...

My dvd writer is an "LG GSA-4160B" that i (now) updated to the last firmware, let's hope something changes...

---

### Post by wpshooter on 2006-11-28
Get **K3b** burning program.

The last time I tried it Gnomebaker was a piece of junk.

---

### Post by Axx83 on 2006-11-28
But i fear that loading all that kde lib will slow my pc...is that possible?

I like k3b too btw.

---

