---
title: "Network problem - can ping other lan hosts, they cant ping me!"
date: 2005-10-14
forum: General Help
---

### Post by TheYetiMan on 2005-10-14
Hi there,

I have installed kubuntu 5.10 on an old PIII 450 with a wireless nic (atheros chipset). I have managed to set up WPA using wpa supplicant, and have set up a static IP. It has access to the internet via my router and is able to ping all lan hosts with no trouble.

However, it seems that I cannot ping the kubuntu machine from ANY other host on the lan - which makes absolutely no sense to me at all. Can anyone help?

ifconfig reports:

ip: 192.168.1.125
broadcast: 192.168.1.255
mask: 255.255.255.0

if i try "ping 192.168.1.125" from the kubuntu machine it works fine so I assume it isn't blocking ping requests.

(i would copy and paste but the machine it is installed on is in a dingy little room and there is no space to use a keyboard properly so I'm using my own machine :D)

Thanks in advance,

Yeti

---

### Post by ngms27 on 2005-10-14
This suggests a Firewall is in use!

JonnyT

---

### Post by TheYetiMan on 2005-10-14
[QUOTE=ngms27]This suggests a Firewall is in use!

JonnyT[/QUOTE]

OK - this had crossed my mind. how do I find out if a firewall is running on my kubuntu box? I certainly didn't set one up but perhaps it has one by default?

Any help would be greatly appreciated - it's doing my head in! :)

---

### Post by pipodnmy on 2005-10-14
iptables -L
(running this as root helps)

---

### Post by TheYetiMan on 2005-10-14
awesome! Did some delving and found that iptables was running (lsmod). I turned off ipfilter_table and ip_tables using modprobe -r and now I can see my kubuntu box from other machines!! Wahoo!

However...... I ran iptables -L before removing it with modprobe and it seemed to have nothing listed - just said 3 things with 

"POLICY ACCEPT"

along side them and a load of headings, but no entries. So..... why would this be blocking my other lan boxes from accessing it if there are no rules set up?? I'm really a n00b to iptables so maybe someone more experienced can explain.

for now though, thanks for the input guys!

Yeti

*********** EDIT ************

OK maybe that was a bit premature. It worked (I could ping from my Windows box to the kubuntu box for about a minute) then it decided it didn't want to work again. So then i went back to the kubuntu box and tried to ping the other way - it was working fine. Then back to the windows box and I could ping the kubuntu again... very strange indeed :-/

But wait there's more!!! :D

I went onto my other linux box (running Mandrake 10.1) and typed "ping 192.168.1.125" and it cannot find the host - returns "host unreachable" - even when the windows box CAN ping the kubuntu box.... hmmm

This is all very bizarre - I just don't get it :-/

I'm starting to think there is something up with the atheros driver / wpa supplicant / router combo that just is not sitting well with my network. Oh well - I shall persevere....

---

