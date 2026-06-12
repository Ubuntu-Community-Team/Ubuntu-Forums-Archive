---
title: "Bluetooth Device"
date: 2008-07-05
forum: General Help
---

### Post by RazorShug on 2008-07-05
HI, this is my first post so first off let me say Hi to everyone here :)

Now on to my problem, i recently bought a USB Bluetooth device for my laptop, when i first used it there was no problem i was able to transfer files between my laptop and phone, now when i plug the device in i dont get the icon in the system tray to say its active or its there. 
.
any help on how to get the icon back so i can use it again would be helpful.

Thanks

---

### Post by f37u5g0d on 2008-07-05
You can use Add/Remove or the synaptic package manager but either way make sure that you have the bluetooth packages you want to use installed.  There are different packages that allow you to do different (and sometimes totally awesome) things.  Other than that I believe bluetooth in ubuntu is automatically started when you have your dongle plugged in.

---

### Post by sayakb on 2008-07-05
Open a terminal and type in:
```
sudo apt-get install bluez-utils
```

---

### Post by RazorShug on 2008-07-06
Thanks your right about the manager automatically starting. i created a 2nd user account and logged in with that and the bluetooth manager is there but not in my main account. for some reason im having problems with the main account, i can get the bluetooth manager to open in that and firefox 3 wont work in that account either but when i log in with a secondary account its not a problem.

anyone have any ideas what could be causing the problems?

---

