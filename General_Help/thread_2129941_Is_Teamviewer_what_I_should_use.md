---
title: "Is Teamviewer what I should use?"
date: 2013-03-27
forum: General Help
---

### Post by clay7 on 2013-03-27
Hello,

I have several computers all on the same network and I need some way to log into each of them and be able to view their desktops and use their Terminals. Some of the computers are without monitors but all are running a desktop environment, all are unattended, and all are Ubuntu or Xubuntu.

Is Teamviewer a good program for this? How resource intensive is it?

Are there other programs that are better/less resource intensive?

---

### Post by jonobr on 2013-03-27
Teamviewer goes out to the internet and back in. so your going to have slow internet serviice if you do it that way,
Why not just remote desktop in [http://www.unixmen.com/how-to-use-remote-desktop-in-ubuntu/](http://www.unixmen.com/how-to-use-remote-desktop-in-ubuntu/)
Or better still control each maching using command line and SSH

---

### Post by clay7 on 2013-03-27
It looks like the Xubuntu machines don't have Desktop Sharing, but **X11VNC Server** shows up in the software center so I can use it.

As for SSH and command lines, I've tried that but some of these machines are used for bitcoin mining and, from my limited experience, the commands don't work over SSH. I don't quite understand the reason but it has something to do with the mining software being dependent on X (or Screen). I do other things over SSH but nothing related to mining.

I'll give X11VNC server a try.

Thank you!

---

### Post by The Spectre on 2013-03-27
TeamViewer should work fine.

It has a option for using on a Local Network...

[ATTACH=CONFIG]240626[/ATTACH]

---

### Post by clay7 on 2013-03-27
For others with the same challenge, I was able to install X11VNC Server on all of the remote machines, and they are working. For the client, I downloaded VNC Viewer on my Windows machine and it connects fine. I tried connecting via an Ubuntu virtual machine on Windows (Virtualbox) and it also works. I haven't had a chance to test the client on a regular Ubuntu installation yet, but from what I've seen, it should work.

As for resources consumed on the target (server) machines while X11VNC Server was running, htop showed about a 10MB increase in RAM and a slight increase in CPU...all very acceptable for my purposes.

Thanks all!

---

### Post by jonobr on 2013-03-28
> It has a option for using on a Local Network...

Thats why I love this forum, Im always learning

---

### Post by The Spectre on 2013-03-30
> **jonobr said:**
> Thats why I love this forum, Im always learning

I definitely agree with you, the Ubuntu Forums is a great source for learning new things.

I have learned much in my short time since switching from Window$ to Ubuntu by using these Forums and the many Ubuntu and Linux web sites that are out there.

---

### Post by AndyOpie150 on 2013-03-30
+1 ^
I also learn from my many mistakes and the great help recived in response to my mistakes.

---

