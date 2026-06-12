---
title: "Missing Virtual Terminals"
date: 2008-01-05
forum: General Help
---

### Post by DaveQB on 2008-01-05
Hi all

Somehow my VT's are missing.  Well when I go to them [ALT+CTRL+F1 etc] I get a black screen and a flashing cursor, thats it.  Can't login at all.

```
ps ax | grep tty
 5293 tty4     Ss+    0:00 /sbin/getty 38400 tty4
 5294 tty5     Ss+    0:00 /sbin/getty 38400 tty5
 5296 tty2     Ss+    0:00 /sbin/getty 38400 tty2
 5299 tty3     Ss+    0:00 /sbin/getty 38400 tty3
 5301 tty6     Ss+    0:00 /sbin/getty 38400 tty6
 5879 tty7     SLs+   1:14 /usr/bin/X -br -nolisten tcp :0 vt7 -auth /var/run/xauth/A:0-yryOoa
17311 tty1     Ss+    0:00 /sbin/getty 38400 tty1


```

killing a tty brings it back automatically.

But they are all useless.

Where should I begin troubleshooting this one ??

Thanks

---

### Post by oldos2er on 2008-01-06
Remove "vga=xxx" from /boot/grub/menu.list .

---

### Post by dlegend on 2008-01-06
Try doing these commands in a standard terminal (xterm, gnome-terminal, etc..):

```

sudo modprobe vga16fb
sudo modprobe fbcon

```

Now try and go back into the virtual terminal. If it works then:

Go to your /etc/modules file and edit it. Add **vga16fb** and **fbcon** as separate lines at the end of the file. This will have the modules automatically load on startup.

See this thread for more info (it is listed in the "Known gutsy bugs and workarounds thread"): [http://ubuntuforums.org/showthread.php?t=582962](http://ubuntuforums.org/showthread.php?t=582962)

Let me know if this works.

---

### Post by DaveQB on 2008-01-08
Thank you.

I will try that tonight.  Great find dlegend

---

### Post by JacobSteelsmith on 2008-01-17
Thanks for that fix! worked perfect for me.

---

