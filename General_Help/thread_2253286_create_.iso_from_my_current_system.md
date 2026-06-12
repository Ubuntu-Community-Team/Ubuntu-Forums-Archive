---
title: "create .iso from my current system"
date: 2014-11-18
forum: General Help
---

### Post by marchello_lippi2 on 2014-11-18
Hi all, 

How do I create .iso from my current system? 

I've installed a lot of packages, configurated them due to my preferences and would like to freeze all this into .iso, please tell me how to do it. 
Thanks ahead.

---

### Post by yancek on 2014-11-18
Use the mkisofs or genisoimage commands from either a Live CD/DVD/flash or another installed system.  You could also try remastersys which was designed to do exactly that for Debian/Ubuntu and worked very well.  It is no longer being developed as it was a one man show and he got tired of all the complaints/demands and no help.  I've used it on Ubuntu 12.04 and earlier versions.  Don't know if it will work for you as you don't indicate which Ubuntu you are using?  You can also use "usb-creator-gtk", open a terminal from an installed system and type:  sudo usb-creator-gtk and it will open the gui you can use.  Don't think it will be on an install medium.

---

### Post by Mark Phelps on 2014-11-18
> and would like to freeze all this into .iso, And, then what?

If what you're really looking to do is save off your current Ubuntu install in a way that you could easily restore it later, you should look into CLonezilla, instead.  That can be used to create a file of your current install, which you can then later use to restore what you have now.

---

