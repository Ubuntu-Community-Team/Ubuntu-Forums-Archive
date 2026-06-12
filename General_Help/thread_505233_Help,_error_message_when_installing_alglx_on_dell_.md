---
title: "Help, error message when installing alglx on dell 700m"
date: 2007-07-20
forum: General Help
---

### Post by sarahsilverman on 2007-07-20
i know, my computer isn't so well. these dell laptops, i only had them for like 2 years and its already old. i have a hard time finding out how to run things and i found that i need to upgrade. i also found that the 700m you can't upgrade anything so you have to purchase a new one. im thinking about getting a mac, but any ways. i need help.

im following this sites wiki: [http://www.canhesaythat.com/wiki/index.php/HOWTO_Ubuntu_On_Dell_700m#Just_the_Graphics](http://www.canhesaythat.com/wiki/index.php/HOWTO_Ubuntu_On_Dell_700m#Just_the_Graphics)

im stuck on  AIGLX DAPPER

when i type and enter this into the terminal "sudo apt-get install linux-dri-modules-common linux-dri-modules-`uname -r`" i get the following error : "Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-dri-modules-common"

i know its because of installing the respiratory, i can't install it. i go into synaptic and add the respiratory link thing "deb [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper aiglx" and "deb [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main" but synaptic says it couldn't download anything and that the respiratory might not be there anymore.

is there any other thing i can do, like another link thingy i can paste into the respiratory thingy so i can continue on.

please and thank you, any help is greatly appreciated :popcorn:

---

### Post by overdrank on 2007-07-21
> **sarahsilverman said:**
> i know, my computer isn't so well. these dell laptops, i only had them for like 2 years and its already old. i have a hard time finding out how to run things and i found that i need to upgrade. i also found that the 700m you can't upgrade anything so you have to purchase a new one. im thinking about getting a mac, but any ways. i need help.

im following this sites wiki: [http://www.canhesaythat.com/wiki/index.php/HOWTO_Ubuntu_On_Dell_700m#Just_the_Graphics](http://www.canhesaythat.com/wiki/index.php/HOWTO_Ubuntu_On_Dell_700m#Just_the_Graphics)

im stuck on  AIGLX DAPPER

when i type and enter this into the terminal "sudo apt-get install linux-dri-modules-common linux-dri-modules-`uname -r`" i get the following error : "Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-dri-modules-common"

i know its because of installing the respiratory, i can't install it. i go into synaptic and add the respiratory link thing "deb [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper aiglx" and "deb [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main" but synaptic says it couldn't download anything and that the respiratory might not be there anymore.

is there any other thing i can do, like another link thingy i can paste into the respiratory thingy so i can continue on.

please and thank you, any help is greatly appreciated :popcorn:

Hi you might try to add the edgy repos from that page to you repos and see if that works I have seen thread where this has work for some. I am not recommending it it is just a suggestion and if it doesn't work you can remove the repos from your system. If you are just wanting to get to the desktop eye candy then you may think of upgrading to edgy or feisty be cause the intel graphics work great for me in both edgy and feisty. Good luck on whatever you choose. :)
[B][COLOR="Red"]
Edit are you using dapper or feisty ?[/COLOR][/B]

---

