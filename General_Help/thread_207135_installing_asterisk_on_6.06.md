---
title: "installing asterisk on 6.06"
date: 2006-07-01
forum: General Help
---

### Post by sickdude on 2006-07-01
I was browsing the net in search for a how to, but with no luck.

i found some stuff via apt-cache search but i dont have an idea wich of the packkages i need to install.

root@mixmaster:~# apt-cache search asterisk          
asterisk - Open Source Private Branch Exchange (PBX) - dummy package
asterisk-app-dtmftotext - Text entry application for Asterisk
asterisk-app-fax - Softfax application for Asterisk
asterisk-app-misdn-v110 - V.110 protocol handler for Asterisk
asterisk-bristuff - Open Source Private Branch Exchange (PBX) - BRIstuff-enabled version
asterisk-chan-capi - Common ISDN API 2.0 implementation for Asterisk
asterisk-chan-misdn - mISDN support for Asterisk
asterisk-classic - Open Source Private Branch Exchange (PBX) - original Digium version
asterisk-config - config files for asterisk
asterisk-dev - development files for asterisk
asterisk-doc - documentation for asterisk
asterisk-h323 - asterisk H.323 VoIP channel
asterisk-oh323 - oh323 channel driver for Asterisk
asterisk-prompt-de - German prompts for the Asterisk PBX
asterisk-prompt-fr - French voice prompts for Asterisk
asterisk-prompt-it - Italian voice prompts for the Asterisk PBX
asterisk-prompt-se - Swedish voice prompts for Asterisk
asterisk-rate-engine - Asterisk least cost routing module
asterisk-sounds-extra - Additional sound files for the Asterisk PBX
asterisk-sounds-main - sound files for asterisk
asterisk-web-vmail - Web-based (CGI) voice mail interface for Asterisk
destar - management interface for the Asterisk PBX
gastman - GUI tool for Asterisk administration and monitoring
libiax-dev - An implementation of the Inter-Asterisk eXchange protocol (devel)
libiax0 - An implementation of the Inter-Asterisk eXchange protocol

for example why is the first package a dummy?

well i hope that someone with experience installing asterisk can give some nice tips :)

thnx in advance =D>

---

### Post by rbalfour on 2006-07-01
This package won't work if you have Digium cards installed, This package dosen't include the zaptel drivers.

If you require help compiling asterisk, just pm me.

---

### Post by sickdude on 2006-07-01
just sent a pm :)

---

### Post by najeer on 2006-07-24
Whaddup rbalfour,

I noticed your message about installing asterisk with a digium card.  I am using TDM400P and just about ready to finalize my 10 installation.  I had a problem using OnDo Sip Server and getting port 5060 open to listen.  Have you worked with a proxy sip server residing on dapper?

Regards,

najeer

---

