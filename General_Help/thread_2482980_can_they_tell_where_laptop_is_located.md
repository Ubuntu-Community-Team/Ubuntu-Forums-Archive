---
title: "can they tell where laptop is located?"
date: 2023-01-16
forum: General Help
---

### Post by hbyan on 2023-01-16
Hi
I realize this question might seem too tinfoil hat, but we all have our own tolerance levels for privacy. 

Assuming that there isn't an independent secret gps inside a laptop, and I install ubuntu on it and turn off location services, and I move the laptop around from location to location, can "they" tell where the laptop is located at any given time? I dont have a specific adversary, "they" means anybody, anybody living on the earth.

---

### Post by grahammechanical on 2023-01-16
Ubuntu documentation says this:

> Geolocation, or location services, uses cell tower positioning, GPS, and   nearby Wi-Fi access points to determine your current location for use in   setting your timezone and by applications such as Maps. When   enabled, it is possible for your location to be shared over the network with   a great deal of precision.

[https://help.ubuntu.com/stable/ubuntu-help/privacy-location.html](https://help.ubuntu.com/stable/ubuntu-help/privacy-location.html)

With Location Services disabled the OS and applications using the OS will not reveal your location. But if you still have the WiFi adapter switched on then any wireless access point in range will detect the WiFi adapter's broadcast signal. WiFi adapters are radio transmitters as well as receivers. 

Mobile/Cell phones also transmit their location and connect to cell towers that they come in range of.

Regards

---

### Post by philhughes on 2023-01-16
Any one who obtains your IP address (eg a website you visit) can often get a reasonably accurate idea of your location. Geolocation by IP address is not always accurate, and of course assumes you are not using means to change your address eg by using a VPN. If you are not connecting to the internet, then of course this is not possible.

As an example, type "what is my IP address" into Google and click on some of the links.

---

### Post by TheFu on 2023-01-16
Google and Amazon have created location-to-SSID maps that they use for geolocation.  So, if you have wifi enabled and live in a country with either of those companies doing deliveries or "Street View", expect someone can figure out within a few houses where you are.

If you don't use wifi and only use wired ethernet, then it is a big of a hit or miss effort.  

If I disallow location and only allow the IP address to be used, [https://www.where-am-i.co/my-ip-location](https://www.where-am-i.co/my-ip-location) is not correct, but pretty close.  They seem to have my IP location to within about 30K people. ;)  Good lock with that.
If I allow the browser to use location services ... which don't exist ... it is off about 10 miles.
Most other Geolocation online services put me 40 miles away.

My phone number is way off - over 50 miles based on the NPA-Nxx ... for the telecom people.  That could be due to my metro area having the largest toll free calling overlays in the world with 5 different areacodes covering the same areas.  We've had 10 digit dialing mandated for almost 30 yrs here.  To call my next door neighbor, I have to dial 10 numbers whether their areacode is the same or different than mine.

With my IP, people can figure out a bunch of things because it is tied to a business.  They'd have nearly zero hope in finding the location using a phone number without access to the Govt E911 database.

---

### Post by hbyan on 2023-01-20
> **grahammechanical said:**
> Ubuntu documentation says this:



[https://help.ubuntu.com/stable/ubuntu-help/privacy-location.html](https://help.ubuntu.com/stable/ubuntu-help/privacy-location.html)

With Location Services disabled the OS and applications using the OS will not reveal your location. But if you still have the WiFi adapter switched on then any wireless access point in range will detect the WiFi adapter's broadcast signal. WiFi adapters are radio transmitters as well as receivers. 

Mobile/Cell phones also transmit their location and connect to cell towers that they come in range of.

Regards

thank you, this is a genius point that I had not thought about. so am I right that to combat this, you can do any of the following:
1) remove the wifi card when laptop is not in use
2) put ubuntu in airplane mode when laptop is not in use
3) remove the battery when laptop is not in use

---

### Post by hbyan on 2023-01-20
> **TheFu said:**
> Google and Amazon have created location-to-SSID maps that they use for geolocation.  So, if you have wifi enabled and live in a country with either of those companies doing deliveries or "Street View", expect someone can figure out within a few houses where you are.

If you don't use wifi and only use wired ethernet, then it is a big of a hit or miss effort.  

If I disallow location and only allow the IP address to be used, [https://www.where-am-i.co/my-ip-location](https://www.where-am-i.co/my-ip-location) is not correct, but pretty close.  They seem to have my IP location to within about 30K people. ;)  Good lock with that.
If I allow the browser to use location services ... which don't exist ... it is off about 10 miles.
Most other Geolocation online services put me 40 miles away.

My phone number is way off - over 50 miles based on the NPA-Nxx ... for the telecom people.  That could be due to my metro area having the largest toll free calling overlays in the world with 5 different areacodes covering the same areas.  We've had 10 digit dialing mandated for almost 30 yrs here.  To call my next door neighbor, I have to dial 10 numbers whether their areacode is the same or different than mine.

With my IP, people can figure out a bunch of things because it is tied to a business.  They'd have nearly zero hope in finding the location using a phone number without access to the Govt E911 database.

thanks, I don't know what you mean by "my phone number is way off" what does phone number have to do with location? I can get a miami area code from a at&t store located in san francisco.

---

### Post by TheFu on 2023-01-20
> **hbyan said:**
> thanks, I don't know what you mean by "my phone number is way off" what does phone number have to do with location? I can get a miami area code from a at&t store located in san francisco.

It wasn't always that way or easy.  In the olden days (2005-ish), you got the number the RBOC provided, period.  Your neighbor would be in the same NPA-NXX that you are in, because that's how telephone switching worked efficiently.  Some parts of the world still work that way for non-cellular phones.

---

### Post by MAFoElffen on 2023-01-20
> **TheFu said:**
> Some parts of the world still work that way for non-cellular phones.

I was going to make a comment and suddenly felt very old... Bahahaha!!!

---

### Post by TheFu on 2023-01-20
> **hbyan said:**
> thank you, this is a genius point that I had not thought about. so am I right that to combat this, you can do any of the following:
1) remove the wifi card when laptop is not in use
2) put ubuntu in airplane mode when laptop is not in use
3) remove the battery when laptop is not in use

If you unload the wifi drivers, that's should do it.  The other methods are a little too much hassle and unnecessary for laptops.  Who would remove a battery from a laptop?

As for phones or cellular network devices, obviously the local tower will have an idea of where you are and if you're using emergency services, then the phone will send GPS coordinates.  There are lots of different sorts of phones.  In my country, it is a legal requirement for phones to provide their GPS coordinates if emergency services are called. It wasn't always that way and I wouldn't presume that all countries have the same requirements.

If your phone is in range of 2 or more cell towers, then triangulation can be used to get closer to your location. It isn't an exact science - think 2500m² as the area of uncertainty, whereas GPS should be withing 100m² in normal locations.  Large buildings or lots of metal can make GPS locations off.  As any geocacher.

---

### Post by hbyan on 2023-01-20
> **TheFu said:**
> If you unload the wifi drivers, that's should do it.  The other methods are a little too much hassle and unnecessary for laptops.  Who would remove a battery from a laptop?

As for phones or cellular network devices, obviously the local tower will have an idea of where you are and if you're using emergency services, then the phone will send GPS coordinates.  There are lots of different sorts of phones.  In my country, it is a legal requirement for phones to provide their GPS coordinates if emergency services are called. It wasn't always that way and I wouldn't presume that all countries have the same requirements.

If your phone is in range of 2 or more cell towers, then triangulation can be used to get closer to your location. It isn't an exact science - think 2500m² as the area of uncertainty, whereas GPS should be withing 100m² in normal locations.  Large buildings or lots of metal can make GPS locations off.  As any geocacher.

I don't know how to unload the wifi drivers. seems kind of annoying to install and uninstall drivers every time I need to use the laptop. isn't it easier to just put ubuntu in airplane mode?
another question. The point of privacy is to blend in and not stand out. That's why I am against faraday bags for cell phones because I think if a cell phone suddenly disappears off the face of the earth that's weird and it draws attention. 
How many other laptops in the world suddenly become undetectable? is there any other reason a laptop would become undetectable other than the owner purposely making it undetectable?

---

### Post by Holger_Gehrke on 2023-01-20
He didn't say 'uninstall' he said 'unload'. Drivers in Linux are modules for the kernel which can be loaded into and removed from memory with the commands 'insmod' / 'modprobe' and 'rmmod'.

Holger

---

