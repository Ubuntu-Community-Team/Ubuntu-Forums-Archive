---
title: "internet wont work and resolution is stuck"
date: 2008-04-18
forum: General Help
---

### Post by mpc827 on 2008-04-18
ok so heres 2 questions which i dont think should be too hard to fix
but with my little knowledge of linux, im kind of stuck >.>

#1- internet
--Ok so we have high speed cable at my house. and that is hooked up to a dlink wireless router, i think its a router anyway, i dont know what else it would be called. but anyway, out of that dlink device, is my internet/ethernet cord. so i am pretty sure its considered a direct internet connection. it isnt networked with my other computer or anyone elses. but i go into the network connections thing and set it to automatic IP (dhcp?) and nothing ever works =/

#2- resolution
--In the resolutions box there is only one option, which is like 500x300 or some ridiculously small resolution like that, i cant remember exactly what it was. but how do i add more? i have a 25" screen, so its pretty big. not HD though. so you should reccomend what resolution to set it to while you help me set it up =p

so yeah any help guys?

---

### Post by zvacet on 2008-04-18
Does that screen have some kind of manual or can you find something about it on net? Type in terminal 

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by george9233 on 2008-04-18
Have you got the restricted driver (in system->administration->restricted drivers/hardware drivers) installed? If did the screen resolution should be automatically set to the highest resolution after reboot.

---

### Post by mpc827 on 2008-04-18
that stuff wont work >.<
it says i need to install sumthing.
but whatever, i'll just live with the big graphics for now.
i would really appreciate the net working >.<
so any help on that?
i have wired connection checked,
and its set to auto IP/dhcp
but wont work

---

### Post by zvacet on 2008-04-18
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

select **vesa **driver.

For connection go to the upper right on panel and cliock on network manager>manual configuration>select your modem (don´t check it ,just ckick on it)>properties<select your type of connection(you allready choose dhcp)>DNS tab<if you find any address there delete it and put your nameservers>connection tab<check your modem and window wil pop up with message changing interface configuration>when it is finish open terminal and type

```
pppoeconf
```

---

### Post by jingo811 on 2008-04-18
**Networking**
Not really knowledgeable regarding "ppoeconf" stuff but try this command in terminal.
```
sudo dhclient
```
If it doesn't work maybe you need to specify which eth(1-99) network interface card to do an update thingy. :)
```
sudo ifconfig
sudo dhclient eth(1-99)
```

**ENVY (Graphics setup for ATI and NVIDIA)**
After you have done the "vesa" trick in xorg like mentioned above.  Then this procedure is like candy for your graphic hardware.
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

