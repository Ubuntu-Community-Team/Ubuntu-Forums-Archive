---
title: "Problems with installing esayubuntu"
date: 2007-01-06
forum: General Help
---

### Post by zazen666 on 2007-01-06
Hi guys, 
I am trying to get Esayubuntu installed so that i can attempt to (finally) get java, flash, and video working from switfox.
However i am getting this error. 

marshal@marshal-laptop:~$ sudo apt-get install easyubuntu
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?


Advice would be MUCh appericated
thanks

---

### Post by maggotbrain on 2007-01-06
> **zazen666 said:**
> Hi guys, 
I am trying to get Esayubuntu installed so that i can attempt to (finally) get java, flash, and video working from switfox.
However i am getting this error. 

marshal@marshal-laptop:~$ sudo apt-get install easyubuntu
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?


Advice would be MUCh appericated
thanks

The error message you are getting means that another application is trying to update packages. Do you have Synaptic Package manager open while you are trying to install easyubuntu from the command line? If so, close the application and try installing easyubuntu again.

As an aside, may I recommend using Automatix2 to install your Swiftfox plugins? (Either do a search for Automatix on the ubuntuforums, or look here: [http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Automatix2_on_Ubuntu.2C_Kubuntu.2C_and_Xubuntu]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Automatix2_on_Ubuntu.2C_Kubuntu.2C_and_Xubuntu")) In my opinion, I have found it to be more 'robust' than easyubuntu. YMMV.  
Hope that helps you out.

---

