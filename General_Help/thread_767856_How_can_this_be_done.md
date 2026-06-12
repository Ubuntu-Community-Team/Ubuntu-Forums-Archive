---
title: "How can this be done?"
date: 2008-04-25
forum: General Help
---

### Post by Chondro_Biak on 2008-04-25
I posted this on another forum, so please excuse the duplicate post... 

I am running a program through Wine and it has the capability of receiving data through Bluetooth... The program runs great but I don't know how to get bluetooth to work with a program ran through Wine...
The item I am trying to connect to is a thermostat, which is being used to heat an incubator. The manufacturer of the thermostat made a windows program that allows the thermostat to be connected to the computer so I can view my temps online or by phone...

My incubator is on the other side of the house on a different floor, so the manufacturer suggested I try their bluetooth setup... The thermostat is connecting to the computer (I can see the name) and the thermostat program installed and looks to be working great, except that it's not connected to the thermostat because I am not sure how to get the bluetooth connection to work when I am running the program with Wine...

Help would be greatly appreciated...

---

### Post by jakupl on 2008-04-26
well this might just help you... (probably not.. but check it out.) [http://ubuntu-utah.ubuntuforums.org/showthread.php?t=700657](http://ubuntu-utah.ubuntuforums.org/showthread.php?t=700657)

btw. you will get more helpful answers if your title reflects your problem... in this case, it could be something like "bluetooth in wine" or simular :) hope you get it sorted out.

---

### Post by Chondro_Biak on 2008-04-26
I looked that over and I am pretty sure that will not work for me... 

Thanks though

---

### Post by Whiffle on 2008-04-26
Hmm, this might be of help. [http://forum.eeeuser.com/viewtopic.php?id=23505](http://forum.eeeuser.com/viewtopic.php?id=23505)

What do you get when you run

cat /dev/rfcomm0   w/ the thermostat running

---

### Post by Chondro_Biak on 2008-04-26
When I run the windows program through wine it is searching for a connection... I think it says searching Comm 1...

I am at work at the moment, but with the thermostat plugged into the bluetooth and the usb bluetooth plugged in I can see the thermostat on my bluetooth manager... The problem is the software running in wine is not "looking" at the bluetooth manager... If I do this on a windows computer it picks it right up... (tested ata friends house, I don't use windows, period)

---

### Post by Whiffle on 2008-04-26
Ok I think what its doing is your bluetooth is just being wireless serial thing, so I think if you link /dev/rfcomm0 to ~/.wine/dosdevices/com1 , it might work...

ln -s /dev/rfcomm0 ~/.wine/dosdevices/com1

That is assuming that the bluetooth is actually putting data to /dev/rfcomm0

---

### Post by Chondro_Biak on 2008-04-26
If the program says it's searching for Comm 1, would the program automatically pick up that it's on comm 0?

This is my first time using Wine... 

The thermostat it shooting a wireless bluetooth signal of the temps to the USB receiver and the program is supposed to gather that data for display on the computer as well as on the net and phone... 

Does that make sense? I am going to try this when I get home unless you think what I just said changes something...

---

### Post by Whiffle on 2008-04-26
Well, in linux, each device is represented as a file.  Your video card has a "file", your soundcard does, etc.  When that   ln -s command is done, its linking one file to another.  When you link /dev/rcomm0 to ~/.wine/dosdevices/com0, you're linking what your windows program sees as com0 to rfcomm0, which is your bluetooth.    So yeah, I think it should work.  Just make sure that  rfcomm0 is the one that corresponds to your bluetooth.

---

### Post by Chondro_Biak on 2008-04-26
I am still learning the world of the terminal... lol

I understand everything you said and it sounds like a solid fix... 

Thank you very much... I really appreciate it... I am going on vacation to Norway (I live in US) for 20 days and need to monitor the temps while I am away... I was getting just a little nervous...

---

