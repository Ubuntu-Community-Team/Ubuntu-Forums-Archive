---
title: "Ubuntu on Sun Ray"
date: 2007-01-12
forum: General Help
---

### Post by rward on 2007-01-12
Hi,

Having tried to get the SunRay server software to work on CentOS and Solaris 10, I saw that Ubuntu had a very detailed guide [https://help.ubuntu.com/community/UbuntuOnSunRay]("https://help.ubuntu.com/community/UbuntuOnSunRay")

I have followed this guide word for word and all seemed to be going well untill i did a reboot and even though i followed the instructions for stopping the keyboard freezing up, it still does. If i am very quick i can log in before it freezes, but there is little point as it is sure to freeze up after about 10 seconds. This is on the server - I cannot tell on the client yet as it does not boot (think i got the address of the router wrong, but thats by the by). Any ideas how i can solve this? I can get a terminal open by pressing CTRL+ALT+F2 (i think it was that) so if someone knows of some configuration i need to change, i can do it fortunately!

Regards
Richard

---

### Post by koojak on 2007-01-30
I ran into the same problem, even after a complete clean reinstall. Keyboard freezes during start up of SunRay. At the time an Ubuntu signon appears on the SunRay terminals the keyboard of the console hangs.
A zsunray-init stop; gdm stop; gdm start; zsunray-init start solves the problem Until the next boot. 
I have no idea what causes this problem, I've been looking for a second GDM start or something simular causing GDM to fail.

koos

---

