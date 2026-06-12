---
title: "Unable to login to desktop following recent updates."
date: 2016-03-15
forum: General Help
---

### Post by 720iD on 2016-03-15
It is about 3 weeks since I have been able to access my ubuntu system. The last time I used the system I was prompted to perform some updates and after the updates I am unable to login. When I boot up I get to the login screen. The login screen looks slightly distorted like it is in the wrong resolution. When I attempt to login the screen flickers and I am returned to the login prompt.  

Can anybody make any suggestions where to start to sort this out. I have searched the forum for related threads but cannot find anything specific to my problem. 

some of the updates I performed where for my ATI graphic card drivers and while searching for solutions I have seen similar problems with Nvidia drivers but nothing related ATI drivers.

TIA

---

### Post by howefield on 2016-03-15
I'd boot to the recovery console and remove any fglrx drivers, assuming that you are using them ?

---

### Post by jondog154 on 2016-03-16
On boot up hold down the shift key 

 [IMG]http://www.howtogeek.com/wp-content/uploads/2014/09/640x480xselect-linux-kernel-in-grub2-boot-loader-on-ubuntu-14.04.png.pagespeed.gp+jp+jw+pj+js+rj+rp+rw+ri+cp+md.ic.wbxLt_6FkP.png[/IMG]
You'll see the screen above tell me what options it gives you

---

### Post by 720iD on 2016-03-16
> **howefield said:**
> I'd boot to the recovery console and remove any fglrx drivers, assuming that you are using them ?
I am not sure about fglrx drivers. I think they are the proprietary drivers from ATI.

---

### Post by 720iD on 2016-03-16
> **jondog154 said:**
> On boot up hold down the shift key 


 [IMG]http://www.howtogeek.com/wp-content/uploads/2014/09/640x480xselect-linux-kernel-in-grub2-boot-loader-on-ubuntu-14.04.png.pagespeed.gp+jp+jw+pj+js+rj+rp+rw+ri+cp+md.ic.wbxLt_6FkP.png[/IMG]
You'll see the screen above tell me what options it gives you 
Yes, I have a dual boot. So I get the GNU grub screen on boot which is very similar but with options of; 
1 ubuntu
2 advanced options for Ubuntu
3 memtest 86+
4 memtest 86+ serial console
5 boot windows 7
I did boot into a recovery mode last night using the option 2. From their i was able to access a terminal. I just don't know what to look for when I am there.

There was also a fail-safe graphics option but it did actually fail. :/

---

### Post by howefield on 2016-03-16
> **720iD said:**
> I am not sure about fglrx drivers. I think they are the proprietary drivers from ATI.

Yes, that's the ones. Are you using the proprietary drivers ?

---

### Post by 720iD on 2016-03-16
> **howefield said:**
> Yes, that's the ones. Are you using the proprietary drivers ?
Yes I was using the proprietary ones which I needed for something ages ago but no longer need. It was these that where updated and broke the GUI environment.

---

