---
title: "Disabling guest user account in ubuntu 12.04.3 with unity"
date: 2013-10-24
forum: General Help
---

### Post by jsvidyad on 2013-10-24
Hello,

   I am running ubuntu 12.04.3 with the unity desktop. The login screen of unity has a guest user account. The guest access is available even when I have locked the screen while using an user account. How can I disable the guest user account in unity on ubuntu 12.04.3 ?

---

### Post by ibjsb4 on 2013-10-24
The guest account is not part of Unity, but your 'display manager' which is 'lightdm'.

First link should work

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=disable+guest+account+lightdm&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=disable+guest+account+lightdm&sa=Search&cof=FORID:9)

---

### Post by jsvidyad on 2013-11-14
Hello,

   I didn't get what you're trying to say.

---

### Post by steeldriver on 2013-11-14
You can edit the /etc/lightdm/lightdm.conf file directly, adding 

```
allow-guest=false
```

to the [SeatDefaults] section, or use the lightdm-set-defaults utility

```
sudo /usr/lib/lightdm/lightdm-set-defaults --allow-guest false
```

---

### Post by jsvidyad on 2013-11-22
Thank you for your help.

---

