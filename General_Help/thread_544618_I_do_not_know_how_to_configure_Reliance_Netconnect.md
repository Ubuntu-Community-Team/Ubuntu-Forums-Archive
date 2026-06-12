---
title: "I do not know how to configure Reliance Netconnect USB modem and connect to internet"
date: 2007-09-06
forum: General Help
---

### Post by appunni on 2007-09-06
Sir,
         Today I installed Ubuntu 7.o4. I found it is very nice. But I saw that there is not Kppp for connecting to net. I took the terminal and wrote 'wvdialconf' . It replied that my USB modem ( it is Reliance Netconnect USB modem) is in /dev/ttyUSB0 and its speed and init string. As I did not see the kppp, I became confused about how to connect to net. I just typed 'wvdial' but it failed.
         Please help me with a step by step method to enble me to connect to internet with my Reliance USB modem. Please note that I am new in Linux. 
         Now I am posting this letter through windows. Please help to connect you back through Ubuntu 7.04.
          Thanks in Advance.
with regards,
appunni

---

### Post by dev3 on 2008-03-09
I haven't used Reliance netconnect myself, But I found this link, which could help u out

[http://www.techbangalore.com/having-reliance-netconnect-usb-card-to-work-on-linux/](http://www.techbangalore.com/having-reliance-netconnect-usb-card-to-work-on-linux/)

---

### Post by mailbinoy on 2008-03-29
just got my usb modem from reliance working. just google, lots of tutorials around.
the only hard part is to find out the device id and vendor id for your device. 
you might also want to install gnome-ppp if you are not comfortable editing wvdial.conf

---

### Post by snailbomb on 2008-05-10
Well here's the simple way ... out of common sense i tried it once I installed ubuntu or anyother Distro for that matter and it works on all.

Click SYSTEM > Administration > Network

On the network connection menu u get 

1. Wireless Connection
2. Wired Connection
3. Is what you want connection.

Click on the third and click " Properties "

Fill out the stuff on the General Tab. 
Connection type ( Serial Modem )
Phone Number : 777
Dial Prefix :#

Account Data :

    Username= Your Phone Number 
    Password= Your Phone Number
on Modem Tab.

Modem Port = "/dev/ttyUSB0 "
Dial type = Tones
Volume = off

On the third (Options )tab choose what you like. 

I chose all three options as mine is a unlimited reliance netconnect connection so the download limits don't really matter. and moreover I just like to get my system online whenever i switch in On.

So I just boot and I just open firefox. and start to use.

Now open firefox and type in what ever domain and check if the internet is working ... and if it's not working still now check for the information that you have filled I mean the number and password stuff.

And if still doens't work well open the System > Administration > Network again
and click on wired connection and click on properties for that selection and when the properties dialog open check the " **Roaming Mode Enabled** " Tab. and close and try again that should do it .

Guys I don't know why everyone goes for that wvdial.conf method but I have used this one right after basic ubuntu install. and this thing has worked for me before the gutsy gibbon times. 

Works on 

1. Fedora
2. Saboyan
3. Mandriva
4. Linux Mint
5. Ubuntu ( All )

---

