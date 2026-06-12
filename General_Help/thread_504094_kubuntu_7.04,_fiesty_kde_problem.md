---
title: "kubuntu 7.04, fiesty kde problem"
date: 2007-07-18
forum: General Help
---

### Post by markeee on 2007-07-18
Hi

i seem to have come across a problem, i rebooted my kubuntu machine and now at login when i type in my pass to login to a kde session, screen goes black-nothing happens at all, no errors etc just black


just rebooted-entered my user/pass and tried to login, and well screen goes black, cursor moves then it goes back to login screen? so must be an issue with KDE-would the best idea be to reinstall whole of KDE(not sure how)
im not sure-what this is caused by> as it was working before
what to check(what logs) for error messages
and how to fix it

suggestions appreciated

when i select restart x server, screen flickers then it goes back to login-i assumed meant successful restart?

thanks guys

mark

---

### Post by AlexenderReez on 2007-07-18
i think you just need to reinstall kdm...boot in recovery mode...then

> login

enter passwords and username...

> sudo apt-get remove kdm
sudo apt-get install kubuntu-desktop
sudo reboot
 -->this want to make sure there is nothing wrong with your system:)

---

### Post by markeee on 2007-07-18
thanks mate

you say remove kdm shouldnt i then add it again?

just gonna try
sudo apt-get remove kdm
sudo apt-get install kubuntu-desktop
sudo reboot



do i not need sudo apt-get install kdm


cheers mate

---

### Post by markeee on 2007-07-18
removing kdm then installing kubuntu-desktop

dont i need to reinstall kdm again then

also kubuntu=desktop, was already installed, no? 


sorry for all the questions

---

