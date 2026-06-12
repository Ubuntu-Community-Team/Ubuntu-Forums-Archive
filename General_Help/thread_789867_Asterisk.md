---
title: "Asterisk"
date: 2008-05-10
forum: General Help
---

### Post by juan_valdez on 2008-05-10
I need to spoof my caller id number, and i hear you can do this with asterisk. if you know how to do this without asterisk, please let me know.

Otherwise, im having problems isntalling asterisk on 8.04, ive tried various guides and havnt found one that works yet. some of the guides said you need a server version of ubuntu, which i know absolutley nothing about.. but other guides say you dont need it.. 
when i get asterisk from synaptic nothing shows up under applications, and when i run asterisk in terminal i get an error with somthing about a .pid in the wrong directory. 

so i guess all i need to know is EXACTLY how to install and use asterisk for said purpose, unless theres an easier alternative...

---

### Post by Monicker on 2008-05-10
Dunno if you are in the US or not, but in the United States it is illegal to spoof your caller id to a number which you do not own.  The penalties for it are rather substantial.  Also its not quite as easy as you think.  You can't always override what the carrier has specified for a particular telephony circuit.

Just an FYI from someone who used to work in a call center.

Asterisk is a command line application.  For it to work properly it needs to be configured for your specific telephony hardware.  Are you using an analog line card? A digital line card? Are you doing a sip or iax connection to another voip provider?  It gets rather complicated quickly.

If you are serious about learning asterisk, this free book is good:

[http://www.asteriskdocs.org/]("http://www.asteriskdocs.org/")

Along with much of the information here:

[http://www.voip-info.org/wiki/view/Asterisk]("http://www.voip-info.org/wiki/view/Asterisk")

---

