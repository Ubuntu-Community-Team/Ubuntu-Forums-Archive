---
title: "Use my old phone modem as a telephone?"
date: 2008-05-25
forum: General Help
---

### Post by ownaginatious on 2008-05-25
I have searched long and hard for this type of program on Windows, but I have been constantly bogged down in search engines by pages and pages of crap on VOiP products.

Well anyway, what I want to do is simply put my old PCI phone modem in my Ubuntu computer, and have some sort of software client allow me to use my existing microphone and speakers to pick up phone calls to my land line. I know that back in the day before Voice over IP this was possible, but now it seems impossible to find software that will do it the way I want...

If anyone knows something for linux/ubuntu that will do this, that would be awesome!

---

### Post by koenn on 2008-05-25
yeah, it's possible. I think it used to be used to create answering machines / automatic attendants, or to send out standard messages to people's phones, although the sound quality might not be optimal.

Whether this will actually work, depends on your modem first of all. It needs to be a voice modem (or a data/fax/voice modem). An ordinary data/fax modem can't create the wave forms/frequenties/... necessary for transmitting voice. 
google "voice modem" or [http://www.modemsite.com/56K/voice.asp](http://www.modemsite.com/56K/voice.asp)


Then, I think you have 2 options :
1/
dig into the old 1980-1990's modem tools (dialers such as minicom, serial port tools such as setserial, ...) to initiate a call, etc. If you got that working, you can at least use the modem's speaker, and plug a microphone in to it. Getting the thing to work with your pc's speaker or speakers and a mike plugged in to your sound card might prove to be a challenge. 

edit: external modems used to have a speaker and sometimes an outlet where you culd plug in a microphone. Don't know how common that is on PCI modems ...

2/
look into Asterisk. [http://en.wikipedia.org/wiki/Asterisk_PBX](http://en.wikipedia.org/wiki/Asterisk_PBX)
It's a linux based PBX (Telephone Exchange), or rather, a toolset to create PBX's on a linux OS. It supports VoIP, but can also be used as a traditional PBX and can interface with the phone network (aka POTS or PSTN), so I suppose some of that software can be used for dial-out telephone calls and accepting incoming calls. 

Here 's an artical about building an answering machine out of a PC, Linux, and (pieces of) Asterisk. That might get you started. 
[http://linuxgazette.net/120/smith.html](http://linuxgazette.net/120/smith.html)

---

