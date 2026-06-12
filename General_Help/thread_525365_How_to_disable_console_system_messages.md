---
title: "How to disable console system messages??"
date: 2007-08-14
forum: General Help
---

### Post by DKnight on 2007-08-14
I've installed a CLI only Ubuntu on an old laptop that has the USB broken. The problem is that Ubuntu detects that it is broken and floods the console constantly with
```
 [ XXXX.YYYYYY]  hub 1-0:1.0: over-current change on port 2 
```
Is there a way to hide these messages? I don't care if the USB is broken, I just want to use the command line. Right now is absolutely unusable; I can type commands, but I can't see the output because the error messages clog up everything lightning fast. They show up even in vi or nano.
Please help!:(

---

### Post by DKnight on 2007-08-14
I've been told to use **grep** but I've been reading the man and I cannot figure out how to use it to hide these messages. Help??:(

---

### Post by anaconda on 2007-08-14
I dont know if this works, but
if you press Ctrl-Alt-F2 and go to another terminal the error messages might stay on the first one..

---

### Post by DKnight on 2007-08-14
> **anaconda said:**
> I dont know if this works, but
if you press Ctrl-Alt-F2 and go to another terminal the error messages might stay on the first one..

Tried that already, no luck, they're everywhere!

---

### Post by thelinuxguy on 2007-08-15
Until there is some solution to this, you may get some relief with Ctrl+L which clears the screen. For commands issued on the terminal, like ls, it clears the output as well. So its not very usable in these cases. But if you are in vim, Ctrl+L redraws the screen. If you are in insert mode, press ESC followed by a Ctrl+L. This also seems to work when you are viewing man pages.

This is still a nuisance but may help till we get a solution.

---

### Post by thelinuxguy on 2007-08-15
You can try stopping the kernel logger. Let me know what happens by this:

```

sudo kill -TSTP `pidof klogd`

```
or if that doesn't work
```

sudo kill -KILL `piof klogd`

```

---

### Post by kostkon on 2007-08-15
An option would be to disable USB support if you don't care to use it. Maybe the messages will stop.

You could do it by adding the *nousb* to your boot parameters.

Alternatively, you could blacklist the USB drivers, by opening /etc/modprobe.d/blacklist and blacklisting the following modules:

[LIST]
[*]usbcore
[*]ehci_hcd
[*]uhci_hcd
[/LIST]

I would like to point out that I don't know if there would further consequences for your system if you disable USB.

---

### Post by DKnight on 2007-08-16
Thanks a lot for the replies guys, but unfortunately none of them worked (except CTRL+L which helped A LOT)
After some research, and a lot of trial and error, I found the solution, which is quite simple and clean (but very very very bad documented and hidden).
I just edited /etc/sysctl.conf, and changed kernel verbosity level from **4 **to **2** by editing this line:
```
kernel.printk = 4 4 1 7
```
The first number is the verbosity level, which by default is at 4. After the boot sequence is finished, the messages disappear.
Now the console is finally usable... phew.:)

---

### Post by thelinuxguy on 2007-08-16
I had tripped on the same thing but I came across [this page]("http://www.linuxjournal.com/article/2365") to change the level
```

echo 8 > /proc/sys/kernel/printk

```
It didnt work even with sudo so I dropped it.
Anyways glad that it worked out. I had also been haunted by this sometime back on an old machine. Now I know where to look.

BTW, [another page here]("http://publib.boulder.ibm.com/infocenter/tssfsv21/index.jsp?topic=/com.ibm.sanfs.doc/foj0_r_sanfs_client_linux_logging_tracing.html") shows how to redirect the messages to a file rather than changing the level. May come handy.

---

### Post by Crippa75 on 2008-06-26
> **DKnight said:**
> Thanks a lot for the replies guys, but unfortunately none of them worked (except CTRL+L which helped A LOT)
After some research, and a lot of trial and error, I found the solution, which is quite simple and clean (but very very very bad documented and hidden).
I just edited /etc/sysctl.conf, and changed kernel verbosity level from **4 **to **2** by editing this line:
```
kernel.printk = 4 4 1 7
```
The first number is the verbosity level, which by default is at 4. After the boot sequence is finished, the messages disappear.
Now the console is finally usable... phew.:)


This works for me :) (To disable the USB)
[INDENT]----------------------
Alternatively, you could blacklist the USB drivers, by opening /etc/modprobe.d/blacklist and blacklisting the following modules:

usbcore 
ehci_hcd 
uhci_hcd 
--------------------[/INDENT]
**BUT**
You must run **_update-initramf _**-u all 
(or with -k..)

---

