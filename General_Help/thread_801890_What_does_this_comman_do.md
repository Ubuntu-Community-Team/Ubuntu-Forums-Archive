---
title: "What does this comman do"
date: 2008-05-21
forum: General Help
---

### Post by boorishid on 2008-05-21
Hi im new to ubuntu, i just installed it on my laptop and finally got the wifi working using ndiswenrapper. Anyways ive been using gentoo for a while but basically just the command line on computers with very simple hardware and wired networks. Ive never really had to "pull teeth" to get linux up and running like i did with this laptop. Anyways i have some piece of trash atheros wifi card in the laptop and ndis wouldnt connect to any of the networks in the list until i threw this command in my gnome>sessions area 

sudo /sbin/ifconfig wlan0 hw ether 00:1E:4C:2D:7F:0A

I read this solution in a forum, im just curious what that commands acually doing and what all the hex is? I also tried it in shell script that started in run level 5 and that didnt work. It seems weird to me it only seems to work after gnome is loaded.

---

### Post by sdennie on 2008-05-21
I believe that command is explicitly setting a MAC address for your wireless card.  I have no idea why that would make any difference.

Where did you put your startup command?  I would try putting it in /etc/rc.local.  It gets run at the very end of the boot sequence and so the card should be initialized by then.

---

### Post by boorishid on 2008-05-21
well originally i had made an executable bash script and put it in /etc/init.d and threw a link in etc/rc5 but that didnt work so i just added it it in the gnome sessions.

---

### Post by jocko on 2008-05-21
> **boorishid said:**
> well originally i had made an executable bash script and put it in /etc/init.d and threw a link in etc/rc5 but that didnt work so i just added it it in the gnome sessions.

Isn't runlevel 2 the default? Try adding the link in /etc/rc2.d (or even all rc*.d except rc0.d and rc6.d just to be sure)?

---

### Post by jespdj on 2008-05-21
Tip: The "man" command (for "manual") gives information about what programs do. In the command above, you're running the program "ifconfig". To see what ifconfig does and what the options are, type this in a terminal:
```
man ifconfig
```

---

