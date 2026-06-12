---
title: "Sometimes No WiFi at Boot"
date: 2022-01-15
forum: General Help
---

### Post by Daveski17 on 2022-01-15
Since Christmas Day I occasionally find I have no WiFi connectivity on boot-up. I've never seen this behaviour before in over five years of using this Lenovo G500 laptop. The system tray WiFi icon doesn't appear.

[ATTACH=CONFIG]289804[/ATTACH]

I'm pretty certain it's some bug related to an update. A reboot or three usually fixes it. I'm running Ubuntu 20.04 LTS.

[ATTACH=CONFIG]289805[/ATTACH]

Has anyone else had this since Christmas?

---

### Post by hk42 on 2022-01-16
It is exactly the behavior when your WIFI is subject to interference.
Try another channel.
Some received a computer or device for Christmas and want to use WIFI too.

---

### Post by Daveski17 on 2022-01-16
> **hk42 said:**
> It is exactly the behavior when your WIFI is subject to interference.
Try another channel.
Some received a computer or device for Christmas and want to use WIFI too.

I don't know what you mean by try another channel. There is no systems tray icon. There are no visible networks.

---

### Post by TheFu on 2022-01-16
> **Daveski17 said:**
> I don't know what you mean by try another channel. There is no systems tray icon. There are no visible networks.

It is a setting in the router, not your computer, if this is really the issue.  The idea is that one of your neighbors got a new router and it is using the same channel that your router does for wifi.  Every year, it is worth scanning for a better channel to use. I have a calendar reminder.  There are some other things to know based on the frequencies, but the main thing is to stay off the same frequencies as other nearby routers.

---

### Post by Daveski17 on 2022-01-16
> **TheFu said:**
> It is a setting in the router, not your computer, if this is really the issue.  The idea is that one of your neighbors got a new router and it is using the same channel that your router does for wifi.  Every year, it is worth scanning for a better channel to use. I have a calendar reminder.  There are some other things to know based on the frequencies, but the main thing is to stay off the same frequencies as other nearby routers.

Oh right, I understand that. I don't think it is a router thing. I have other laptop computers and neither they or my desktop are affected. This is a boot-up system tray issue as far as I can deduce.

---

### Post by TheFu on 2022-01-16
> **Daveski17 said:**
> Oh right, I understand that. I don't think it is a router thing. I have other laptop computers and neither they or my desktop are affected. This is a boot-up system tray issue as far as I can deduce.

Could the router have a limited range of DHCP addresses and all the available ones are taken?  Just shooting in the dark now.

---

### Post by Daveski17 on 2022-01-16
> **TheFu said:**
> Could the router have a limited range of DHCP addresses and all the available ones are taken?  Just shooting in the dark now.

It's not every time that this happens. When it does, it always happens on boot. The wifi icon just doesn't appear in the systems tray. A reboot usually brings it back. I still think it's related to an upgrade.

---

### Post by Daveski17 on 2022-01-27
I still say that this is related to an upgrade. I still have to reboot a computer several times to make a WiFi connection that in over five years never had this problem. Ethernet is fine. My other computers have no connectivity problems. This is an Ubuntu problem.

---

### Post by hk42 on 2022-01-28
At boot in the grub menu if you choose advanced options you can try
an older kernel.
This menu is very useful each time you suspect an update and for
many other things.

---

### Post by Daveski17 on 2022-01-28
> **hk42 said:**
> At boot in the grub menu if you choose advanced options you can try
an older kernel.
This menu is very useful each time you suspect an update and for
many other things.

OK, thanks for the info.

---

### Post by Daveski17 on 2022-01-28
Now the WiFi lasts for a few seconds after boot then disappears.

---

### Post by Daveski17 on 2022-01-28
Occasionally I take the Ethernet cable out and the WiFi bounces back for an amount of time before disappearing again.

---

### Post by Daveski17 on 2022-02-01
Updated kernel. Now I have WiFi.](*,)

---

