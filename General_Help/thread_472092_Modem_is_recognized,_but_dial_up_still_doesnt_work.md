---
title: "Modem is recognized, but dial up still doesnt work"
date: 2007-06-12
forum: General Help
---

### Post by HgBoy on 2007-06-12
I have my modem recognized, and have setup all of my information in gnome ppp, but when I hit connect, it says it is dialing and does nothing else. What am I missing. The modem is an intel and runs off the ac 97 drivers (I have them properly installed). When I use the detect button in gnome ppp, it says the modem is located at /dev/ttys0. I have this option selected, but is it possible the modem isn't really located there? (I just converted my dad to Ubuntu(the comp is his) and now he is talking about switching back to MS after only a day without internet.) I am in desperate need of help, and the solution cant be anything web based, as my dad has no internet, and is 2 hours away from where I live.

---

### Post by Blayde on 2007-06-12
Which version are you using? I got my modem to work w/ 7.04 through the System > Administration > Network tool really easy, but I'm not sure if it was in the older versions. The biggest problem I had was getting the right phone number (I had to halfway install PeoplePC on a windows computer to get it) and forgetting to add @peoplepc.com to the user name.

Also, check the advanced permissions for his user account to make sure he has access to all the modem stuff.

Hope this helps!

---

### Post by HgBoy on 2007-06-12
I just tried setting it up using wvdial, and got this output after setting up the /etc/wvdial.conf file

Editing `/etc/wvdial.conf'.

Scanning your serial ports for a modem.

Modem Port Scan<*1>: S0   S1   S2   S3   
WvModem<*1>: Cannot get information for serial port.
ttySL0<*1>: ATQ0 V1 E1 -- OK
ttySL0<*1>: ATQ0 V1 E1 Z -- OK
ttySL0<*1>: ATQ0 V1 E1 S0=0 -- OK
ttySL0<*1>: ATQ0 V1 E1 S0=0 &C1 -- OK
ttySL0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 -- OK
ttySL0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
ttySL0<*1>: Modem Identifier: ATI -- SmartLink Soft Modem
ttySL0<*1>: Speed 4800: AT -- OK
ttySL0<*1>: Speed 9600: AT -- OK
ttySL0<*1>: Speed 19200: AT -- OK
ttySL0<*1>: Speed 38400: AT -- OK
ttySL0<*1>: Speed 57600: AT -- OK
ttySL0<*1>: Speed 115200: AT -- OK
ttySL0<*1>: Speed 230400: AT -- OK
ttySL0<*1>: Speed 460800: AT -- OK
ttySL0<*1>: Max speed is 460800; that should be safe.
ttySL0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK

Found a modem on /dev/ttySL0.
Modem configuration written to /etc/wvdial.conf.
ttySL0<Info>: Speed 460800; init "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0"

It almost acts like it is dialing, but then it hangs up immediately (it says there is no dial tone). All of the ISP settings are correct, the modem is located at the ttySL0 port, and the drivers seem to be installed properly. (The modem is a winmodem, but I read about several people using it successfully on Acer Laptops with the same packages I installed.)It may also have something to do with the fact that the driver for the modem is the same for the sound  on the laptop. I couldnt get the sound working either, until I installed the modem driver. Then everything magically popped up in the system. This has me about pulling my hair out, and I have tried **everything** in the DialUpHOWTO.

What next?

---

### Post by Blayde on 2007-06-13
I don't have much experience w/ winmodems and such so I don't think I'll be a very good help, but I found a couple mailing list archives that might help. I'm hoping you haven't tried them already!

[http://archives.linmodems.org/18927](http://archives.linmodems.org/18927)
[http://archives.linmodems.org/14155](http://archives.linmodems.org/14155)

The second is just a reply to the first, but there are a lot of configuration tips and stuff in it. All I did was search for ttySL0 on Google so there might be other things there that can help. Sorry I can't do more for you!

---

### Post by terabite on 2007-06-13
Have u tried using GnomePPP?? Its a great utility... Its in Add/Remove Programs..

---

### Post by HgBoy on 2007-06-13
I have tried gnome ppp as well. The only thing I can think of is that my modem might not actually be at the port listed, or it cant access this port for some reason. Any way I try to connect, it says "couldnt get information from serial port" and then "no dial tone" and hangs up. Is there any way to verify which port my modem is at? in the /dev folder I just see a bunch of tiles representing ports... Any way to check whats in these locations?

---

### Post by HgBoy on 2007-06-13
Ok. Suppose I have all of my settings set properly, I should in theory be able to connect to the internet. The only thing I have left to suspect is the outpput from sudo wvdial that says, "cannot get information from serial port". This leads me to believe that the modem is setup properly, but the path may not be correct. I know that on my particular system, the sound controller and modem controller are linked. Is it possible that my modem being autodetected could actually be the osund card and the modem is on another port? That could be why I can not for the life of me get a dial tone on a working phone line with the correct ISP settings. Anyone????:(

---

### Post by _duncan_ on 2007-06-15
Check if the following lines are in the wvdial.conf file:

```
Carrier Check = off
Stupid Mode = on
```

---

### Post by mbsnr on 2007-09-20
OK - I use a laptop with built in AC97 Modem. I added sl-modems package so that it was recognised as /dev/ttySL0 but I initially got 'No Carrier' error. I'm told this is a problem with the latest sl-modem package and Alsa drivers as the modem and sound card are on the same board.   After downgrading my sl-modem package to [etch]("http://packages.debian.org/sl-modem-daemon") the No Carrier error disappeared leaving me with a No Dial Tone error - same as you found.

The fix.... well unbelievable but true and credit goes to this [ link]("http://www.linuxquestions.org/questions/showthread.php?t=416577") really! Took a lot of googling....

Basically the modem sits on the same IRQ as the Alsamixer (audio board) and you need to run 'alsamixer' from a terminal window and set the 'phone' to unmute (I set it to approx 75) and the 'no dial tone' error disappeared.

Now I tend to get it sometimes but 75% of the time the modem dials straight away. This works using wvdial from terminal or using Gnome-ppp - just make sure you have 

carrier check = no 
INIT 3 = AT+MS=34
set in that wvdial.conf file.

---

