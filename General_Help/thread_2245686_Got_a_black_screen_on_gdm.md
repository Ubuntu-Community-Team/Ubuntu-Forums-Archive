---
title: "Got a black screen on gdm"
date: 2014-09-25
forum: General Help
---

### Post by holliswuhollis on 2014-09-25
Hi,

I have installed ubuntu gnome. I can use it normally last time. But now, I can't use GDM to login. When I boot into Ubuntu (I am using duel-boot, by the way), I got a black screen with nothing on it.

I have switched to tty2 and try to fix it. When i type "startx", the screen goes black. But I can still use tty3 and so on.

I have also ran "sudo /etc/init.d/gdm stop". It returned "/etc/init.d/gdm 79: syntax error: "fi" unexpected". Don't know if it is the problem.

I am using AMD R9 280x display card with AMD driver(download from amd. Don't know what the name is :P ). This driver can work normally before this happen.

If you need any information, please leave a comment. I will post them as soon as I can.

---

### Post by holliswuhollis on 2014-10-10
I know this post have been a long time, but hey, I have solved the problem. Just want to post it here for my future reference and for those faced the same problem can come here.

I have just faced the same problem once again(reinstalled ubuntu when I faced it last time, that cause me few hours for re-installing all my packages:evil:). The cause is because I have updated my Kernel and fglrx did not add its module into kernel and rebuilt it.

To be specify, this problem is caused by X11. It will crash(?) or failed to build interface when fglrx do not have kernel module in kernel.

I solved this problem by typing the following command through tty2 (Ctrl+Alt+F2 after grub)

```

cd /lib/modules/fglrx && sudo ./make.sh && cd .. && sudo ./make_install.sh

```

This have to be executed every time when kernel is updated.

---

