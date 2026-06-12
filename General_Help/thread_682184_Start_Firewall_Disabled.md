---
title: "Start Firewall Disabled"
date: 2008-01-29
forum: General Help
---

### Post by gruss on 2008-01-29
I just want to have a firewall start in the disabled state.  Typically I"m at home behind my own hardware filrewall and dont need one on my pc too, but occasionally I want to leave the safety of my firewalled home land and be able to click a button and turn it on.  Will Lokkit or GuardDog let me do this?  I tried Firestarter but no matter what everytime you turn the pc on the firewall is enabled.  Just seems like a very simple thing, I know security is big in Ubuntu, but c'mon, I'm a big boy I can remember to put on my protection when I step out ;)

Any ideas let me know...

---

### Post by bodhi.zazen on 2008-01-29
yea, firestarter kind of takes over the place >_<

I suggest you work directly with iptables

Start firestarter 

sudo sh "iptables-save > /root/firewall-on"

now deactivate your firewall and again 

sudo sh "iptables-save > /root/firewall-off"

Now remove firestarter

sudo sh "iptables-restore < /root/firewall-off"

Save your changes

sudo iptables-save  #< -  This step will save your firewall in the off setting

Now to activate your firewall

sudo sh"iptables-restore < /root/firewall-on"

And to disable

sudo sh "iptables-restore < /root/firewall-off"

---

### Post by gruss on 2008-01-30
OK I think I'm usnderstanding the lingo, I'll give that a shot, thats much better than having to disable it everytime I boot.  Thanks man.

---

