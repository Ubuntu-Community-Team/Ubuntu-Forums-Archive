---
title: "can't log in: log screen loop"
date: 2013-02-27
forum: General Help
---

### Post by csad on 2013-02-27
Hello,

I've got a big problem here and badly need help. Don't know what happened, but I can't log into my computer anymore. Or to be more precise, I keep logging in, and there is the usual black screen with the usual start process messages, but only for barely a second, and then it's back to the login page. 

I can't even log in to the guest account. On the other hand, it is possible to log in using text only modus with ctrl+alt+f1, just as there are no problems to use a live usb stick as I'm doing now.

But, and this may well be relevant:  

* prior to this, I kept getting the error message "permission denied" in the file manager pcmanfm, which has my home folder as the start folder. The "file system" entry had also disappeared from the locations bar on the left side. 

* In the live usb environment, I can easily access all my data on my home folder--if I open up the folders as root.

So maybe it's a problem with permissions? Or is it an X-server crash? Lightdm problem? I really don't know. 
 
I use Xubuntu 12.04, 64bit (and have also Gnome installed).  This is my graphic card: 
```
lspci -nnk | grep -i VGA -A2 
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation Device [10de:1055] (rev a1) 
    Subsystem: Sony Corporation Device [104d:908b] 
    Kernel driver in use: nouveau 

```Does anyone have any ideas here? How do I solve this problem? Thank you in advance. :)

---

