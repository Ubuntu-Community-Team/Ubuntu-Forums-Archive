---
title: "Removing services for faster boot"
date: 2012-12-26
forum: General Help
---

### Post by M1C4HTRON13 on 2012-12-26
My boots have been quite slow lately.

Can anyone suggest any services that I should disable.

[IMG]http://i.imgur.com/VUFNN.png

---

### Post by ranger1021994 on 2012-12-26
You can disable :
1 : cupsd If you dont have Printer
2 : Bluetooth If you have no necessary use immediately after boot
3 : Skype
4: /usr/bin/termin

You can go to Startup Application and disable services that you dont require.
For furthr Boot acceleration , use e4rat instead of ureadahead

---

### Post by M1C4HTRON13 on 2012-12-28
Trying to configure e4rat but Im getting an error when I try to update the grub

```
sudo update-grub
/usr/sbin/grub-mkconfig: 1: /etc/default/grub: ]#: not found
```

---

