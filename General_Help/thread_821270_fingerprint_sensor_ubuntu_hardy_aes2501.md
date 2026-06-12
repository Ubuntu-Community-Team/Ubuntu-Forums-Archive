---
title: "fingerprint sensor ubuntu hardy aes2501"
date: 2008-06-07
forum: General Help
---

### Post by soumen08 on 2008-06-07
Hello,
I have just gotten my fingerprint sensor on hp6515b to work(well somewhat..) by following the walkthrough on this link

[http://blog.irwan.name/?p=471](http://blog.irwan.name/?p=471)

I am facing a slight glitch. I can login and even use sudo applications but after one sudo when i try to invoke another i get a "Segmentation Fault" message on the terminal. 

Eg. I type sudo synaptic, after having logged on with the fingerprint sensor, it asks me to swipe my finger, i do it, and it opens synaptic(with administrator privileges). I write sudo gedit it says segmentation fault.

Can someone explain what segmentation fault is, and how i can attain multiple sudo capability using the sensor?
Thanks,
Soumen

---

### Post by soumen08 on 2008-06-07
Well someone please reply to the post... I'm waiting for a solution to the problem.

---

### Post by shishka on 2008-08-02
Getting a seg fault means that the program tried to access an area of memory it did not have permission to access. It often takes much labor to discover what's causing it.

A simple (but annoying) workaround is to clear the timestamp after every time you run sudo (ie use "sudo -k"). I'm still looking for a straight-up solution.

---

### Post by shishka on 2008-08-02
Here's another workaround:

```

cd /etc/pam.d/
sudo gedit common-auth sudo
```
In common-auth copy all of the lines except the one containing pam_fprint.so. Now go into the sudo file, comment out @include common-auth (prepend a "#"), and paste the lines directly below this one.

This makes sudo only use password authentication (or whatever you were using before fingerprints). Everything else still uses fingerprints.

---

