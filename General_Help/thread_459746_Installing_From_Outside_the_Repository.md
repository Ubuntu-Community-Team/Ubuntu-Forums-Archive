---
title: "Installing From Outside the Repository"
date: 2007-05-31
forum: General Help
---

### Post by randal on 2007-05-31
apt-get and other package managers are very convenient to use. Just find the repository and you'll be running in no time. But it really interests me how to install packages you get as archived folder. By installing, it means your system recognizes the application. I've had experience with tars that you extract and run the ./configure and do something else and have the application installed and recognized by the system given you have all the dependencies. But how about applications like Azureus and Firefox that as soon as you extract you can get going but your it just doesn't feel they're part of the entire system. In Windows, if this is the case, I would edit the environment variables and manually create links on the start menu and elsewhere. I guess I could do the same with Linux (specifically Kubuntu) but I'm not sure how... any help?

---

### Post by randal on 2007-06-02
I'm not sure how integrated the applications I've setup our to my system but I made it work...

just a side note... the forum doesn't seem to be very active... hmnn

---

### Post by Ocxic on 2007-06-02
install "checkinstall"  form the repositories, then instead of running:
./config
make
make install

do this:
./config 
make
checkinstall

that will add the program to synaptic

---

### Post by andrew.46 on 2007-06-15
Hi,

 Read your comments below:

> **randal said:**
> I'm not sure how integrated the applications I've setup our to my system but I made it work...

just a side note... the forum doesn't seem to be very active... hmnn

 The guide where I picked up a lot of info on installing is:

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

 And yes the forums have been quiet. I have my suspicions that Ubuntu is flooded with refugees fron Wi[..]ws Vi[..]a.

                 Andrew

---

