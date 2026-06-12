---
title: "How to sent Sms Msg"
date: 2014-02-15
forum: General Help
---

### Post by bnatgame on 2014-02-15
Hallo !!! Is there any way to send sms messages from Ubuntu/Kubuntu?
My PC is connected to the internet but doesn't have 3g modem.
My mobile 'phone is an HTC One using Vodafone on a contract.
I am located in the U[.]("http://www.bnatgame.com/game/12/flappy_bird_%D9%84%D8%B9%D8%A8%D8%A9_%D9%81%D9%84%D8%A7%D8%A8%D9%8A_%D8%A8%D9%8A%D8%B1%D8%AF.html")K.

---

### Post by Psil0cybin on 2014-02-15
There are plenty of applications you can use in order to access your phone via a GUI and send text messages, is this what you want?
I know with Samsung devices, they have something called Kies, that you can use in order to send and read text messages from your cellphone by accessing your phone like you would an internal web server 192.168.1.etc

---

### Post by fdrake on 2014-02-15
you can send an email to the provider with the phone number of the target number 
[http://janitha.com/archives/90](http://janitha.com/archives/90)

amil addresse differ from carriers.

---

### Post by nerdtron on 2014-02-15
This is how I send message using the computer with a gsm modem. Haven't tried about using a phone.
## Using a GSM modem to send text messages
## install gsm modules
sudo apt-get install usb-modeswitch gsm-utils

## watch syslog for the device information when plugged
tail -f /var/log/syslog

##sample device is ttyACM0
## send a text message syntax
sudo gsmsendsms -d /dev/ttyACM0 -b 19200 <phonenumber> "<Sample Message inside double quotes.>"

---

### Post by Bucky Ball on 2014-02-15
Skype. It's in the repositories.

---

### Post by lisati on 2014-02-15
I think bnatgame has [left the building]("http://ubuntuforums.org/showthread.php?t=2205768").

---

### Post by fdrake on 2014-02-16
> **lisati said:**
> I think bnatgame has [left the building]("http://ubuntuforums.org/showthread.php?t=2205768").

I can't access your link Lisati, seems you need some privileges..

---

### Post by Bucky Ball on 2014-02-16
Ya do. They've been spam banned, beans burnt, shan't be returning. ;)

I think I can safely say this thread has served its purpose and

*Thread closed.*

---

