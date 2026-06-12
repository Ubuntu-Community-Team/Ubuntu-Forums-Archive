---
title: "Wpa supplicant - a few questions on setting up"
date: 2012-12-05
forum: General Help
---

### Post by sunfromhere on 2012-12-05
(Ubuntu 12.04)

Hi, I need to connect to wireless network on my college. It cannot be done in Ubuntu's wi-fi graphical manager, but needs to have a wpa_supplicant.conf file with the correct info (I have the info).

My Ubuntu installation didn't create the .conf file, so do I:

a) copy the example file and just append the info at the end 
or
b) create a new .conf file which has only the correct info?

1. How will this file effect my other wireless networks (home, office etc)? Do they need to be put in the .conf file also?

2. What to do after creating/editing this file? How do I connect to the said network? Can it be made so it connects from Ubuntu's wifi manager?

I messed around with wpa_supplicant on Arch, but this bugs me.

Thanks

---

### Post by sunfromhere on 2012-12-08
I would greatly appreciate some help here.
I have since read wpa supplicant man pages, help pages, wiki etc and have concluded that messing with one network connection )by creating a new .conf file) will have effect on my other connections (esp. if I change something in network/interfaces). 

Is there a way to have wpa_supplicant for only one connection and leave all others to network manager?

---

