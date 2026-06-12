---
title: "startup/ shutdown issue with mount"
date: 2008-05-23
forum: General Help
---

### Post by zay2 on 2008-05-23
Hello!

I installed hardy heron the day it went live and im extremely satisfied with it. Is way better than gutsy was. Only thin left to fix for me is the problem with shutdown/startup.

I use my eeepc as office computer. I go to work, turn it on, plug in keyboard and mouse and start working. We have wireless network at work and since eeepc diskspace is limited i keep all documents in server. We have set up samba share and i have line in my /etc/fstab:

//server/serverdir /home/alan/Desktop/importantdir smbfs credentials=/root/.smbcredentials,dmask=777,fmask=777 0 0

it works just fine. Until i want to shut down the computer. unmounts or kills the process. whichever it does - im not sure. It takes ages to shut down because of that.
same with startup. it takes a while to figure out that the wireless is not yet up and it cant mount the damn stuff.

is it any way to bypass the mount at startup and mount it bit later or not mount at all if im on battery power and most important - is it possible to unmount it when computer shuts down?

Can anyone help me please?

Thanks.

Alan.

---

### Post by zay2 on 2008-05-25
bump

---

### Post by h4mx0r on 2008-05-25
Post the dmesg output issues. And please disable splash screen in /boot/grub/menu.lst so you can see what you are doing.

---

