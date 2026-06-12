---
title: "Audio USB Philips Mini System wont work under Ubuntu"
date: 2007-01-13
forum: General Help
---

### Post by Ubempi on 2007-01-13
Look, I have this (-> [this]("http://www.p4c.philips.com/cgi-bin/dcbint/cpindex.pl?sct=MINI_SYSTEMS_SU&cat=AUDIO_SYSTEMS_CA&grp=HOME_ENTERTAINMENT_GR&session=20070112234132_200.71.227.117&ctn=FWM779/21&slg=AEN&scy=PA") <-) fmM779 Mini Hi-Fi System from Philips and it is connected to the PC by USB.

On Windows it works fine, I can hear all the sounds (from Windows, from Winamp... etc.)

On Ubuntu it just don't work.

If I do start Ubuntu with the Mini System powered on then Ubuntu tells in the "Audio Preferences" this:

Default sound cards: (a drop down list)
	- VIA 8237.............................................(<- Don't work)
	- SBLive! Platinum [CT4760P]..........(<- Works, my sound card, not the Mini System)
	- Philips Audio Set..............................(<- Don't work, this one appears in Windows too)

If it detects the Philips Audio Set why wont play?

I just am lost here.

---

### Post by HAMANN on 2007-01-18
up
I have philips fm m777 and i wanna install ubuntu, but if i cant make it working, its not possible to have such OS ](*,) :(

---

### Post by rmt on 2007-03-04
I have the same issue, Ubuntu seams to recognize the device however it doesn't play anything.
I'm posting this just to see if you have resolved the issue already.
Thanks

---

### Post by Abala on 2007-10-24
up !

i'm the same problem

---

### Post by rdownie on 2007-10-24
I can't get it to work either. If someone gets this to work, please post.
Thanks.

---

### Post by phibit on 2008-05-09
Same problem for me on Ubuntu Hardy with a Philips M779 Audio System. On windows it requires extra software (Sound Agent 2) or something...

---

### Post by slipky on 2008-05-30
same here with my philips fw M779 =/

```

yuri@yuri-desktop:~$ cat /proc/asound/cards
 0 [V8235          ]: VIA8233 - VIA 8235
                      VIA 8235 with AD1980 at 0xe000, irq 21
 1 [Bt878          ]: Bt87x - Brooktree Bt878
                      Brooktree Bt878 at 0xe6800000, irq 20
 2 [SA             ]: USB-Audio - Philips USB SA
                      Philips Philips USB SA at usb-0000:00:10.0-1, full speed
yuri@yuri-desktop:~$ lsusb
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 013: ID 0471:0111 Philips 
Bus 001 Device 001: ID 0000:0000  

```

---

