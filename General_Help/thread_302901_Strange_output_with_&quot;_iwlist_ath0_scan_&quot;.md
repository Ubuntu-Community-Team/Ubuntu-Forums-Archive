---
title: "Strange output with &quot; iwlist ath0 scan &quot;"
date: 2006-11-19
forum: General Help
---

### Post by kent41 on 2006-11-19
hi
 When I run iwlist ath0 scan I get the following output.
```
ath0      Scan completed :
          
          Cell 01 - Address: 00:0F:B3:E0:45:1C
                    ESSID:"202581792BE"
                    Mode:Master
                    Frequency:2.452 GHz (Channel 9)
                    Quality=39/94  Signal level=-56 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/sp
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:bcn_int=200
          Cell 02 - Address: 00:0F:B3:E0:45:1C
                    ESSID:""
                    Mode:Master
                    Frequency:2.452 GHz (Channel 9)
                    Quality=40/94  Signal level=-55 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:bcn_int=200

```

Notice the mac address is the same for both connections but the ESSID: is different, how can the be. Has someone taken over my WIFI ?

I have an Actiontec modem/router. This problem just started.

---

### Post by yopnono on 2006-11-19
Try to change the ESSID on you router/ap and see what happens

---

### Post by kent41 on 2006-11-19
Is there something wrong with the ESSID ?

Listing 1 & 2 are the same hardware.

---

### Post by doobit on 2006-11-19
Could be seeing a reflection. the scan function is very fast.
Move your router to a different place ( afew feet away) and try it again.

---

### Post by wieman01 on 2006-11-19
What router have you got?

---

### Post by kent41 on 2006-11-19
> **doobit said:**
> Could be seeing a reflection. the scan function is very fast.
Move your router to a different place ( afew feet away) and try it again.

Hi thanks for the reply

Currently  I am about 20 feet from the router.  and at this moment I dont see the second display with a null "" ESSID. It seems to come and go with no pattern i can notice.

---

### Post by kent41 on 2006-11-19
> **wieman01 said:**
> What router have you got?

I have an Actiontec router  from verizon.

---

### Post by wieman01 on 2006-11-19
It must be the same device. Could be as Doobit has suggested: The scanning speed. Try changing your router's wireless settings. Nothing to worry about though.

---

### Post by yopnono on 2006-11-20
> **kent41 said:**
> Is there something wrong with the ESSID ?

Listing 1 & 2 are the same hardware.

Yes I can see that, but if you like to find and fix any problems, you normally need to start somewhere. In this case I would have started with the ID of the router.

---

### Post by kent41 on 2006-11-20
I am new to linux and I am not sure what you mean start with the ID of router.
Can you explain?

BTW the null ESSID is back

---

### Post by doobit on 2006-11-20
> **kent41 said:**
> Hi thanks for the reply

Currently  I am about 20 feet from the router.  and at this moment I dont see the second display with a null "" ESSID. It seems to come and go with no pattern i can notice.

Still sounds like a reflection to me. I could be wrong. Move around in the area and look at the signal strengths.

---

### Post by kent41 on 2006-11-20
ok I moved around to check signal strength and found a -37dBm right next to the router and -66dBm about 20 feet from router. however the ghost ESSID was still there.

Also a interesting fact is I installed WIFI-RADAR and I don't see the ghost ESSID.

I there a problem with Ubuntu Edgy and iwlist because I dont see the problem when I exchange the hard drive in my laptop with a Windows hard drive.

---

### Post by kent41 on 2006-11-22
bump

---

### Post by wieman01 on 2006-11-22
The question is if the "ghost" ESSID (which I believe is a reflection of you actual network) causes any problem. If not, then I'd just leave it. It would be interesting to know what the root cause is, however, since it's no immediate problem I would just ignore it.

---

