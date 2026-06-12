---
title: "Is there a program to increase wifi signal strength?  (Ubuntu 14.04 with Xfce DE)"
date: 2014-09-15
forum: General Help
---

### Post by pretty_whistle on 2014-09-15
The title says it.

The problem:

Sometimes my wifi signal strength dips below 100%.  Sometimes as low as 97%.  When it does this my streaming videos run choppy. 

 I'd like to correct this if I can.

My modem is new so that's not an issue.

Is there a program I can install that would increase the srength?  Is that even possible?

---

### Post by tgalati4 on 2014-09-15
Use a wired ethernet cable.  Normally laptop wifi chips operate at maximum power:  20 to 33 dBm.  Most wireless routers operate at 100 dBm, some have a switch to go to 10 dBm and some can be boosted slightly with firmware or hardware modifications.

> tgalati4@Mint14-Extensa /var/log $ iwlist wlan0 txpower
wlan0     unknown transmit-power information.

          Current Tx-Power=20 dBm  	(100 mW)


Use an Android phone with WiFi Analyzer app to see if you have too many wifi networks in your area.

---

### Post by Bucky Ball on 2014-09-18
You need a wifi signal booster. It doesn't need to be any particular brand, just a signal booster/relay. No program I know of is going to boost the signal strength as the signal your machine is receiving is the signal it is receiving. Nothing software-wise is going to change that. You'd need to boost the signal with external hardware (get closer to your router/access point is cheap as a longer cable). A cable connection to the router, as previously suggested, is a sure fire way of stabilising the signal strength. 

Strange, though, as I'm never on a hundred percent signal strength, not even ninety, and never have an issue with choppy streaming videos or anything else wifi related ... :-k

---

### Post by HermanAB on 2014-09-18
Run 'top' and 'ntop' to see what is chewing system resources.  Try an external WiFi dongle and see if it works better than the onboard one.

---

### Post by grahammechanical on 2014-09-18
Signal strength is a function of the power amplifier in the transmitter and the power of WiFi transmitters is regulated by government legislation to prevent our hardware from causing interference with the WiFi devices of other users.

Any program to adjust the power output of a wireless transmitter can only work if the electronics in the wireless adapter had a function to allow the power output to be adjusted by computer software. I have never seen that ability in the set up program in my WiFi router.

And then you have to consider the laws of physics and thermal runaway. Increase the power out of the amplifier and we increase the amount of heat produced. Increase the heat and it becomes easier for electrons to move through the electronic circuit. That in turn increases the power output, which increases the heat produced, which increases the ease with which electrons move through the circuit, and so on until the electronic components melt.

[http://en.wikipedia.org/wiki/Thermal_runaway](http://en.wikipedia.org/wiki/Thermal_runaway)

A 97% signal strength is high signal strength. I would look for other reasons why video is choppy. The download data transfer rate of the telephone line from the ISP to the router. The data transfer rate between the router and the computer. The ability of the video adapter to play videos.  That sort of thing.

Regards.

---

### Post by pretty_whistle on 2014-09-18
Hmm....   Running on the ethernet cable resolved it for now but to solve the wifi it sounds like I'll need something in the hardware department to solve it.  Ok.  I'll have to go down that route then.

Thanks for your help everyone.  I'll mark this as solved.

---

