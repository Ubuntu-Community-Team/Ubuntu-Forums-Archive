---
title: "Trickle problem (speed limit can't be changed)"
date: 2016-12-02
forum: General Help
---

### Post by bultol on 2016-12-02
Hello all!


I have a problem.

Today, I decided to use a bandwidth limiter, trickle. 

sudo apt-get install trickle
sudo trickle -d 500 -u 250


Now, the problem is I can't change these values! I am stuck  witch 500 kbps and can't change it! I deleted (sudo apt-get remove  trickle), reinstalled, use a "-s" after "sudo" to make change, nothing  did the job! I also sudo purged and sudo autoremoved.


Thank you! :)

---

### Post by #&amp;thj^% on 2016-12-02
If you are using systemd IE: Ubuntu 16.04 you could try this:
```
sudo systemctl stop trickle.service
```
This is just kind of shot in dark though. As I know nothing about trickle.

---

### Post by bultol on 2016-12-02
Thank you for the help but it don't work for me. systemctl command not found.

---

### Post by #&amp;thj^% on 2016-12-02
> **bultol said:**
> Thank you for the help but it don't work for me. systemctl command not found.

So ok might be helpful to know what Version you are running then.
```
lsb_release -a
```
Will show this.;)
EDIT: You may also have to reinstall it to set the values back to default. I just noticed you had already uninstalled it.
So that would make sense for "systemctl command not found"
Hopefully someone more knowledgeable with Trickle will chime in.

---

### Post by kpatz on 2016-12-02
Try:
```
sudo apt-get --purge remove trickle
sudo apt-get --purge autoremove
```
Just run the 2nd command if you already uninstalled Trickle.

Also have you tried rebooting?

---

### Post by bultol on 2016-12-02
Version: 

Ubuntu 14.04 LTS

sudo apt-get --purge autoremove
Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances       
Lecture des informations d'état... Fait
0 mis à jour, 0 nouvellement installés, 0 à enlever et 510 non mis à jour.


sudo apt-get --purge autoremove
Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances       
Lecture des informations d'état... Fait
0 mis à jour, 0 nouvellement installés, 0 à enlever et 510 non mis à jour.


And yes, already rebooted several times... Still stuck at 500 kbps.

And already reinstall it to set back the value, nothing take effect.

I also reinstalled to try systemctl command, still not found.


Thank you.

---

### Post by #&amp;thj^% on 2016-12-02
> **bultol said:**
> Version: 

Ubuntu 14.04 LTS

sudo apt-get --purge autoremove
Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances       
Lecture des informations d'état... Fait
0 mis à jour, 0 nouvellement installés, 0 à enlever et 510 non mis à jour.


sudo apt-get --purge autoremove
Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances       
Lecture des informations d'état... Fait
0 mis à jour, 0 nouvellement installés, 0 à enlever et 510 non mis à jour.


And yes, already rebooted several times... Still stuck at 500 kbps.

And already reinstall it to set back the value, nothing take effect.

I also reinstalled to try systemctl command, still not found.


Thank you.
14.04 This is not a "systemd" system...so try this
```
sudo /etc/init.d/trickle stop
```

---

### Post by bultol on 2016-12-02
sudo trickle**_d_** -d "value" -u "value" seems to work!!!

I think the problem is solved. I will come back if it try to get on my nerves again! :rolleyes:


Thank you!

---

### Post by bultol on 2016-12-02
The problem not solved in fact I think. My connection goes mad... I tried to set value to 100 kbps to test if it worked well, rebooted, and nothing change. I mean, speed goes to 1 mb/s but not over! And it seems to be capped at the first value I set when I installer this software. 1 mb/s. Now my connection goes mad, making yoyo from 300kbps to 1mbps...

sudo /etc/init.d/trickle stop command not found. I looked at init.d, there is no trickle in it (but trickle is installed).

---

### Post by kpatz on 2016-12-02
```
sudo apt-get --purge remove trickle
sudo killall trickled
```

Then see if you have a /etc/trickled.conf file, delete it if you do.

Then reboot.

---

### Post by #&amp;thj^% on 2016-12-02
Just noticed this...but had to translate to be sure.
> Reading packet lists ... Done Build dependency tree Read status information ... Done 0 updated, 0 newly installed, 0 to be removed _**and 510 not updated**_
May or may not be part of the problem.
So try this for me: Run one line at a time.
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```
The last command will not take you to a newer OS version it will simply update your system fully.
And I would reboot after.
After you do what kpatz requested.

---

### Post by bultol on 2016-12-02
Thank you for the help.

I don't know it it work for now, a member of my family is using internet right now, so I can't know my full speed.

At sudo apt-get upgrade, there was a HUGE upgrade. It took almost 40 minutes I think.

And for the "sudo apt-get --purge remove trickle" and "sudo killall trickled" commands after the reboot, they did not work because trickled was already uninstalled. And no /etc/trickled.conf. So theoretically, it should work now?

Thank you!

---

### Post by #&amp;thj^% on 2016-12-02
Fingers Crossed....And keep us updated.
Kind Regards

---

### Post by bultol on 2016-12-02
I hope it worked!

I will keep you updated.

Thank you! :)

---

### Post by bultol on 2016-12-02
I worked! :)


Thank you a lot!

---

### Post by #&amp;thj^% on 2016-12-02
Cool! I am glad to hear this...enjoy.

---

