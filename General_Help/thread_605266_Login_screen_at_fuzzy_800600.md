---
title: "Login screen at fuzzy 800*600?"
date: 2007-11-06
forum: General Help
---

### Post by eheyl on 2007-11-06
Hey all! I'm on a geforce fx 5200. I installed what I thought was a new driver and everything died. So I popped another card in and got everything back to the way it was 1280*1024. BUT! The login screen looks like its a 800*600 and a bit fuzzy not unreadable. Can anyone tell me why this happened or how to fix it. I know its a small thing but I'm a perfectionist and I'm a bit stumped. 

I did do a search but nothing covered this particular problem

Thanks
Erik

---

### Post by lyndaj70 on 2007-11-06
Hi Erik!

I don't know if it will help.... but on system>administration>login window, near the bottom of one of the tabs is a button that says "configure x server."  Maybe that would help fix it?   It's the only thing I can think of off the top of my head...

Hope it helps,
~Lynda

---

### Post by eheyl on 2007-11-06
Thanks I'll check it out. I noticed something else: before I was able to switch users and have my wife log in. Now when I try that it seems either to hang or work but I get no screen I am not sure which.

---

### Post by dcstar on 2007-11-07
> **eheyl said:**
> Thanks I'll check it out. I noticed something else: before I was able to switch users and have my wife log in. Now when I try that it seems either to hang or work but I get no screen I am not sure which.

Make sure that your have the **discover1** package installed, then In a terminal:

```
sudo dpkg-reconfigure xserver-xorg
sudo /etc/init.d/gdm restart
```
and accepting the defaults should set up things correctly.

---

### Post by eheyl on 2007-11-07
thanks dcstar! it worked. I'd love ot know how you remember that? I realize I'm new but there just seems to be so much to learn in terms of CLI. I can't wait!

---

