---
title: "how to log into desktop automaticaly"
date: 2022-02-25
forum: General Help
---

### Post by buill on 2022-02-25
hi i have set the account to log in without password but the login screen still appears and requires me to press login i want it to skip this screen all together and just booth into desktop i have searched through out the settings in users and groups  etc but cant find the setting anywhere i am using mate desktop env does anyone know how this can be done either by terminal or pointing out im stupid either way is fine thanks  in user accounts there is no option for automatic login ubuntu version 20.04

---

### Post by buill on 2022-02-25
found solution here [https://askubuntu.com/questions/51086/how-do-i-enable-auto-login-in-lightdm](https://askubuntu.com/questions/51086/how-do-i-enable-auto-login-in-lightdm) 

/etc/lightdm/lightdm.conf.d/12-autologin.conf
  and add:
  [SeatDefaults]
autologin-user=youruser

---

