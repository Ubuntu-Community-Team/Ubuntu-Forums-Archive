---
title: "Lubuntu 15.10, Hybrid hibernate"
date: 2016-01-11
forum: General Help
---

### Post by christian92 on 2016-01-11
Hello

sudo pm-suspend-hybrid works fine, but i don know how i can change the System to enable it when i close the lid

At the Energy Settings of Xfce i can't select

If i can change it on console or change the normal Suspend-Script to have only Suspend Hibernate it also Work for me

Greetings CK

---

### Post by christian92 on 2016-01-12
Hi
i found now the key i had to set to enable hibernate: [http://www.florian-diesch.de/doc/ubuntu/ruhezustand-aktivieren.html](http://www.florian-diesch.de/doc/ubuntu/ruhezustand-aktivieren.html)

But i further can't select the hybrid Hibernate / hybrid suspend



I found the Difference, The XFCE seems to don't use the pm-tools

i change the configuraton of pm to go to hybrid-standby when i just call pm-standby, it work's
further in the log it&#347; nothing when i close the lid

where can i configure on console what to to when lid is closed? I thing it is another script

---

### Post by christian92 on 2016-02-15
Hi

the Problem further exist´s

Can i use anoter Tool like PM and kill Xfce?

---

### Post by christian92 on 2016-02-21
another long sunday, and something new:

i can kill xfce4-power if i type pkill xfce4

further i can activate Hybrid Hibernate in /etc/systemd/logind.conf when i set:

HandleLidSwitch=hybrid-sleep
LidSwitchIgnoreInhibited=yes


Now i don know how i can control the other functions from xfce-power or kill only the close-lid Function in XFCE-power





Ps, i renamed the xfce-power-manager because i can find from where it was started, it&#347; not in init.d
So it work for me, if anybody know where is the Starting Link i want to know


greetings ck

---

