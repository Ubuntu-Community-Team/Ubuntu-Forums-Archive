---
title: "Ubuntu on Toshiba Chromebook 2 - Mil CAC issue"
date: 2014-12-26
forum: General Help
---

### Post by jhh on 2014-12-26
I am trouble shooting an issue that I'm having with my Toshiba Chromebook 2. I successfully installed Ubuntu (trusty) with the XFCE DE on my Chromebook. It really was easy, and makes the chromebook awesome, especially for its price point. 

I am attempting to use a CAC reader, and I have successfully made it work twice. After I intially installed coolkey pcscd (command below), and updated the security devices in Firefox (location below), it worked perfectly. However, if I restart the computer and plug in the CAC reader, it seems the CAC reader is not found (I get no green light from the reader at all). 

Last night, I removed coolkey pcscd, and then re-installed it. Doing that made it possible to check email and access Mil-CAC websites; however, now that I've restarted it and unplugged the CAC reader, and subsequently now plugged it in to use it -- it doesnt work again.

sudo apt-get install coolkey pcscd
/usr/lib/pkcs11/libcoolkeypk11.so

Any ideas/advice?h
Tanks, 
jhh

---

### Post by jhh on 2014-12-29
anyone else worked through this?

---

### Post by jhh on 2014-12-29
New development -- 

I removed the security modules and devices from the Security tab under Preferences on Firefox, and I also removed the coolkey pcscd  with [sudo apt-get remove coolkey pcscd]

After removing the security modules (libcoolkeypk11.so) and coolkey pcscd, I reinstalled with the following:

sudo apt-get install coolkey pcscd
And uploaded the approparite security modules to Firefox (libcoolkeypk11.so)

As soon as I did that, the green light on the common access card (CAC) reader began to blink, and it successfully read the certificates from the DoD CAC card. I was able to check email, and go to other sites.

Now that the session has finished, if I plug in my CAC reader, it seems like it is not recognized (the green light does not blink). 

Any ideas as to why this is happening? Will I just need to uninstall/install each time to get it to work?

---

