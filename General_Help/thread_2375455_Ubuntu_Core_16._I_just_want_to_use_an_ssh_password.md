---
title: "Ubuntu Core 16. I just want to use an ssh password not ssh key pairs."
date: 2017-10-24
forum: General Help
---

### Post by BL86vYR on 2017-10-24
I am running a Nextcloud 11 instance on a Raspberry Pi 2 with Ubuntu Core 16.

I initially set up the Pi about two months ago, went through the First Boot procedures and was able to ssh into the box, and everything was great. Then about two weeks ago, I attempted to ssh into the box and was greeted with a password prompt for [EMAIL="UbuntuSSO@192.168.X.XXX"]UbuntuSSO@192.168.X.XXX[/EMAIL], which doesn't exist.

I didn't have anything important on the Pi, so I just reformatted/recreated the whole system. I went though the First Boot procedures and was able to ssh into the box and everything was great. Then today, I attempted to ssh into the box and was greeted with a password prompt for [EMAIL="UbuntuSSO@192.168.X.XXX"]UbuntuSSO@192.168.X.XXX[/EMAIL], which doesn't exist.

What am I doing wrong? The necessary ssh keys has been properly uploaded to Ubuntu One and is in the correct location on my PC.

What I really want is to get rid of this entire ssh-keypair-external-SSO system. I just want a normal ssh password like every other machine on my LAN, and don't want to have to bother with the maintenance of these keys. I do not and will never have an internet-facing open port 22 and my ssh password is very long. Can anyone explain what I need to do to make this happen if it is even possible? Thank you!

---

### Post by QIII on 2017-10-24
Near duplicate of [https://ubuntuforums.org/showthread.php?t=2373399](https://ubuntuforums.org/showthread.php?t=2373399)

Closed.

---

