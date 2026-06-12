---
title: "Charge Creative Zen V"
date: 2007-07-11
forum: General Help
---

### Post by hylkedonker on 2007-07-11
Hello,
I've bought myself a Creative Zen V 4 gb. According to the manual I need to charge my mp3-player through USB(because the mp3 player doesn't come with an adapter for the mp3 player). 
When I plug in my mp3 player, it shows a loading screen, and then, for a few milliseconds, it shows a screen with a battery(I gues it's to indicate it's charging) and then it shuts down(it shows a black screen).
This is some output from dmesg:
> [ 9584.662196] usb 5-6: new high speed USB device using ehci_hcd and address 8
[ 9584.796283] usb 5-6: configuration #1 chosen from 1 choice
[ 9586.939572] usb 5-6: USB disconnect, address 8
Also, both Amarok(i've added a mtp device) and gnomad2 can't find my mp3-player, but I think that's because my battery is not yet charged.
Does anyone know how I can charge my battery?
Thanks in advance,
Hylke

---

### Post by moore.bryan on 2007-07-11
[I]i don't know if this will fix anything, but make sure the following is installed:
```
sudo aptitude install --with-recommends libnjb5 libnjb-dev libmtp5 libmtp-dev 
```and install the newest gnomad2 from [here]("http://downloads.sourceforge.net/gnomad2/gnomad2-2.8.13.tar.gz?modtime=1181348834&big_mirror=0"), then:
[/I][I]```

tar -xvzf gnomad2-2.8.13[/I][I]
cd gnomad2-2.8.13
./configure
make
sudo make install
```[/I][I]
the gnomad2 [website]("http://gnomad2.sourceforge.net/") expressly claims to support the zen v.  if you get any errors while compiling, just post and we can work through them.
[/I]

---

### Post by hylkedonker on 2007-07-11
I've already installed gnomad2 through synaptic. So I don't think it's neccesary to also compile one from source. And gnomad2 is (if i'm correct) only for sending files, and not for charging up an mp3-player.

---

### Post by moore.bryan on 2007-07-11
> **hylkedonker said:**
> I've already installed gnomad2 through synaptic. So I don't think it's neccesary to also compile one from source.
*that's what i'm saying... it may not be "new" enough.  some of the linux forums claim it doesn't work with "older" gnomad2's.*
> And gnomad2 is (if i'm correct) only for sending files, and not for charging up an mp3-player.
*gnomad2 will take control of mounting the player, which is what you sound as though you're having problems with...*

---

### Post by hylkedonker on 2007-07-11
I've partly charged up my mp3-player on Windows, and now both Amarok and gnomad2(still the one from synaptic) are able to find my mp3-player. And it looks like my mp3-player is also getting charged now(while i'm sending files to it in Amarok), because there's a lightning-strike layed on top of the battery-indicator.
So it looks like everything seems to be working perfectly now.
Anyway, thanks for your time.
Hylke

---

### Post by moore.bryan on 2007-07-11
*just glad to hear you got it working...*

---

### Post by Norst on 2007-07-18
Getting this error on complie

configure: error: *** id3tag.h C header is needed (missing -dev package?) ***\n*** You might have erroneously installed id3lib instead of libid3tag ****\nThis distinction is very delicate, so PLEASE pay attention! ***

----EDIT---

Blah I got it now:)

---

### Post by moore.bryan on 2007-07-18
*what are you compiling?*

---

