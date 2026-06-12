---
title: "linux-686 and kernel questions - linux-image"
date: 2006-12-27
forum: General Help
---

### Post by ice60 on 2006-12-27
hi, i installed linux-686 to go with my processor. so now i have 386 and 686 kernels installed and i use the 686 one. 

i wanted to ask if there's any need to keep the 386 kernels? or if it's just ok to uninstall them. 

i got the idea from [this](http://www.ubuntuforums.org/showthread.php?t=186792) post. it says this down the page
```
sudo aptitude install linux-686
```

i've attached the bottom of my grub menu to show what i mean. thanks :)

---

### Post by scrooge_74 on 2006-12-27
Well I have not yet remove the 386 kernel, from my laptop, I just kind of forgot  ;)

If after a couple of days you see that you are not experiencing any problems I suppose you don't need to keep it.

---

### Post by veli on 2006-12-27
you can safely remove the 386 kernel from Synaptic. I don't think that you'll have problems with 686, which is compiled by the Ubuntu team. If you make your own kernel though, it's better to keep the 686 kernel in your boot loader, in any case.

---

### Post by scrooge_74 on 2006-12-27
if you break it, you keep it. :D

---

### Post by ice60 on 2006-12-27
OK, thanks for the help. i just wanted to make sure before i removed it incase there was a reason for keeping it which i hadn't thought of. it was starting  to get on my nerves abit for some reason lol. 

i use this version of ubuntu in a VM because it's very complicated to get installed on my hardware, but i have ubuntu on another computer with the same thing - 386 and 686 kernels. so, i'll uninstall the kernel in the VM first and use it for awhile to see how it goes, then uninstall the kernel on the other computer :D thanks for the help :cool:

---

