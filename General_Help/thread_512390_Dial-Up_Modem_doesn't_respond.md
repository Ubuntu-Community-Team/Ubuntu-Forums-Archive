---
title: "Dial-Up Modem doesn't respond"
date: 2007-07-29
forum: General Help
---

### Post by Minki on 2007-07-29
Hi, everyone!

I'm lost when it comes to installing my dial-up modem onto my desktop, which I recently installed Ubuntu 7.04 on. My modem's a Netcomm Smartmodem56. What happens is I turn it on and then I run scanmodem.gz file to scan the modem but then when I read the modem file I'm supposed to send to them, it says the modem didn't respond. Please someone help me! I'm lost!

---

### Post by dragonwings on 2007-07-29
if you are using a full hardware external modem
go to "system" on your desktop
then addministration
then network

put your dailup number in phone number area
put your dailup user name and password in

now set up modem if you have a serial conection use "/dev/ttyso from drop box 
or if your using a usb conection change /dev/ttyso   to /dev/ttyUSB0     (note manualy change it  point click and edit it)
set dail type to tones

tick all boxs in options tab

once all done click save tick box at top left 

now when you turn on your pc it will dail up straight away

if your using a pci modem it will be an uphill battle best to get  full hardware external modem 
as i did .they're cheap as chips

im using a dynalink v1456vqe          serial conection )  a bit old school v90

i set up a dlink dfm-562e                  serial conection  ) on my mates macbook  which is a v92

no serial port no worries just get a serial to usb adapter cord and use the  /dev/ttyUSB0  as i said above


need more help email me      [email]x794z2000@yahoo.com.au[/email]

---

### Post by astralsin on 2007-07-29
that's a winmodem, it may not work at all.  your best bet would be to check out [http://www.linmodems.org/](http://www.linmodems.org/) to see if there is a driver available for it.  i agree with dragonwings, your best solution would be to pick up an external modem.  you can get usb ones very cheap and most if not all of them work in linux

---

### Post by Minki on 2007-07-29
> **astralsin said:**
> that's a winmodem, it may not work at all.  your best bet would be to check out [http://www.linmodems.org/](http://www.linmodems.org/) to see if there is a driver available for it.  i agree with dragonwings, your best solution would be to pick up an external modem.  you can get usb ones very cheap and most if not all of them work in linux

I've gone on linmodems but I don't remember seeing a netcomm driver there. :neutral: I'm pretty sure I'm using a serial connection. By the way, I am using an external modem, but I better make sure I've done everything right. Thanks, guys! :)

---

### Post by Bartender on 2007-07-30
You're using a Netcomm SmartModem?  The SM 5695 shown on this [page]("http://www.netcomm.com.au/Modems/external.php")?  The one going for $495?

Wow

I downloaded the .pdf specifications.  On the one hand, it kinda sounds like a full hardware modem, but under "Minimum System Recommended" it says "Windows 95, 98, 2000, or Me".  That's not a good sign, but it's not the mark of death either.  Sometimes they just don't bother to mention Linux.
I'd contact the company and ask them.

Try the wvdial and/or ppp-config steps listed [here]("http://ubuntuforums.org/showthread.php?t=480717") to see if your PC can detect and talk to the modem.

---

### Post by acesabe on 2007-07-30
If you can find a Conexant modem somewhere - there are millions of them around - Dell ahs released the driver for it (used to be a charge for the full speed driver or 14kb/s limit for the free one)

[Click here to get the driver as a .deb file]("http://support.dell.com/support/downloads/download.aspx?c=us&l=en&s=gen&releaseid=R155004&SystemID=INSPIRONI6400/E1505&servicetag=&os=UBLN&osl=en&deviceid=8593&devlib=0&typecnt=0&vercnt=1&catid=-1&impid=-1&formatcnt=1&libid=20&fileid=206745")

---

### Post by Bartender on 2007-07-30
acesabe -
Can you tell us any more about those Dell drivers?  Do they appear to work for any Conexant-based winmodem?  And at full-speed, not the the crippled 14.4K?
Another question - I keep hearing that the Conexant drivers have to be re-installed every time you upgrade the kernel.  I assume the same holds true for the Dell drivers?

---

### Post by Minki on 2007-07-30
> **dragonwings said:**
> if you are using a full hardware external modem
go to "system" on your desktop
then addministration
then network

put your dailup number in phone number area
put your dailup user name and password in

now set up modem if you have a serial conection use "/dev/ttyso from drop box 
or if your using a usb conection change /dev/ttyso   to /dev/ttyUSB0     (note manualy change it  point click and edit it)
set dail type to tones

tick all boxs in options tab

once all done click save tick box at top left 

now when you turn on your pc it will dail up straight away

if your using a pci modem it will be an uphill battle best to get  full hardware external modem 
as i did .they're cheap as chips

im using a dynalink v1456vqe          serial conection )  a bit old school v90

i set up a dlink dfm-562e                  serial conection  ) on my mates macbook  which is a v92

no serial port no worries just get a serial to usb adapter cord and use the  /dev/ttyUSB0  as i said above


need more help email me      [email]x794z2000@yahoo.com.au[/email]

It worked!!! :D Thankyou sooo much, Dragonwings! I was soo scared I'd have to go back to windows XP! You're a legend. And as for everyone else, thanks so much for the advice!!!! It's much appreciated! :KS

---

### Post by Bartender on 2007-07-30
Well, someone please xplain to me what's happening.  Everyone's been saying that the dial-up section of Networking doesn't work in Edgy and Feisty.  It didn't work for me.  But it just did for the OP?

---

### Post by Minki on 2007-08-12
[COLOR="DarkGreen"]> **Bartender said:**
> Well, someone please xplain to me what's happening.  Everyone's been saying that the dial-up section of Networking doesn't work in Edgy and Feisty.  It didn't work for me.  But it just did for the OP?

I used to have fiesty and dialup worked just fine on it.[/COLOR]

[COLOR="DarkSlateBlue"]However, I'm now using hoary and I'm getting some troubles with it. It keeps disconnecting. I'll dial up to the net, right? Then I might web browse for a bit, but I'll only be able to do that for maybe a few minutes cuz it keeps cutting off! :mad: It's very annoying. Can someone help me out here? :)[/COLOR]

---

### Post by Slingshot on 2007-08-12
> **Bartender said:**
> acesabe -
Can you tell us any more about those Dell drivers?  Do they appear to work for any Conexant-based winmodem?  And at full-speed, not the the crippled 14.4K?
Another question - I keep hearing that the Conexant drivers have to be re-installed every time you upgrade the kernel.  I assume the same holds true for the Dell drivers?

FYI The driver is located here - [http://support.dell.com/support/downloads/download.aspx?c=us&l=en&s=gen&releaseid=R155004&SystemID=INSPIRONI6400/E1505&servicetag=&os=UBLN&osl=en&deviceid=8593&devlib=0&typecnt=0&vercnt=1&catid=-1&impid=-1&formatcnt=1&libid=20&fileid=206745]("http://support.dell.com/support/downloads/download.aspx?c=us&l=en&s=gen&releaseid=R155004&SystemID=INSPIRONI6400/E1505&servicetag=&os=UBLN&osl=en&deviceid=8593&devlib=0&typecnt=0&vercnt=1&catid=-1&impid=-1&formatcnt=1&libid=20&fileid=206745")

Its the Linuxant driver that for free was crippled to 14.4k (or you could buy the un-restricted drive). Worked for my Dell M1210 internal modem on 7.04 that is D110 based, however I am not sure about other Conexant modem. I believe its x86 32bit only.

PS I recommend using gnome-ppp for those stuck in dialup land. I personally find its interface to wvdial simpler and more options then the default gnome interface.

---

