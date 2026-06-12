---
title: "How can I connect to internet ?"
date: 2008-06-23
forum: General Help
---

### Post by sowhat12345 on 2008-06-23
I had to format the pc because of a problem my pc had like every time . While formatting something drew my attention. After the formatting process, I wanted to run the drivers of modem. Before I started to run, the third light on the modem wasn't turned on. Then I run the modem and when I am on the desktop, it is always turned on. And when I am on the desktop of Ubuntu, that light is always turned on and I have just noticed it. In my opinion, that means the modem read the drivers automatically. So, what can I do to connect the Internet ?

---

### Post by cariboo on 2008-06-23
We are going to need way more information to be able to help you. What type of modem is it, what are your hardware specs? Does the modem work in Windows?

Jim

---

### Post by Uchiha_madara on 2008-06-23
If you are using eatherNet card Type This

> 
sudo pppoeconf

Then Type The User Name and the Password of the Provider
-Not that use it While Login to System-
Then Follow The Steps By Next & Switch if you need the Connection
start while booting or not

to turn Connection on
> 

sudo pon dsl-provider


to turn it off

> 
sudo poff dsl-provider


---

### Post by sowhat12345 on 2008-06-23
Uchiha_madara I don't have eatherNet card.(I didn't know if I have to install modem drivers.so I did everything I can do for install my modem driver but every time it gives me error about eatherNet car. I don't have eatherNet card). My modem works properly in windowsxp. My modem is Billion Bipac 7000 ADSL USB Modem.I use Ubuntu 8.04

---

### Post by Halfling Rogue on 2008-06-23
I've found that most of the time with Ubuntu you need to set a static IP address or use DHCP if you want the internet to work. Go into your Network Settings and look at the properties of your Wired Connection. Try turning off "Enable roaming mode" and switching the configuration to DHCP.

---

### Post by sowhat12345 on 2008-06-24
There isn't anything about your options you sad. I looked all the setting about connections...

---

