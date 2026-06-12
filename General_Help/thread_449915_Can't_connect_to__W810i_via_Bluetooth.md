---
title: "Can't connect to  W810i via Bluetooth"
date: 2007-05-20
forum: General Help
---

### Post by Bealer on 2007-05-20
Hi, I'm having problems pairing with my Sony W810i mobile phone. 

I can see the device by putting:
```
hcitool scan
```

But when I try to connect by using
```
sudo hidd -connect 00:16:B8:53:FC:5B
```

It just won't work. It times out. I've enabled bluetooth on the phone, but don't get a prompt that something is trying to connect. 

Also my phone can do a search but isn't able to see my computer as a device. 

Am I missing something, a basic package of some sort etc... that is stopping the two pairing?

Thanks.

---

### Post by reclusivemonkey on 2007-05-22
I don't think this is it, but I am posting it anyway as I just happened to read it the other day, and I doubt you would find it just googling ;-)

[http://www.adamish.com/geekish/k700_bluetooth_remote_linux_freeze_fix.php](http://www.adamish.com/geekish/k700_bluetooth_remote_linux_freeze_fix.php)

---

### Post by Bealer on 2007-05-22
I got it working but wasn't able to properly determine the problem. If I sat my phone just over a metre from the bluetooth dongle it would be temperamental and only pick it up once in a while. 

I then sat the phone 10cm from the dongle. The first time the phone asked me for a PIN which I put in, but got no response from Ubuntu. I tried a few times then it worked. 

The strange thing is I can now sync my phone from over 2 metres away without any problems, yet earlier it couldn't even see it if it was that far.

---

