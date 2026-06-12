---
title: "[SOLVED] command to know what the kernel is doing"
date: 2007-04-10
forum: General Help
---

### Post by nga911 on 2007-04-10
is there any command to know what the kernel is doing now or what it did .:confused:


to know what happens when i plug a usb device !

---

### Post by tommcd on 2007-04-10
lsusb
will list any usb devices pluged in.
lspci -v | grep usb
should give you the same, or perhaps additional info. Sorry, I'm at work now so I can't check this out myself.

---

### Post by g8m on 2007-04-10
dmesg gives some info.

or tail /var/log/messages will give the latest messages from the system.

top will give the running processes.

---

### Post by teaker1s on 2007-04-10
we are writing a beginners faq section, would you like to take a look, see what you think
[https://help.ubuntu.com/community/Beginners/FAQ?highlight=%28beginners%29#head-a651bed0d14d229d92250023c1c03e170be537aa]("https://help.ubuntu.com/community/Beginners/FAQ?highlight=%28beginners%29#head-a651bed0d14d229d92250023c1c03e170be537aa")

---

### Post by mcduck on 2007-04-10
> **g8m said:**
> dmesg gives some info.

or tail /var/log/messages will give the latest messages from the system.

top will give the running processes.

'tail -f /var/log/dmesg' or 'tail -f /var/log/messages'. 'tail -f' displays the last lines of a file, and then keeps on updating changes. Nice way to follow what's going on in your log files. Press 'Ctrl-C' to quit.

---

