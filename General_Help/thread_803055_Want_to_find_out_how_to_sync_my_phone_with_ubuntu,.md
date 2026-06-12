---
title: "Want to find out how to sync my phone with ubuntu, but the sony software uses outlook"
date: 2008-05-22
forum: General Help
---

### Post by DJSchmidty on 2008-05-22
Want to find out how to sync my phone with ubuntu, but the sony software uses outlook to hold all my contacts and dates and notes and stuff.  How can I use ubuntu to sync with my phone?  I have a sony w580, the slider walkman phone (Friggin awesome, and cheap!!) anyway, it uses nsony ericson pc suite.  I would have just loaded into wine and see what happens, but I knew that it had to sync with outlook(I guess I needed to have outlook installed for it to sync anyway... wierd)

---

### Post by asrai on 2008-05-22
I use a program called multisync (different to multisync 0.90) which is easy to use and very fast.  It is in the repos :)

Do you want to sync using bluetooth or usb?  If you're using bluetooth make sure you also download the ircmcbluetooth plugin :)

---

### Post by DJSchmidty on 2008-05-22
ok, for some reason my last post on the fact that I can't add or remove programs never got posted, so whats the "sudo apt-get" or what ever for that program?

---

### Post by asrai on 2008-05-22
the add/remove programs problem is a bigger one.. happy to help with that if I can? What error messages are you getting or what is happening when you try to use synaptic or the add/remove app?

It would be sudo apt-get install multisync 

you will also need some plugins - so also add libmultisync-plugin-irmc libmultisync-plugin-evolution and libmultisync-plugin-irmc-bluetooth if you need bluetooth support.

This is the package page:  [http://packages.ubuntu.com/hardy/multisync](http://packages.ubuntu.com/hardy/multisync)

---

