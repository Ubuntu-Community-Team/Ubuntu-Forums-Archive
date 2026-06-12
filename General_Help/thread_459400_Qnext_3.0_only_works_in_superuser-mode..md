---
title: "Qnext 3.0 only works in superuser-mode."
date: 2007-05-30
forum: General Help
---

### Post by maol62 on 2007-05-30
I just installed [Qnext 3.0]("http://www.qnext.com") and to be able to use the file-, music- and photosharing (or streaming) service that comes with the application, there must be some ports open in the firewall, or UPnP should be enabled. Although my router supports UPnP I have not managed to get it to work so I just port forward the three ports mentioned in the Connection Wizard in Qnext, 80 and 443 as TCP and another as UDP.
Then, when launching the program as me, with the command:

```
./qnext
```

it looks promising, everything looks ok, except for the little led, in the qnext application. that showing if incoming connections are blocket, proxied or ok. In my case it is orange meaning that all incoming conncetions are proxied. Then I try to restart the router but that makes no difference.
I exit Qnext and start it with

```
sudo ./qnext
```

and now it works, the led is green! So I exit and start as a normal user, and then I get the orange led again.
So, Qnext works ok when started in superuser mode but not in normal user mode. Anyone who knows why this happens? The installation of Qnext is just unpacking a comressed file and I uncompressed it in ~/qnext, so its not much of an installation. Qnext is a java application, could it be some permissions regarding that which are wrong?

---

