---
title: "Gaim Exits, kernel 2.6.20-5-generic"
date: 2007-02-22
forum: General Help
---

### Post by Aurdal on 2007-02-22
Hey, I upgraded to the kernel from Feisty in order to get the drivers for my network hardware.

But, ever since, I did that, gaim keeps exiting (not just logging off, the program is terminated) at random intervals. I have no idea whether these two things have anything to do with each other, but I can't think of anything else...

So, does anyone have any idea as to what I can do to fix this? (I have the gaim version from the edgy repositories.)

-Kristoffer Aurdal

---

### Post by zanglang on 2007-02-22
It's more likely a gaim development bug. Try running 'gaim -d' from command line and see if gaim spews out any error messages before dying.

---

### Post by Aurdal on 2007-02-25
Thank you for replying. :)

It worked for quite some time now, but it did stop eventually:

```
g_log: msn_object_get_creator: assertion `obj != NULL' failed
g_log: msn_object_get_sha1c: assertion `obj != NULL' failed
Segmentation fault
aurdal@tree:~$ dns[3604]: Oops, father has gone, wait for me, wait...!


```

---

### Post by zanglang on 2007-02-27
You might want to post the messages and other info on Gaim's bug tracker. And that is one bizarre error message I must say... :roll:

---

### Post by Aurdal on 2007-02-27
Where can I find the bug tracker? :)

---

### Post by maddbaron on 2007-02-27
I get the same problem. gaim just randomly shuts down. I have no plugins working. I did gaim -d and I received no error message. I get an error message when I open it.
> libnm_glib_nm_state_cb: dbus returned an error.
  (org.freedesktop.DBus.Error.ServiceUnknown) The name org.freedesktop.NetworkManager was not provided by any .service files


I don't have dbus enabled.

---

### Post by zanglang on 2007-02-28
> **Aurdal said:**
> Where can I find the bug tracker? :)
[http://gaim.sourceforge.net/bug.php](http://gaim.sourceforge.net/bug.php)

> **maddbaron said:**
> I get the same problem. gaim just randomly shuts down. I have no plugins working. I did gaim -d and I received no error message. I get an error message when I open it.
Gaim was trying to query for network-manager... shouldn't it skip that since you don't have dbus? Might need to file a bug as well...

---

