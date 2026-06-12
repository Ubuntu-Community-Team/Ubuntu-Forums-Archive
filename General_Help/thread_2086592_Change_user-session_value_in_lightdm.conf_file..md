---
title: "Change user-session value in lightdm.conf file."
date: 2012-11-21
forum: General Help
---

### Post by kleenex on 2012-11-21
Hello, can I, without any issue, change value for [COLOR=Blue]user-session[/COLOR] in [COLOR=SeaGreen]/etc/lightdm/lightdm.conf [/COLOR]file? Default entry is set to [COLOR=Blue]xubuntu[/COLOR] and I would like to change it to e.g. 'diablo' or whatever. I'm afraid I will not be able to log in after system reboot etc. So I can modify this entry, or not?
  
Thanks.

---

### Post by lykwydchykyn on 2012-11-21
I believe it will only change what the default session is set to, so it should not affect your ability to log in.  Do you in fact have an xsession called "diablo"?  What's your goal here?

---

### Post by kleenex on 2012-11-22
Hi **lykwydchykyn**. No, I do not have a xsession called 'diablo'. It is only an example.  ;-) So everything should be okay?

---

### Post by lykwydchykyn on 2012-11-22
Sure.  Worst case, you log in to a terminal, "sudo nano /etc/lightdm/lightdm.conf" and change it back.

---

### Post by kleenex on 2012-11-23
Hi, yeah true! I forgot about it - [COLOR=SeaGreen]ctrl[/COLOR] + [COLOR=SeaGreen]shift[/COLOR] + [COLOR=SeaGreen]Fx[/COLOR]. Thank You!

---

