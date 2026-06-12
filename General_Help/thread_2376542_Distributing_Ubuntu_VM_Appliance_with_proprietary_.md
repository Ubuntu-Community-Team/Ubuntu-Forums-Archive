---
title: "Distributing Ubuntu VM Appliance with proprietary and OSS software"
date: 2017-11-03
forum: General Help
---

### Post by gawillbe on 2017-11-03
Hello All, 

I have been through ubuntu's license page and GPL license FAQ ([https://www.gnu.org/licenses/gpl-faq.en.html](https://www.gnu.org/licenses/gpl-faq.en.html)).  Lots of legal mumbo jumbo, but I still didn't get an answer if I can legally distribute the following image: 
- A  vdi/ova/qcow2 ubuntu image (server version). 
- Pre-Installed with some open source softwares like Mariadb / ElasticSearch / OpenJDK etc. 
- Also installed our own proprietary (commercial) Java package.  We do not link to any ubuntu libraries in our code. 

Absolutely no modification is made to the ubuntu OS.  We just want our customers to be able to download the VM image on a virtual box and be up and running without the hassle of installing anything or running any vagrant up or accepting EULAs etc.  Any clear documentation of whether this is allowed or not ?   Any examples of this having been done?  If not, what might be the work around?  Example,  do I need to create a new derivative distro out of ubuntu to do this? 

rgds
GA

---

### Post by coldraven on 2017-11-03
I'm not a lawyer but this company has been offering virtual images for years now. I'm sure that they would have been stopped if they had violated some licensing  terms.
Disclaimer: I'm in no way connected to them, I just use their server images for non-profit use.
[https://virtualboxes.org/](https://virtualboxes.org/)

---

### Post by gawillbe on 2017-11-03
Thanks for the answer coldraven ... I checked out the virtualboxes site and all the images they have are just preinstalled variants of Linux.  None of them are installed with other open source software or proprietary components as far as I can tell.  So this unfortunately would not be a good example in this scenario.

---

### Post by dragonfly41 on 2017-11-03
Instead of deploying custom images, could you release automation scripts which "walk" the customers through installation?

[https://www.ansible.com/](https://www.ansible.com/)

---

### Post by oldos2er on 2017-11-03
gawillbe, you need to contact Canonical at [https://www.ubuntu.com/about/contact-us](https://www.ubuntu.com/about/contact-us)

See [https://www.ubuntu.com/legal/terms-and-policies/intellectual-property-policy](https://www.ubuntu.com/legal/terms-and-policies/intellectual-property-policy)

---

