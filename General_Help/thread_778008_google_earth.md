---
title: "google earth"
date: 2008-05-01
forum: General Help
---

### Post by sweeneytodd on 2008-05-01
can someone please tell me how to install googleearthlinux, i have a bin file on the desktop

---

### Post by bollix47 on 2008-05-01
Google Earth 4.3 is now included in the Medibuntu repository of Ubuntu 8.04. 

How to add medibuntu for Hardy see
[http://ubuntuforums.org/showthread.php?t=713009](http://ubuntuforums.org/showthread.php?t=713009)

---

### Post by ryanhaigh on 2008-05-01
This tells you everything you need to know:
[https://help.ubuntu.com/community/GoogleEarth](https://help.ubuntu.com/community/GoogleEarth)

---

### Post by sweeneytodd on 2008-05-01
O.k, done that, now i get the interface without the earth, looks like it isn't connecting to their servers, I followed instructions correctly, any idea?

---

### Post by meho_r on 2008-05-01
4.3 doesn't work for me either. I installed from Medibuntu and get some errors, couldn't connect to server. 4.2 works fine. Any ideas?

---

### Post by mister_k81 on 2008-05-01
> **meho_r said:**
> 4.3 doesn't work for me either. I installed from Medibuntu and get some errors, couldn't connect to server. 4.2 works fine. Any ideas?

It might be your processor. Google Earth 4.3 won't work on older CPU's that don't have SSE2 support under Linux. I couldn't get it to work on my older Athlon XP 2600 machine because of this, too. 

More information here: 

[http://groups.google.com/group/earth-linux/browse_thread/thread/e77715780fd5ede5#](http://groups.google.com/group/earth-linux/browse_thread/thread/e77715780fd5ede5#)

---

### Post by sweeneytodd on 2008-05-01
athlon 64 X 2 4600+, should do 'a

---

### Post by mister_k81 on 2008-05-01
The only other suggestion I have is to run Google Earth in the terminal and post the error message here, in hopes that someone might be able to figure it out.

---

### Post by sweeneytodd on 2008-05-05
sudo googleearth worked, so if anyone else has no earth try this first, if not at least you know its a permission thing

---

### Post by chrisccoulson on 2008-05-05
It is likely that you ran Googleeath from the installer, which means your Googleearth profile (~/.googleearth and ~/.config/Google) is now owned by root and not writable by yourself - which is why running it with sudo works.

You need to fix this by:
```
sudo chown -R *<user_name>*:*<user_name>* ~/.googleearth
sudo chown -R *<user_name>*:*<user_name>* ~/.config/Google
```
...replacing *<user_name>* with you user name

---

### Post by kesman on 2008-05-05
I installed google earth 4.3 a week ago, didn't work so uninstalled. Then installed again two days ago and now it works, dunno what has changed but it complained about not to be able to connect to servers. Now works like a charm.
Surprisingly there was 3d models of my home town Helsinki in Finland too :D

---

### Post by dondad on 2008-05-05
> **sweeneytodd said:**
> can someone please tell me how to install googleearthlinux, i have a bin file on the desktop

How do you get thae .bin file to run?

---

### Post by chewearn on 2008-05-05
> **kesman said:**
> Surprisingly there was 3d models of my home town Helsinki in Finland too :D

One of your town folk must have a lot of free time in his hands.  :lol:
If you can find out who, you could whack him in the head for his trouble.  :lol:

---

### Post by kesman on 2008-05-05
> **dondad said:**
> How do you get thae .bin file to run?

You don't, install google earth from add/remove applications or with synaptic package manager.

---

