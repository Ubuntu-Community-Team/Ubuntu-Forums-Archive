---
title: "Xubuntu 12.04: USB Mouse does not work"
date: 2014-02-21
forum: General Help
---

### Post by jv69 on 2014-02-21
Hello,  I just installed Xubuntu 12.04 on a Dell Optiplex GX620. I was given a Gateway Keyboard and Mouse to use temporary. 
The keyboard works, but no mouse. Searched many web pages on mouse problem. 
I opened a tty (CTRL-ALT F1)  and performed the following:
sudo -update -usbids 
sudo modprobe -r psmouse;
sudo modprobe ehci-hcd  ( ehci-hcd is not installed) 


Then I went to Applications -> Settings, , using F10 and arrow keys on the 
keyboard but there is no mouse configuration options. Currently running updates
to see if something was missed. 

Any help is appreciated.
thanks

---

### Post by howefield on 2014-02-21
Thread closed, duplicate here : [http://ubuntuforums.org/showthread.php?t=2207012](http://ubuntuforums.org/showthread.php?t=2207012)

---

