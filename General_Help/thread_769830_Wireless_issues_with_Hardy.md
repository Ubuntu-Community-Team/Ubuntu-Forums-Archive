---
title: "Wireless issues with Hardy"
date: 2008-04-26
forum: General Help
---

### Post by hawk1278 on 2008-04-26
I have tried ndiswrapper and madwifi but I have yet to be successful in getting my laptops wireless card working properly.  The laptop is an HP nc6000 with an Atheros 5212/5213 chip set wireless card.  I am going to keep trying to figure out what the issue is but I have had no success.   

I don't know what it is but the card will see other wireless networks in the area but not mine even though the SSID is broadcasted and the router/AP is less than 10 feet away.

---

### Post by rgutierrez on 2008-04-26
Don't know that I'll be much help. But, some questions which may help others help you are:

Did you upgrade to Hardy? And, was your card working before? Or, was it a new install? I have an atheros chipset in my wireless nic, too. I don't think I had to use ndiswrapper. I could be wrong.

I am using nm-applet 0.6.6. I remember having lots of issues getting it to work in the previous version of Ubuntu (whichever it was - Gutsy or Fiesty). I think I had the same problem. I could see other networks, but not my own. And, once I installed nm-applet, I think I got it working right away. Again, it's been a while, but I think there are some steps you need to take (removing this, installing that, etc.).

What type of encryption are you using? WPA2 has been spotty in the past. But, I think it works fine, now.

---

### Post by hawk1278 on 2008-04-27
I was running Gutsy for awhile and did not have any wireless issues for a few months, then after an update about two weeks ago or so the wireless stopped working.   I worked on it for awhile and then just decided to try other linux distros that I had downloaded till Hardy came out.  I installed Hardy on Friday and have not had much luck getting the wireless to work properly.

My wireless network is using WEP with a 64 bit key.  128 bit is to much to type when I am entering the key to connect to the network :)

---

### Post by ghost_ryder35 on 2008-04-27
you could try manually entering your info into network manager or changing the channel that your ap is broadcasting on. 
p.s. and this is not intended to offend, but 64bit WEP = huge amounts of false security. could crack that on a 500mhz laptop in less than an hour (back track f.y.i.)

---

### Post by danwood76 on 2008-04-27
Can be cracked on a good laptop in under 3 minutes ;)

---

### Post by starcannon on 2008-05-06
Use WPA bare minimum if you can

---

