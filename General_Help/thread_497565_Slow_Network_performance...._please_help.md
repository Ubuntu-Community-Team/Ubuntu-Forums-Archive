---
title: "Slow Network performance.... please help"
date: 2007-07-10
forum: General Help
---

### Post by jaguiler on 2007-07-10
Hi everyone - 

I am trying desparately to not have another Windows PC in my house.  So I setup Ubuntu 7 "Fiesty Fawn" on an old Toshiba Satellite Laptop....  model 2545xct (?) it is a 333 mhx Pentium with 192 mb RAM.
It runs pretty well, and after a few days I got it to work with my PCIMIA network card... Netgear WPN511

it connects to my home network, but at half the speed of my Windows PC's - next to the router, about 6 feet away I only get 50% signal - in another room it goes down to less than 20% - where a windows PC would be at 85% and up.  I am using the Atheros driver that came with the Fiesty Fawn install - ath_pci (?)

any ideas ?

also how do you get it to stop asking for a key ?  I have WEP enabled and my card is configured to use the WEP key, but then it keeps asking for another key password ?  I get by it by typing in my pswd but do I have to do this every time ?

thanks in advance !

---

### Post by jaguiler on 2007-07-11
still slow network - does anyone have any ideas ?

---

### Post by Rui Pais on 2007-07-11
an ipv6 issue?

try:
```
sudo sh -c "echo 'blacklist ipv6' >> /etc/modprobe.d/blacklist"
```

and then reboot (restart network is not enough... you need to reboot to kernel unload the ipv6 module)

---

### Post by misterhaan on 2007-12-29
thanks, disabling ipv6 seems to have fixed the speed issue for me (i'm running gutsy though).

i've found that i'm asked for my linux user password so that it can get the wpa2 password out of the password bank if i log in using my fingerprint, but not if i log in by actually typing my password.  i'd like to have it store the wpa2 password somewhere that isn't protected by another password so it doesn't ever have to ask -- any ideas on that?

---

