---
title: "Number Lock Before Logging In - Lubuntu"
date: 2019-09-21
forum: General Help
---

### Post by rbscebu on 2019-09-21
I would like my number lock to be on at the login screen so that my numeric keypad can be used during login in Lubuntu.

I know the number lock problem has been address numerous times in this forum, however I cannot find a solution to my problem that works in Lubuntu 18.04. All the solutions that I have found are for Ubuntu and they do **not** work in Lubuntu.

So far I have installed numlockx with the Synaptic Package Manager. I then:
```
sudo nano /etc/xdg/lubuntu/lxdm/lxdm.conf
```
uncommented numlock and set that variable to 1. That automatically turns my numloc on AFTER I log in.

The problem remains, how to turn numlock on before logging in?

---

### Post by Skaperen on 2019-09-21
someone who knows how to do this needs to do it with a file change discovery program running and figure out which file gets changed to keep the setting persistent.  it has to do that in order to make it active before login.  maybe many DEs use the same file if lightdm greeter is used.  if so, then i might be able to make a script that sets it and unsets it that is pan DE.

---

### Post by him610 on 2019-09-22
> how to turn numlock on before logging in?
You can set it in your Bios/Uefi utility. Review your motherboard manual.

---

### Post by rbscebu on 2019-09-28
Unfortunately I do not have a motherboard manual and my BIOS give no option the set the numlock at startup.

---

