---
title: "[SOLVED] program for DSL"
date: 2006-12-10
forum: General Help
---

### Post by nga911 on 2006-12-10
hi , is there any program for Ubuntu 6.10 to dial the ppp connection at start up , i have to configure the connection every time i use Ubuntu ](*,) ](*,) ](*,) ](*,)

---

### Post by padre999 on 2006-12-10
I am not sure what kind of DSL you use. 

But you could try pppoeconf. Just open a Terminal and type "sudo pppoeconf". There you can setup a DSL over Ethernet connection with name and password. You can also tell it to automatically dial in when booting.

If this is not for you let us know what hardware/DSL you use.

---

### Post by nga911 on 2006-12-10
hello,
am using pppoeconfig tool and it works but it dosnt start at boot time ween i tell it to ](*,) ](*,) 
am using a standard DSL modem (don't know what brand):-k

---

### Post by padre999 on 2006-12-10
Could it be that you use a cable extension for modem and computer with a power switch, so that you switch the computer and modem on and then boot immediately?
My DSL Modem for example needs a minute after being switched on to establish a DSL line. So if I switch modem and computer on and boot straight away I get the same result as you because the modem was not ready yet.
Solution would be to switch on the modem first, wait a minute and then boot the computer.

If that's not the case obviously something is wrong with pppoeconf here.

edit-------------

If you search the forums a bit you will find that you are not the first one to experience this problem. See [http://ubuntuforums.org/showthread.php?t=236858](http://ubuntuforums.org/showthread.php?t=236858) for example.

---

