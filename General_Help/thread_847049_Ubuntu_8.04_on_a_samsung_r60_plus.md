---
title: "Ubuntu 8.04 on a samsung r60 plus"
date: 2008-07-02
forum: General Help
---

### Post by binary_dreamer on 2008-07-02
Hi. I got a samsung r60 plus laptop and i would like to install ubuntu 8.04. i did download the live cd, chacked it's md5 checksum and it was ok.
I booted from the cd and it started the wizard to boot. then i pressed ok and i was waiting for the desktop of the live cd to appear. unfortunately i did not get anything, rather than an error in the console saying that it could not start x.
i thought that th cd might be defective. i checked it in a desktop pc and it worked perfectly and the installation finished successfully.
Any ideas anyone?
[http://www.laptopsdirect.co.uk/Samsu...UK/version.asp](http://www.laptopsdirect.co.uk/Samsu...UK/version.asp)

Also i have tried to boot in safe mode graphics by pressing F4 but i had the same response as above.

---

### Post by beN..87 on 2008-07-03
> **binary_dreamer said:**
> Hi. I got a samsung r60 plus laptop and i would like to install ubuntu 8.04. i did download the live cd, chacked it's md5 checksum and it was ok.
I booted from the cd and it started the wizard to boot. then i pressed ok and i was waiting for the desktop of the live cd to appear. unfortunately i did not get anything, rather than an error in the console saying that it could not start x.
i thought that th cd might be defective. i checked it in a desktop pc and it worked perfectly and the installation finished successfully.
Any ideas anyone?
[http://www.laptopsdirect.co.uk/Samsu...UK/version.asp](http://www.laptopsdirect.co.uk/Samsu...UK/version.asp)

Also i have tried to boot in safe mode graphics by pressing F4 but i had the same response as above.


you need to use the alternate CD .. fortunately for you i recently installed 8.04 on a samsung r60, hopefully this guide will save you all the blood sweat and tears!

[http://ubuntuforums.org/showthread.php?t=839000](http://ubuntuforums.org/showthread.php?t=839000)

---

### Post by binary_dreamer on 2008-07-07
Hi. thanks a lot for the quick reply.
The guide was simply amazing. 
It worked finally. cheers!
One final think that bothers me. How can i turn off the wireless LAN card? while in MS Vista it can be done by making use of a key combination. it can be turned on by making use of the same keys as well. How can we do that in ubuntu?

---

### Post by beN..87 on 2008-07-08
good i'm glad it worked!

to turn off your wireless - just use wicd network manager to either remove any possible listings of wireless connections

also if you are using wired interface -- the part where you did 

sudo gegit /ect/modules

ath_hal
ath_pci 

this part adds you wireless to load on start up - you could remove those to stop it turning on at start up.

---

### Post by binary_dreamer on 2008-07-08
Hi thanks a lot for your quick reply.
If i add the lines:
ath_hal
ath_pci
it will stop wifi from loading at boot time.
Now, how do i enable it on demand?

---

### Post by beN..87 on 2008-07-08
> **binary_dreamer said:**
> Hi thanks a lot for your quick reply.
If i add the lines:
ath_hal
ath_pci
it will stop wifi from loading at boot time.
Now, how do i enable it on demand?

no you remove those lines because they tell the modules to load at boot - if you want to switch it on and off on demand - better to leave them on and simply use a network manager such as Wicd to gain control over your connections in a GUI

---

### Post by binary_dreamer on 2008-11-05
hi. i upgraded to ubuntu 8.10 and i cannot have internet access.

unfortunately i cannot ping anywhere even my gw. i can see that ifconfig gives me ip from dhcp. any ideas anyone?

---

