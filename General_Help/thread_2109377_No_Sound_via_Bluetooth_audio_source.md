---
title: "No Sound via Bluetooth audio source"
date: 2013-01-27
forum: General Help
---

### Post by c2tarun on 2013-01-27
Hi friends,

When I pair my android mobile phone with Xubuntu 12.04 then after selecting audio source when I play song from my cellphone I am not able to hear anything. Though I can see data activity in lower right corner of blueman bluetooth manager's window. 
When I installed blueman in Ubuntu 12.04 then this feature was working fine.
Can anyone please help me with this?

---

### Post by Merrattic on 2013-01-28
Blueman is not at all intuitive, you often have to help it.

Connect your phone

Click on the icon and open devices, you should see the phone.

Start playing some music on the phone

Right click on your phone in devices and select audio source. If successful you should hear music :)

If not, open up pavucontrol (install it if you haven't got it) and check your input/output settings.

Also have a look at alsamixer, just to check that everything is unmuted

---

### Post by c2tarun on 2013-01-28
> **Merrattic said:**
> Blueman is not at all intuitive, you often have to help it.

Connect your phone

Click on the icon and open devices, you should see the phone.

Start playing some music on the phone

Right click on your phone in devices and select audio source. If successful you should hear music :)

If not, open up pavucontrol (install it if you haven't got it) and check your input/output settings.

Also have a look at alsamixer, just to check that everything is unmuted

I tried all you suggested :( no music. I immediately disconnected my phone and played music via clementine and I am able to hear sound, so I guess nothing is mute.

Regarding pavucontrol, its just a volume controller kind of thing, do you really think that it can make a difference?

---

### Post by Merrattic on 2013-01-29
Pulse Audio is much more than a volume controller! (I sometimes wish it weren't ;))

In pavucontrol, is your phone/audio source there as a bluetooth input/output device? It should be. Also check in configuration as to which audio input(output) it is set to.

Again check alsamixer

---

### Post by jonathanfv on 2013-03-31
Hey there! I'm trying to do the same thing. I connected to my iPod's audio source, but nothing is played. I checked pavucontrol and alsamixer, and none of them showed my bluetooth source. I don't really need it, but I'd like to make it work if possible. I'm using Ubuntu Studio.

---

### Post by c2tarun on 2013-04-01
I switched to ubuntu 12.04 installed xfce4 in it and now blueman Bluetooth is working like charm :)

---

