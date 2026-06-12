---
title: "switching cell phone SIM chips."
date: 2008-04-13
forum: General Help
---

### Post by Ptero-4 on 2008-04-13
Hi. I just got tasked to extract the photos out of a samsung sgh-e356 cell phone, for this I was given the phone and a usb data cable that was supposed to work with it, but so far I haven't been able to get it working neither in my linux box nor in my family windoze box (even with the drivers for the sgh-e356 it just can't recognize the "COM port" emulated by the data cable and was wondering. If I switch the SIM chip to my mom's cell phone (which works on the family's computer) Do the photos stored in the phone (I assume they get stored in the SIM chip) move over safelly?

---

### Post by essexboyracer on 2008-04-13
Sounds like you tried ti in Windows with the correct driver and it didnt work. Maybe it s the cable?

---

### Post by ShodanjoDM on 2008-04-13
Photos, Musics, Movies etc are usually stored in the phone's internal memory (or memory cards for the newer phones) and not in the SIM card.

Does the phone has a "file transfer" mode or something similar? If it is and if you choose that mode, I think it will be recognized as a storage medium.

---

### Post by Kevbert on 2008-04-13
The Sim normally only saves network settings and phone numbers, some sms etc.  Sims normally come in 32Kb and 64Kb flavours.  The phone memory (8Mb shared) will store pictures, videos etc.
One question, is the phone locked to a network other than that of the Sim card that your putting in the phone?  It may be that as the phone is locked to a network it has not booted up, check if the network is displayed.  Drivers can be found here [http://www.nodevice.com/driver/SGH-E356/get40392.html]("http://www.nodevice.com/driver/SGH-E356/get40392.html") 
When you connect the phone to the PC in Windows, does the PC recognise that a phone/modem has been connected ?  If not it may be that the comms port on the phone is not enabled (by the manufacturer) or the data cable is wrong/suspect.   You could also try using Hyperterminal in Windows when connecting the phone.   Set the port settings to COM1, 9600 8 data bits, no parity, 1 stop bit. Enter  at  and the phone should reply 'OK' (assuming the phone is on COM1).
Best of luck.

---

### Post by Ptero-4 on 2008-04-13
I haven't changed to SIM (they will do after I transfer the pics). As for windoze, the samsung PC Link app detects a com3 port (it maybe the softmodem) and in windoze's hardware manager (windoze's lspci) there's "Samsung data cable" listed.

---

### Post by Kevbert on 2008-04-14
Looks like the cable is fine.  Can you see the phone in Windows Explorer ?  If so, you can use it as if it is a disk drive.

---

