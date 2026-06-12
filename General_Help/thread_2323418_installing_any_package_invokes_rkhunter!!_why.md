---
title: "installing any package invokes rkhunter!! why?"
date: 2016-05-05
forum: General Help
---

### Post by a-you on 2016-05-05
This is insane: for some reason every time I install anything with synaptic or on the command line with apt-get install at the end of that install process rkhunter is run, apparently it's running --propupd, meaning that it's updating rkhunter to say that "everything if fine on this system"!!! This is TOTALLY IDIOTIC because it assumes that the simple fact that I'm installing something means that my system is clean. That is an absurd assumption!! If it does have a rootkit then how am I going to know that?

How in the world can I stop this from happening??? Please, any advice MUCH appreciated!!! I have disabled the rkhunter "apps" test but I don't know what else to do.

Ubuntu studio xenial 64 bit

---

### Post by Habitual on 2016-05-05
Who installed rkhunter?

---

### Post by deadflowr on 2016-05-05
Look in /etc/default/rkhunter, and see what the line for APT_AUTOGEN= says.
If true, you need to switch it to false.

---

### Post by a-you on 2016-05-07
Thank you both for your answers! @habitual: I installed it using synaptic. @deadflowr: thanks; I checked and in rkhunter.conf for my version of rkhunter 1.4.2 there's no variable called APT_AUTOGEN. But checking for something similar I discovered that there is one called UPDT_ON_OS_CHANGE which seems to do what you were pointing out. BUT it is commented out and the default value is 0, so it seems like that shouldn't be causing this. I'll try uncommenting it and explicitly setting it to 0.

---

### Post by a-you on 2016-05-08
@deadflowr: explicitly setting UPDT_ON_OS_CHANGE to 0 seems to have fixed that. Thanks again for the tip that led to that. Seems like an rkhunter bug because it's supposed to use the default but didn't seem to be doing so in that case.

---

