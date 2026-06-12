---
title: "Unable to add printer"
date: 2007-04-06
forum: General Help
---

### Post by derbyjon on 2007-04-06
I've installed Edgy onto a brand new HDD. Everything has gone fine until I try to add a printer for the first time. When I double-click the 'New Printer' icon, the gnome-cups-add dialogue box appears with "Reading printer database". Then nothing. The dialogue box stays there and appears to be dead. I've tried this several times, and left it for over an hour. Still no joy.

time lpinfo -m > /dev/null resulted in:
real    0m50.176s
user    0m0.304s
sys     0m0.172s

---

### Post by Puppy fam on 2007-04-06
I don't know what printer you have, but if you have a hp printer you could use [hplip]("http://hplip.sourceforge.net/"). If you do not have a hp printer I don't know what to tell you, meanly because I am very new to Ubuntu.

Hope this helps,
-Puppy fam

---

### Post by derbyjon on 2007-04-07
It's an old Epson. Any suggestions? Would it be safe to uninstall and then reinstall cups? Which packages specifically would I need to address?

---

### Post by derbyjon on 2007-04-07
I've reinstalled cups (server + client + common) to no avail.

If I stop cupsd I can get further (to the "add a printer" dialogue), but then the printer port drop-down list is empty and I can't proceed (I assume this is because cupsd isn't running?).

Can I get around this via the command line?

---

### Post by derbyjon on 2007-04-07
If I hook up gdb, the top of the backtrace when it appears to hang looks like:
(gdb) bt
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb74ac816 in pthread_cond_wait@@GLIBC_2.3.2 () from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb755ede3 in gnome_cups_request_execute_async () from /usr/lib/libgnomecups-1.0.so.1
#3  0xb7384528 in gcups_connection_selector_new () from /usr/lib/libgnomecupsui-1.0.so.1

Does anyone know what gnome_cups_request_execute_async() could be waiting for?

---

