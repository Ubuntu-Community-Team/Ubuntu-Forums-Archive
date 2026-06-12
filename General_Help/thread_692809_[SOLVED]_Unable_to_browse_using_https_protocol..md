---
title: "[SOLVED] Unable to browse using https protocol."
date: 2008-02-10
forum: General Help
---

### Post by ColdAir on 2008-02-10
Hello,

I'm facing a strange problem with my Ubuntu installation.
I can browse internet using any installed webbrowser in Ubuntu except for any websites using *_**https**_* protocol.

Initially I found that I'm not able to login to [www.gmail.com](www.gmail.com).
But then I noticed its any website which requires an _***https connection***_ with the client is not loading in my webbrowser (also using wget terminal command.).

I have a dual boot dell 1720 laptop with windows vista and ubuntu. 

Any help is greatly appreciated

Thanks in advance.

---

### Post by src2206 on 2008-02-11
Which browser are you using? Look in to the settings and see if there is any setting that you may need to tweak. If you are not using, try FireFox. In Add/Remove Software, in the Search box type Firefox and install the main browser package. See if this resolves your problem.

BTW, does your internet connection requires any special permission to enter a Secured Site?

---

### Post by ColdAir on 2008-02-11
Thanks for the reply.
I use FireFox mainly, also tried the other web browsers ([SIZE=-1]Epiphany and [/SIZE]Opera ) to check whether this problem is also present with those. And it seems this is not to do with web browser or its settings as I also tried using wget terminal command and no success. 
Anyway, FireFox settings shows the check box is checked to use SSL3.

My feeling is that, there are no special permissions required to enter a Secured Site using my ISP. The reason behind this thought is that everything connected to the web works fine from my second laptop (Win XP and OpenSuSE) and also from this laptop when booted into Windows Vista.
From all my PC/OS combination I'm using FireFox to browse internet. 
Except for Ubuntu, every other OS works fine with https.

I wanted to avoid Windows completely from my usage...but this one stuff is asking me to go back to Vista for checking mails and going some online banking etc which needs secure connection.

I have a feeling that if I could reinstall/ repair/ configure some modules connected to sockets/networking in my Ubuntu installation, this should get solved. 

Unfortunately I don't have the knowledge of How to in this area.
Its greatly appreciated if any of you could throw some light in this direction...

---

### Post by src2206 on 2008-02-11
Did you check the Security Settings in Ubuntu? It should be available under the Preference or Security (sorry not using Ubuntu right now, so can't be more specific).

---

### Post by ColdAir on 2008-02-11
It seems the problem is rectified now. 
Your question on Security Settings has made me recall that I have uninstalled the firestarter some time ago and probably this might have changed some settings in the system. 
So I did install firestarter again and the https connection is working now!!!


Earlier I have uninstalled firestarter due to some crash keep happening with this firewall program...I never expected it had some dependencies with the system working!!!

Anyway, thanks for the hint. 
Btn: Could you pls let me know how to reach "Security Settings" in Ubuntu? I tried looking all the menus, but no luck...

---

### Post by src2206 on 2008-02-11
Happy to be of some assistance :)

This might help you: [https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

Firestarter is the front end GUI of iptables (ie the so called firewall in Linux).

---

