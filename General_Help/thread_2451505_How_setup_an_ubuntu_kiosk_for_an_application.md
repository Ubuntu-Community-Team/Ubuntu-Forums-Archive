---
title: "How setup an ubuntu kiosk for an application"
date: 2020-10-05
forum: General Help
---

### Post by giobaxx on 2020-10-05
Hello guys

I need an help to understand how to build a Kiosk using Ubuntu 18.04. This kiosk need to run only one application (google-earth) that basically should start at boot without and after an autologin.

I knew an old collegue who did this....but i don't know where to start and i need to start from the basics?

I have googled but for the moment i did't find anything userful for me...

Thanks in Advance

---

### Post by SeijiSensei on 2020-10-05
[https://ubuntu.com/tutorials/secure-ubuntu-kiosk#1-overview](https://ubuntu.com/tutorials/secure-ubuntu-kiosk#1-overview)

---

### Post by giobaxx on 2020-10-07
Thanks for the help but this guide is a big complicated for my level. i don't even know what is ubuntu core.  :-(. 

I found this guide to try to install a kiosk tha work in single application mode, basically does not need login and run an application  at boot in full screen: [https://help.gnome.org/admin/system-admin-guide/stable/lockdown-single-app-mode.html.en](https://help.gnome.org/admin/system-admin-guide/stable/lockdown-single-app-mode.html.en)

But i just tried the automatic login editing the /etc/gdm3/custom.conf file adding ther following line

> 
[daemon]
AutomaticLoginEnable=[COLOR=#2E3436]**True**[/COLOR]
AutomaticLogin=[COLOR=#2E3436]**user-kiosk**[/COLOR]

The VM i build just to test does not boot correctly i see only a dark screen. 

:-(

---

