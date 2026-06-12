---
title: "Input/Output error"
date: 2008-04-07
forum: General Help
---

### Post by kiwi_matamata on 2008-04-07
Hi,

I'm a newbee to linux and I was trying to instal ubuntu using wubi to get a feel for it. I get the following error message when I try and boot ubuntu.

init: Unable to execute "/sbin/getty" for tty3: Input/Output
init: tty4 main process (4731) terminated with status 255 error
init: tty4 main process (4732) terminated with status 255 error
init: tty4 main process (4733) terminated with status 255 error
init: tty4 main process (4734) terminated with status 255 error
init: tty4 main process (4735) terminated with status 255 error
init: tty4 main process (4736) terminated with status 255 error
init: tty4 main process ended, respawning
init: tty4 respawing too fast. spotted

Does anyone have any idea of what to do?

Peter

---

### Post by ago on 2008-04-07
Hi can you try to boot in rescue mode and see what happens?

---

### Post by ago on 2008-04-07
You might want to subscribe to the following bug: [https://bugs.launchpad.net/wubi/+bug/204133](https://bugs.launchpad.net/wubi/+bug/204133)

The more info you guys can provide the easier it is to fix it.

---

### Post by ago on 2008-04-07
Even more interesting, when you boot press esc after selecting "Ubuntu", then press "e" once to edit the first boot option, and press "e" on the kernel line to edit it. Append:

init=/bin/sh

Press enter and then "b" to boot.

Now you should be able to boot and end-up in a shell

Can you test that the filesystem is rw by writing something?

touch /test.trash

Also run 

/bin/ntfs-3g.probe

and report the output

---

### Post by kiwi_matamata on 2008-04-08
I've tried touch /test.trash but it says that I can only read. How do I change to rw?

---

### Post by ago on 2008-04-08
after you boot with init=/bin/sh

try to run the following command (watch the white spaces):

for x in /etc/rcS.d/S*;do [ -x "$x" ] && $x start; done

See if there is any error and if after that / is rw

---

### Post by kiwi_matamata on 2008-04-13
None of what you suggested worked on my machine. I've gone back to an earlier version of wubi (7.10) and the istall worked great. Thanks for your help

---

### Post by ago on 2008-04-14
That should have been fixed
But you have to use the latest daily ISO withe the latest wubi

---

