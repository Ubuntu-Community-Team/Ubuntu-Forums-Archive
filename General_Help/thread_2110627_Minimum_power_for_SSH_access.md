---
title: "Minimum power for SSH access"
date: 2013-01-30
forum: General Help
---

### Post by andypi on 2013-01-30
I'd like my home computer to function as a server that I can access from elsewhere when I'm not at home. I can set this up fine, but I don't really like the idea of leaving my computer on all the time.

What I'd really like to do is change what my sleep button does so that it sends my computer into an "almost suspend" mode. That is, it would turn off the screen, fans, and anything else that can be turned off or reduced such that the computer is doing next to nothing.

I would then be able to SSH into the machine, and if necessary restore it to full operating power, and then send it into "almost suspend" again when I'm done.

Unfortunately Wakeup On LAN is not an option because I'm using a wireless network to connect to the internet, and it would appear that my computer does not have the hardware for Wakeup On Wireless LAN.

Can I somehow set up a power profile that would fulfil this objective? If so, how do I do that and how would I achieve the lowest power consumption in that state, whilst still being accessible using SSH?

---

### Post by tgalati4 on 2013-01-30
I have seen, but not used server-room ethernet power switches.  They receive a signal from the WAN and power up a strip which then powers on a server.  They are not cheap.

Another method is to get a low-power rasperry pi or micro/nano ATX pc that runs at a few watts and connected to the WAN.  Ssh into that micro server, set up fail2ban or some other rate limiter to lock out if too many bad logins.  Change port 22 to some obscure port above 12K, then set your router to port forward another obscure port to your ssh-listen obscure port.  Remember to log into your machine with IP: obscure-port  Then from that machine issue a WoL magic packet to the high-power server.

You can experiment with acpitool to turn on and off parts of your server's bus to save power, but in the end, your server is either up and running or off/suspend.  There really is no low-power mode.  For instance my Dell PowerEdge servers run at 218 to 240 watts whether they are crunching or sitting idle.  They are at 10 watts in WoL mode.

---

### Post by andypi on 2013-01-31
Thanks. I seem to be finding that for more and more things I might wish to do, the answer is "Get a Raspberry Pi!". I already have one which I use as a media centre, but I guess I'll hold of getting another for now...

---

### Post by CaptainMark on 2013-01-31
You won't need a second raspberry pi, the same one can serve both these functions, mine does

---

### Post by andypi on 2013-01-31
Ah yes, except that it's in a different room, so I can't really wire it in.

---

### Post by rnerwein on 2013-01-31
> **CaptainMark said:**
> You won't need a second raspberry pi, the same one can serve both these functions, mine does
hi
oh another rasberry pi fan - you are wright.
i am in germany and in the "manual" is a wrong [www..]("http://www..")... address. i can get to rasperi with
[http://www.designspark.com/nodes/view/type:design-centre/slug:raspberry-pi#resources](http://www.designspark.com/nodes/view/type:design-centre/slug:raspberry-pi#resources)

have more fun with this toy.
cheers
  richi

---

