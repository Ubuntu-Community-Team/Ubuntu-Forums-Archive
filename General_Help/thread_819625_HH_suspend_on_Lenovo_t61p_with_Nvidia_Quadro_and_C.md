---
title: "HH suspend on Lenovo t61p with Nvidia Quadro and Compiz"
date: 2008-06-05
forum: General Help
---

### Post by armandli on 2008-06-05
I'm having some unstable problem with ubuntu suspend on my machine. The suspend sometimes work, and sometimes doesn't, and it seems that if i leave my laptop suspended long enough, it will fail to suspend, and show up a white screen. 

I have a nvidia video card, and i use compiz with vBlank option off. what can i do to make sure the white screen don't show up after waking from suspend?

also, I know that I can switch to tty1 or other channels to restart my gdm. but sometimes i just want to shutdown gdm completely, without causing it to reboot into another tty. how do i do that? 

often if gdm restarts, it goes to use a higher tty channel, and i don't like that, how do i close gdm securely and reuse the previous tty to restart gdm?

---

### Post by armandli on 2008-06-05
update: i found out the reason i get white screen when i woke from suspend is probably caused by the login screen, and if i guess where the login screen's position for putting in my password, then the desktop can be successfully restored.

---

