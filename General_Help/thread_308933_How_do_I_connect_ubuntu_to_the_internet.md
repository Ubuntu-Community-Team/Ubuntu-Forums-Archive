---
title: "How do I connect ubuntu to the internet"
date: 2006-11-28
forum: General Help
---

### Post by bcarm17 on 2006-11-28
I'm new to Linux and to put it short I know nothing. I need to know how to connect Ubuntu to the net through a dial-up modem(56k). I've tried everything I can think of.


HELP!!!!!!!!!!!!!!!](*,) ](*,) ](*,)

---

### Post by SendDerek on 2006-11-28
What's "everything"?  How are you trying to connect?  Wireless or wired?  What kind of computer do you have? And this might sound a little funny, but you wouldn't happen to have ISP service through Qwest would you?  For some reason I hear that's a hard one to connect to.

If you're trying to connect wirelessly, you might want to try network manager which can be found in the Synaptic Package Manager.  It worked for me.

If you're connecting with a wire, things should just work out of the box.  

If you're connecting via dial-up, I don't have the first clue.  Good luck!

---

### Post by sarc on 2006-11-28
If you have ADSL, connect to your ADSL modem with an Ethernet cable, go to Console and type:
pppoeconf

You will be asked for you username and password, then you will be connected!  Look up pppoeconf in this forum.

After the first time, to connect type in terminal: pon dsl-provider

Type poff to disconnect.


If you connect thru dial-up and have a Winmodem (most common type, internal software modem) you may need to buy an external modem.

---

