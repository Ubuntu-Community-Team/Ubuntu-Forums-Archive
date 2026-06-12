---
title: "Installed ubuntu cloud server but cannot access the webpage through phone using wifi"
date: 2015-04-18
forum: General Help
---

### Post by jayon on 2015-04-18
I have installed ubuntu 14.04 in Oracle virtualBox
the Ip address is 192.168.56.101
I can access the IP address(index.html) in my main browser and also the mozilla browser in virtual Box!
I made hotspot in my laptop and connected my phone to the same network of Lan wire!
when I access the same Ip address in my phone...It cannot be displayed?? :( please help???

---

### Post by jayon on 2015-04-18
please reply ASAP!! :(

---

### Post by jayon on 2015-04-18
I can access Localhost Xampp files on ma phone...then why cant the cloud server is not coming to the picture??

---

### Post by nerdtron on 2015-04-18
> I made hotspot in my laptop and connected my phone to the same network of Lan wire!
when I access the same Ip address in my phone...It cannot be displayed?? :sad: please help???


This is not ubuntu problem but a network problem. Be sure your IP addresses are all on the same LAN, IP of the Ubuntu, IP of Laptop and IP of the mobile phone should all be on the same LAN.

And, you can't expect people to "reply asap" as this is a volunteer forum. And most people (in the US) are probably sleeping by now.

---

### Post by jayon on 2015-04-18
sorry my BAD!
all are on same LAN....still I cant access my cloud on mobile!! which IP address should I use?? 192.168.56.101 is auto eth0 Ip address which is connected!!
I cant figure out anything ! please help and sorry for late night troubling :(

---

### Post by jayon on 2015-04-18
ufw status is INACTIVE!!!!
:(

---

### Post by nerdtron on 2015-04-18
What is your "cloud" is it installed on Ubuntu? Is this a webpage? You said you can access the index.html of the Ubuntu. What error are you seeing on your mobile? can you ping the ubuntu IP from your mobile phone?

---

### Post by jayon on 2015-04-18
Installed ubuntu 14.04......in oracle virtual box!!! when i use that IP address in my laptop browser or in virtualbox browser....the index.html is displayed!!
but when I use in my phone browser....it cannot connect!! "we are having trouble displaying this page"

---

### Post by nerdtron on 2015-04-18
Are you sure you can ping the IP of Ubuntu from the your mobile phone? what is the IP address of you mobile phone?

---

### Post by jayon on 2015-04-18
I donot know how to ping the IP of ubuntu?
u mean use the IP address right? I donot know the mobile IP address...m using hotspot from laptop!

---

### Post by nerdtron on 2015-04-18
> 

u mean use the IP address right? I donot know the mobile IP address...m using hotspot from laptop! 						

Android phone? click on the wifi hotspot you are connected to and you will see your device IP address. Since you use a hotspot, I'm guessing your wifi has different IP LAN from the LAN of the laptop and Ubuntu LAN. And what hotspot software are you using? there are a lot of troubleshooting we can do here.

To ping the IP of the Ubuntu from your mobile phone, install a terminal app, it will give you access to the command prompt on android and use it to ping the IP of the Ubuntu  server.

Another check you use, try to Ping your mobile IP, from Ubuntu, if Ubuntu can't ping your mobile phone, it still a network issue.

---

### Post by jayon on 2015-04-18
My cloud IP is 192.168.56.101
My mobile IP is 192.168.137.32

---

### Post by nerdtron on 2015-04-18
Different IPs, different LAN. You need to use a router as access point so that all devices have the same IP block.

---

### Post by jayon on 2015-04-18
I can ping from Ubuntu mobile IP from UBuntu !!

---

### Post by jayon on 2015-04-18
So u mean I cant use my laptop wifi hotspot?? I have to use  a wifi router....???

---

### Post by nerdtron on 2015-04-18
you don't have a wifi router? The wifi hotspot on the laptop creates a separate LAN IP block. Unless you can control that, you can't continue with your testing. 

If your phone is an android, I think it would be better to create a hotspot on the phone. Activate it's "Tethering" on the mobile settings. Then upon creating the hotspot, connect the laptop to that access point. And be sure that the Virtual box is setting on the VM is bridge mode on the wireless interface.

This way you can have all three devices on the same LAN IP block.

---

### Post by jayon on 2015-04-18
I can change my wifi hotspot IP address in network sharing configuration....YOu tell me wat shoud I change??
Cloud IP  is 192.168.56.101
to what mobile IP address (192.168.137.32) should I change??? you say?? :o

---

### Post by nerdtron on 2015-04-18
Try the changing the ip of hotspot.  It doesn't matter if you change the server or mobile IP, the end goal is to get them all on the same IP block and each one should be able to ping each other.

Like I said, mobile hotspot tether is worth a try.

---

### Post by jayon on 2015-04-18
yea mobile hotspot is a try. but I am going to use android applicaton thatt connects to cloud IP address for push messaging and other stuffs! So i need good speed internet connection !! Can you help with changing the IP address  of hotspot?? I donot know to what address I change?? :(

---

### Post by jayon on 2015-04-18
same IP block means?? can u give me example?? please

---

### Post by jayon on 2015-04-18
@NERDTRON!!
YOU  ARE AWESOME MAHN!!! YOU SERIOUSLY helped with me so many info....I really haappy!
I changed the virtualbox to bridged network with hotspot directly as u SAID...both connected to 192.168.137.156 address!!
GOD BLESS YOU.... !! THANKS ALOT!!! :)

---

### Post by nerdtron on 2015-04-18
Same IP bock all netmask 255.255.255.0
Cloud IP  is 192.168.56.101
PC IP: 192.168.56.135
Mobile PC: 192.168.56.140


I don't have any experience on hotspots in windows.

---

### Post by nerdtron on 2015-04-18
Glad you sorted it out.

---

### Post by jayon on 2015-04-18
THANKS MAHN.........!!! THANKSSS!!!! ITS done...now m gonna start with my application testing!
i can successfully access the cloud from my phone now :)

---

