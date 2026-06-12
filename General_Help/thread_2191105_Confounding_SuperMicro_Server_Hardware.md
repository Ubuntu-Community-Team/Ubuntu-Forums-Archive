---
title: "Confounding SuperMicro Server Hardware"
date: 2013-11-30
forum: General Help
---

### Post by rackit on 2013-11-30
Since you all are the smartest group of folks I know, here we go:

I have a[ SuperMicro ]("http://www.supermicro.com/products/system/4U/7045/SYS-7045B-8R_.cfm")[COLOR=#222222][FONT=arial][SuperServer 7045B-8R+]("http://www.supermicro.com/products/system/4U/7045/SYS-7045B-8R_.cfm") with a bad [COLOR=#222222][FONT=arial][SAS743tq]("https://www.google.com/search?q=SAS743tq&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a&channel=rcs") backplane. I removed the faulty backplane and connected the drives directly to the SATA on the MB and power direct from the PS. [SIZE=1](normally, you plug power and SATA into the backplane and then plug the drives into that.)[/SIZE] The disk controller and the fakeRAID chip are on the mobo. The backplane controls the pretty blinking lights next to each of the drive bays and has a buzzer for when things go awry. The backplane also allows for hot-swapability.

The box runs software RAID 6 via mdadm so I get failure/integrity warnings anyway - mdadm even tells me which drive(s) are going south. The pretty blinking lights are rarely seen as the box spends much of it's lonely existence in a dark, well ventilated closet. Actually, there are some Cisco managed switches, a router, a WAP, and an [AirVision]("http://www.ubnt.com/airvision") NVR in there too, so it's probably not that lonely. Don't really need hot-swap drives as the box is mostly a file and vpn server.

SuperMicro doesn't offer much technical info for us laymen (I'm not a SM distributor), so I am trying to determine if I am missing anything here that may preclude the lack of backplate[/FONT][/COLOR][/FONT][/COLOR]. Your valuable opinions are truly appreciated.

Bottom line: can I have a robust system without the backplate?

Running Ubuntu Server 12.04.3 LTS - jsyk :)

---

### Post by Bucky Ball on 2013-12-01
You have asked a support question on a poll in a non-support area. I would advise that you edit the first post and ask your support question in ***Server Platforms ***rather than here. Polls are polls, not support threads, and ***The Cafe*** is NOT a support area. Thanks. ;)

---

