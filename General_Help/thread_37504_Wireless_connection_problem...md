---
title: "Wireless connection problem.."
date: 2005-05-27
forum: General Help
---

### Post by byen on 2005-05-27
Hey fellas,
After finally figuring out the ndiswrapper work-around...I now have a connection running.. My WLAN card works perfectly except for the glitch where after turning on the computer i have to go to the Network connection settings and deactivate and re-activate my Wireless connection interface for the WLAN card to work and use the connection. Anyone know of any particular reason why this is happening?

Is there anyway i can run a command in the terminal to do this instead of having to manually do that everytime?

Please help. thank you for any suggestions you might have,
byen.

---

### Post by dave9191 on 2005-05-27
You can use the command in post 2 [http://ubuntuforums.org/showthread.php?t=30671&page=1](http://ubuntuforums.org/showthread.php?t=30671&page=1) to connect to your network. You can put them into a script file so that it will run all those commands for you. 

Dave

---

### Post by xristos on 2005-05-27
You can edit your /etc/network/interfaces file and add these 2 lines :

```
auto wlan0
iface wlan0 inet dhcp
```

---

### Post by byen on 2005-05-27
thank you dave and xritos for your replies. Xritos..those two lines are already in the link that you mentioned. the problem or may be my ignorance...is this.. After I start my computer my WLAN card starts up but fails to detect my network... though this is not all the time...about 25% of the time it does connect to my network but sometimes it just does not. SO i have to deactivate and reactivate my wlan to get it to connect.

My point being,...is there anyway where I can serach the networks available in my area ala..windows (sorry about the ref) and connect to the one i choose?because my school has a wireless network too and i do not know how to connect to it,,,,?

thank you fo your time,....
byen

---

### Post by xristos on 2005-05-28
[QUOTE=byen]thank you dave and xritos for your replies. Xritos..those two lines are already in the link that you mentioned. the problem or may be my ignorance...is this.. After I start my computer my WLAN card starts up but fails to detect my network... though this is not all the time...about 25% of the time it does connect to my network but sometimes it just does not. SO i have to deactivate and reactivate my wlan to get it to connect.

My point being,...is there anyway where I can serach the networks available in my area ala..windows (sorry about the ref) and connect to the one i choose?because my school has a wireless network too and i do not know how to connect to it,,,,?

thank you fo your time,....
byen[/QUOTE]
 ```
man iwconfig
man iwlist
```

---

