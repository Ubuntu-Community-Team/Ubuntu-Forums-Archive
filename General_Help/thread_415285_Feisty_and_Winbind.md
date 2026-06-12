---
title: "Feisty and Winbind"
date: 2007-04-20
forum: General Help
---

### Post by sefs on 2007-04-20
On upgrading to feisty ... feisty auto uninstalled winbind.  On reinstalling tru synatic i get this far

Setting up winbind (3.0.24-2ubuntu1) ...
 * Starting the Winbind daemon winbind    

then its stuck here.  How should i proceed.

Thanks.

---

### Post by sefs on 2007-04-20
I killed synaptic
and its telling me to run dpkg --configure -a which does not complete because its stuck at starting the winbind deamon.

So now i am unable to access synatic.

what to do.

---

### Post by sefs on 2007-04-20
ok this is solved due to incorrect line ins /etc/samba/smb.conf

the line is     interfaces = lo, wlan0

and had to change it to     interfaces = lo, eth1, until i can get my wireless working again on feisty.

---

### Post by msak007 on 2007-04-24
Wow I can't believe that was the problem. I've had this problem since Edgy and I couldn't find a single answer on what was hanging it from starting. I'm the opposite - I have wireless working and my ethernet port is not being used so eth0 is what was hanging it.

Before
   interfaces = lo eth0 wlan0

After
   interfaces = lo wlan0

I restarted samba and winbind installed fine. It's kind of silly that it hangs on an interface that's not up, as I may plug my LAN cable in in the future and will have to play with the config file again and restart samba. Maybe it's a bug? Either way thanks for the fix.

---

