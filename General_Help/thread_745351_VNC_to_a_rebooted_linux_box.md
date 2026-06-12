---
title: "VNC to a rebooted linux box"
date: 2008-04-04
forum: General Help
---

### Post by tom_e_reynolds on 2008-04-04
Hi all,

Not sure if I am missing something here or not.  I setup a default Ubuntu 7.10 install and am quite pleased to use it as a replacement for some of my Windows Boxes.  That said I am able to use the Ubuntu Remote Desktop client to connect to a Windows server and see the login prompt.  Then I login and do my stuff.

Yet, even after I setup the Remote Desktop options on my Linux boxes, when I try to use VNC to access my Linux boxes, I cannot VNC in until after I logged in on the Linux Server?  How can I remotely access a Linux server that hasn't been logged in yet?  Must I SSH to it, and start the VNCServer?  or something like that.  I need to be able to access a Linux box after it gets remotely rebooted. 

It always allows me to VNC to the Linux Server after that Server has been locally logged in already, so I know that part works.

Any help would be appreciated.

-Tom

---

### Post by commonplace on 2008-04-04
Set the machine to autologin, or use another remote solution such as NX. NX is what I use.

---

### Post by maybeway36 on 2008-04-04
I set up x11vnc as my VNC server (see my sig.)

---

### Post by tom_e_reynolds on 2008-04-07
Great.  I just set it to auto login until i have time to test the other options.  

Thanks again.

---

