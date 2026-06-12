---
title: "usb ports"
date: 2021-08-14
forum: General Help
---

### Post by T6&amp;sfpER35% on 2021-08-14
hi 
i've got a new laptop with 4 usb ports and accordingg to ***lsusb ***1 of the ports is usb3. 
how can i determine which 1 of the ports is usb3 ,without trying each one to see which is faster?

terminal output :

```
[FONT=Verdana]jp@14:~$ lsusbBus 002 Device 003: ID 413c:818e Dell Computer Corp.[/FONT]
[FONT=Verdana]Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub[/FONT]
[FONT=Verdana]Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/FONT]
[FONT=Verdana]Bus 001 Device 005: ID 08ff:2810 AuthenTec, Inc. AES2810[/FONT]
[FONT=Verdana]Bus 001 Device 004: ID 0c45:648b Microdia Integrated Webcam[/FONT]
[FONT=Verdana]Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub[/FONT]
[FONT=Verdana]Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/FONT]
[FONT=Verdana]Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub[/FONT]
[FONT=Verdana]Bus 003 Device 002: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse[/FONT]
[FONT=Verdana]Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/FONT]
[FONT=Verdana]jp@14:~$[/FONT]
```


thanks!

---

### Post by T6&amp;sfpER35% on 2021-08-14
btw ,what is the correct way to post terminal output here ?

---

### Post by sudodus on 2021-08-14
Please post the output between code tags like this
 
[noparse]```

output

```[/noparse]
 
to get output like this
 
```

output

```

I think you put the first closing bracket ] in the wrong place (relative to the text)

---

### Post by sudodus on 2021-08-14
Often but not always, the USB 3 port has blue plastic inside while USB 2 has white or black plastic.

Edit:

What about looking for it in a user manual for the computer (find one via the internet)? There is often a description of all the ports with detailed illustrations.

---

### Post by T6&amp;sfpER35% on 2021-08-14
sudodus thanks for that yes i now notice i pasted bit skew ,but wasn't sure if i must use the codes tags in the 1st place, now i know.
i've searched and saw that a usb3 port will have a blue inner ,but i don't see anything blue . might be cause it's an old lappy (but a new one for me lol) ,and it's worn off.
i'll have a look at the model manual and see if it shows .

EDIT: fixed the code tags in 1st post

---

### Post by T6&amp;sfpER35% on 2021-08-14
ok iv'e found it in manual ...(feels like idiot)
looks like there's 2 usb3 ports , idk, anyway ,just need 1.
THANKS !

---

### Post by sudodus on 2021-08-14
You are welcome. I'm glad that you found what you wanted to find :-)

---

