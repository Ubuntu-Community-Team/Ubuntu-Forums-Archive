---
title: "Please help, Failed to start X server"
date: 2007-08-31
forum: General Help
---

### Post by simbataisa on 2007-08-31
I'm using IBM T61 Core 2 Duo with Intel Graphic Media Accelerator X3100, I want to install ubuntu but I got the error: Failed to start X server. is this because of lacking video driver or I need to make some changes  so that I am able to install Ubuntu. 
Thank you for your help.

---

### Post by arsya on 2007-08-31
Sorry, need to clarify something first. Do you mean you have problem during loading the Installation CD or you had already installed Ubuntu and have problem with it?

If you have problem during loading the Installation CD, then maybe the CD is defected. Check the checksum first. I don't think there is a problem with the video hw or driver.

If what you mean you had already installed Ubuntu, and somehow the X server won't run, you need to check the log files in:
/var/log/Xorg.0.log   and   ~/.xsession-errors

---

### Post by brenix on 2007-10-31
Maybe try running in a console:
dpkg-reconfigure xserver-xorg

That might help, just a suggestion..

EDIT: I didnt notice you were in the process of installing ubuntu, not sure if that will work..

---

