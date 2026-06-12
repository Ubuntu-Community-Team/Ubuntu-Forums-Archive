---
title: "Cant install XGL :("
date: 2007-11-07
forum: General Help
---

### Post by lynxus on 2007-11-07
I'm having problems installing XGL.. 
i apt-get install xserver-xgl but once thats installed i cant login, it starts to login then just goes back to the login screen.

The error log mentions a fatal xserver error , restarting.

Is there something im missing here ?


This is a new build on an IBM R51 with an ATI card, 
It all used to work fine on feisty, so im assuming something is different in gusty thats causing this problem.

Thanks
G

---

### Post by Fire_Chief on 2007-11-07
Are you using the ATI restricted driver (check your xorg.conf and see what driver is listed for the graphics card section)? If so, do you know which version of the driver you have installed?

I'm assuming you want XGL to run CompizFuzion? The latest ATI driver (8.42) can run CompizFuzion without the need for the XGL server. Granted it's still not perfect but certainly less complicated.

---

### Post by lynxus on 2007-11-07
Ahh,
im using the "radeon" driver.

Its odd cos when my m8 who has the same laptop installed it, he had to goto the restricted drivers thing and click enable. However i dont have that as an option, it just has a modem driver that i can enable. Really odd whay it didnt install that.

Maybe ill try and install that latest version of the ati driver.

Any ideas where i can grab it , or maybe even an install guide..

---

### Post by Fire_Chief on 2007-11-07
Try this guide [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_8.42.3_Driver_Manually]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_8.42.3_Driver_Manually")

---

