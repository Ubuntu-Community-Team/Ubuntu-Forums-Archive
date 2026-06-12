---
title: "Modem Configuration Problem"
date: 2007-12-17
forum: General Help
---

### Post by mafsi on 2007-12-17
I installed Ubuntu 7.10 with my modem imputed in slot. I can see it in Network but it says that is not connected.

i dont need modem to connect to the internet just for sending faxes. Why thenmy modem asks for username & password & Phone number & Prefix to enable connection. This is odd!

I imputed the phone cable into my modem. this is all i have to do on windows, load the file & send fax!

tell me how to enable the damn modem to send dome faxes! Thanks in advanced! ](*,)

---

### Post by phidia on 2007-12-17
A little more specs would be helpful but it sounds like this is an internal modem. Almost all internal modems are built to function with windows-they're controllerless modems using the OS  to function. Many of those modems can be made to work under linux. 

The 1st step in that is to identify your modem with a scam modem tool available [here]("http://www.linmodems.org/"). It is a pain that it's not more of an auto process and there are not as many modem/dial up users as there were also a lot of devs worked hard to get the winmodems we have functioning supported.

There are ways to send faxes using online resources but since I haven't done that I'll leave that for someone else to explain. Good luck.

---

### Post by mafsi on 2007-12-17
ok i followed instructions from there and worked out of the box

```

WvDial<*1>: WvDial: Internet dialer version 1.56
WvDial<*1>: Initializing modem.
WvDial<*1>: Sending: ATZ
WvDial Modem<*1>: ATZ
WvDial Modem<*1>: OK
WvDial<*1>: Modem initialized.
WvDial<*1>: Sending: ATDT1234567
WvDial<*1>: Waiting for carrier.
WvDial Modem<*1>: ATDT1234567
WvDial Modem<*1>: NO DIALTONE
WvDial<Err>: No dial tone.
WvDial<*1>: Disconnecting at Tue Dec 18 02:31:43 2007

```

now here is my 2C Q:

Since i dont connect to the internet via modem BUT since it asked for an user & a password i put
```
[Dialer Defaults]
Modem = /dev/536ep0
Baud = 115200
Init = ATZ
New PPPD = yes
Stupid Mode = 1
Auto Reconnect = off
#Carrier Check = no
Dial Attempts = 1

# MODIFY THE FOLLOWING 3 SECTIONS FOR YOUR CONNECTION
Phone = 1234567
Username = ExampleName
Password = ExamplePassword
```

Exactly as you see it in the link below  
[https://help.ubuntu.com/community/DialupModemHowto/Intel536EP](https://help.ubuntu.com/community/DialupModemHowto/Intel536EP)

I wonder if this will affect my fax sending since is just a dummy conf file.. what do you think?:neutral: 

BTW: 10x 4 your help

---

### Post by phidia on 2007-12-18
I honestly don't know. Can you send a test page and see what happens?
If you have a problem give the error messages and/or output.
If it works then your report on that will help others looking for a solution to this too.

---

