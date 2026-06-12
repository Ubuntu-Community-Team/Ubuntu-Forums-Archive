---
title: "Bluetooth help! (A2DP)"
date: 2007-10-31
forum: General Help
---

### Post by illbashu on 2007-10-31
ok i am running ubintu 7.10 and i want to run an a2dp head phone with the built in softwere . ok, well the program can see the headphones and when i connect to it it tells me to type in the pass key, i typed it in and pressed ok and i got this error "Couldn't display "obex://[00:07:a4:f2:64:e6]" :confused: :( plz and thx!

---

### Post by illbashu on 2007-10-31
bump!!!!
 plz help!!!

---

### Post by zakeen on 2007-10-31
I get the same thing.......

---

### Post by illbashu on 2007-10-31
Bump! plz help!!!

---

### Post by illbashu on 2007-10-31
bump! HELP!!!!!!!!!

---

### Post by illbashu on 2007-10-31
Help!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!1

---

### Post by wieman01 on 2007-10-31
Look, mate. The more you bump, the less help you can expect. Understand that you want this solved, but generally speaking bumping puts people off, in particular when it comes at hourly intervals.

What Bluetooth dongle to you have? And what headphone?

---

### Post by illbashu on 2007-10-31
sry about the bumping... i have this adapter \/
[IMG]http://www.unikoo.com/ebay/photo/bluetooth/BT-004.jpg[/IMG]

and my headphones are the Motorola 820
[IMG]http://www.samstores.com/_images/products/Motorola%20HT-820.jpg[/IMG]

---

### Post by wieman01 on 2007-10-31
Billionton... generally no big issues with those. Now when you fire up Gnome's bluetooth utility and put the headphone in pairing mode, it would ask you for a pin, correct? Have you got the right pass key?

If nothing works, there is a nice little tool that you can install & use (heard it works great for a lot of people):

[http://www.stgraber.org/2007/05/20/gbtsco-already-release-02/]("http://www.stgraber.org/2007/05/20/gbtsco-already-release-02/")

---

### Post by illbashu on 2007-10-31
ya, the key is 0000... when i type it in and press ok i get this error "Couldn't display "obex://[00:07:a4:f2:64:e6]"

i tryed the program you told me and it doesn't work... :( it says "connecting" then the window closes and it doesn't connect.

---

### Post by wieman01 on 2007-11-01
> **illbashu said:**
> ya, the key is 0000... when i type it in and press ok i get this error "Couldn't display "obex://[00:07:a4:f2:64:e6]"

i tryed the program you told me and it doesn't work... :( it says "connecting" then the window closes and it doesn't connect.
Mmm... perhaps Ubuntu finds fault with the current USB dongle. Could you try another one? Perhaps you can borrow one from a friend of yours.

---

### Post by illbashu on 2007-11-01
it cant be the dongo because i used this one on windows and it worked... :/

---

### Post by wieman01 on 2007-11-01
> **illbashu said:**
> it cant be the dongo because i used this one on windows and it worked... :/
It could relate to it, because Ubuntu does not support all dongles... Therefore I am mentioning it. The fact that Windows recognized it does not mean anything (in fact Windows only recognizes it after installing a driver to be precise).

---

### Post by illbashu on 2007-11-01
can you tell me what drivers i have to install on ubuntu?

---

### Post by wieman01 on 2007-11-02
> **illbashu said:**
> can you tell me what drivers i have to install on ubuntu?
You don't have to install any, that's the point. Ubuntu either recognizes the dongle or it doesn't. At least that's my experience. Therefore I was asking you to try other ones as well, to see if they are supported.

---

### Post by illbashu on 2007-11-04
i tried with another bluetooth adapter and it gave me the same error "Couldn't display "obex://[00:07:a4:f2:64:e6]"." idk if i can find a pic becuse it just says "bluetooth" on it and has no compony name...

are you sure there isn't any drivers i need to install from synaptic package manage?

---

### Post by wieman01 on 2007-11-04
I am sure that I did not have to install any drivers in my case. And I have used 3 different dongles so far, all different brands & chipsets. Running out of ideas. 

Anybody else?

---

### Post by illbashu on 2007-11-04
bump! someone plz help!

---

### Post by illbashu on 2007-11-06
Come on! someone plz help!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!1

---

### Post by wieman01 on 2007-11-06
Ok, I really cannot do much but I found this:

[http://blueman.tuxfamily.org/]("http://blueman.tuxfamily.org/")

Some people said it helped them tackle their bluetooth issues. Before you do so, please run this from command line, restart the computer, and try to connect once again:
> sudo apt-get install gnome-vfs-obexftp

---

### Post by illbashu on 2007-11-06
i already have that installed :/

---

### Post by wieman01 on 2007-11-06
> **illbashu said:**
> i already have that installed :/
And have you also looked into the other tool that I have mentioned (previous post)?

Now I am really running out of ideas. The last thing you could check it bug reports on launchpad. I have seen some which might relate to your problem. If you can't find any simply file a bug report. People will help you there.

---

### Post by dvmrp on 2007-11-09
I also have issue in A2DP. The headset is paired and connected using the "Bluetooth Headset", the default mixer is set to "BT Headset". However, the sound is still going through the speaker. Any idea?

---

### Post by edwardTheGreat on 2007-11-09
These links have helped me with my Bluetooth Issues, but I haven't connected headphones so I can't comment on it too much.

Bluetooth setup:
[https://help.ubuntu.com/community/BluetoothSetup]("https://help.ubuntu.com/community/BluetoothSetup")

Bluetooth Audio Devices:
[https://help.ubuntu.com/community/BluetoothAudio]("https://help.ubuntu.com/community/BluetoothAudio")

HTH

---

