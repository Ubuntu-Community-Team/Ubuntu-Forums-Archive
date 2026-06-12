---
title: "BT changed broadband channel"
date: 2013-08-20
forum: General Help
---

### Post by ex-para on 2013-08-20
I have a laptop working as a server for a website on Ubuntu for the last five years with no problems until BT changed the channel as my broadband was going on and off. I have been into my Home-hub and seen it is now on 11 but now matter what I do I cant get the website back online. Any suggestions will be appreciated.

---

### Post by papibe on 2013-08-20
Hi ex-para.

A few thoughts:

Not all laptops are built to work 24/7. Some would do OK, but some may overheat and then components will start to fail (wireless card for instance).

I would personally avoid providing any kind of service over wireless. I'd prefer using a ethernet cable.

Having said all that, I've seen a lot of cases where a neighbor gets a new powerful router and starts interfering with your own. Specially if they are using the same channel. The solution is simple, choose a different channel.

There are several alternatives to diagnose the 'neighbor problem'. The easiest would be to use an Android app like WiEye, or Wifi Analyzer. Here are a couple of related articles: [Change the Wi-Fi Channel Number to Avoid Interference]("http://compnetworking.about.com/od/wifihomenetworking/qt/wifichannel.htm"), and [When Defaults Are Bad: How To Pick a Unique Wireless Channel For Your Router]("http://compnetworking.about.com/od/wifihomenetworking/qt/wifichannel.htm").

Hope it helps. Let us know how it goes.
Regards.

---

### Post by ex-para on 2013-08-20
Maybe I shoud have mentioned it is on an ethernet cable and the laptop has worked for years 27/7 and I live in a remote part of the UK with no neighbores for half a mile but I thank you taking the trouble to reply.

---

### Post by ajgreeny on 2013-08-20
I know the BT router/hub has some idiosyncrasies, but surely they do not set the channel used remotely, do they?
You should be able to change it if you go to the hub's configuration page in your browser.

---

### Post by ex-para on 2013-08-21
Thanks for the reply, BT did change the channel at their end and yes I can change it if I need to but my problem is getting my site back on line. I have done the bit in port forwarding like putting the http www and the laptop name in where they should be but still not back on line.

---

### Post by lisati on 2013-08-21
> **ex-para said:**
> Thanks for the reply, BT did change the channel at their end and yes I can change it if I need to but my problem is getting my site back on line. I have done the bit in port forwarding like putting the http www and the laptop name in where they should be but still not back on line.

Is your device one of the [BT Home Hub 3]("http://www.techradar.com/news/internet/broadband/bt-home-hub-3-reduces-wi-fi-interference-926330") devices? If so, you might want to look at adjusting its "Smart Wireless" settings.

---

### Post by coffeecat on 2013-08-21
> **ex-para said:**
> Maybe I shoud have mentioned it is on an ethernet cable

Are you saying that the laptop server is connected to the BT Home Hub router by an ethernet cable? In which case the wireless channel would be irrelevant. Perhaps you could confirm.

If BT reconfigured the router remotely, they may also have changed your IP address.

---

### Post by coldraven on 2013-08-21
> **coffeecat said:**
> Are you saying that the laptop server is connected to the BT Home Hub router by an ethernet cable? In which case the wireless channel would be irrelevant. Perhaps you could confirm.

If BT reconfigured the router remotely, they may also have changed your IP address.

A residential internet connection will have a dynamic IP address and has probably changed.
You might just have been lucky and had the same one all this time.
I live in a remote place and my ISP rides on BT Wholesale’s backbone and my IP address has not changed in years.

---

### Post by coffeecat on 2013-08-21
> **coldraven said:**
> A residential internet connection will have a dynamic IP address and has probably changed.

Not necessarily. It depends on the ISP - at least in the UK. Mine has allocated me a fixed IP address even though I never asked for one. Others will if you ask or pay an extra fee. I really don't know about BT Retail's policy, but a fixed IP is obviously a must for a webserver, so the OP needs to check this.

---

### Post by Cheesemill on 2013-08-21
If the OP has a HomeHub then it's a residential BT connection, this means that it has a dynamic IP.

The only way to get a fixed IP with BT is to go with one of their business packages.

---

### Post by btindie on 2013-08-21
It may be that BT have decided to put you onto a shared public IP address which will screw things up. I only found out last week that they were doing it.

There's information on how you can check here [http://btsupport.custhelp.com/app/answers/detail/a_id/44044/c/6433](http://btsupport.custhelp.com/app/answers/detail/a_id/44044/c/6433) and how to opt out of their crippled service offering.

---

### Post by ex-para on 2013-08-21
My laptop server is connected to the BT Home Hub router by an ethernet cable.
The IP is dynamic but hardly ever changes and I check it every day using DYNDNS, if it does change I can alter it from any computer even if not in the country. I have not yet gone into the Smart Wireless" settings but I will. If I change the channel I will get drop out problems again. Thanks for the replies my problem might lie in the configuring the home hub like I did 5 years ago but I can not remember what I did. I built the website myself with help from w3schools and again I have trouble remembering how I did it so any info on configuring the hub would be of help.

---

### Post by ex-para on 2013-08-21
I have played about with the hub settings as I was convinced my problem was there as the only thing different  was the change of channels, the site is now back on line. As it is more than five years   since I built the site myself with help from w3schools I have forgotten how I did everything. My IP is dynamic but hardly ever changes but I check it every day using DYNDNS and if it does change I can fix it from any computer even from another country. I thank every one that replied to me thank you.

---

