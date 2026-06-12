---
title: "Just Upgraded to Linux 3.7 What about updates?"
date: 2012-12-31
forum: General Help
---

### Post by Eugene King on 2012-12-31
I upgraded to Linux 3.7 so I can USB tether with my iPhone 5. Everything is working great, plus now I can tether without transmitting WiFi.

My question is this......like the title says during updates I see it wanting to load kernal 3.0.0.29. 

Will that harm the 3.7 kernal?

Do I ignore it?

Gene

---

### Post by 2F4U on 2013-01-01
What version of Ubuntu are you running? As far as I know, none of the released Ubuntu versions has kernel 3.7 available. Did you install that kernel from a repository or did you compile it yourself? If installed from a repository, there should be no attempt to install a lower version, however, if compiled the system may not be aware of the newer kernel.
Anyways, installing kernel 3.0 shouldn't harm the other kernel, but most likely changes the boot order, so that the system, by default, boots kernel 3.0.

---

### Post by Eugene King on 2013-01-01
I used upubuntu blogs instructions. It was a few simple commands in terminal. 

It's installed on my USB drive I use at work and its 11.10. So worse case I just put the CD back in and reload the USB. Only thing special on it are some favorites.

[FONT=.HelveticaNeueUI]http://www.upubuntu.com/2012/12/installupgrade-to-linux-kernel-37-under.html?m=1 [/FONT]
[FONT=.HelveticaNeueUI]
[/FONT]
[FONT=.HelveticaNeueUI]Incase someone is wondering how to do it. Expecially for iPhone 5 USB tethering here it it. [/FONT]

---

### Post by Eugene King on 2013-01-03
I just allowed updates and kernel 3.7 stayed even though it sure looked like 3.0.0.29 was being installed. 

3.0.0.29 also didn't show up as a boot option........

---

