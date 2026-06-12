---
title: "Cable Internet with Dual Boot"
date: 2007-07-30
forum: General Help
---

### Post by shavenlunatic on 2007-07-30
Hi,

I am have my PC dual booting Ubuntu & WinXP SP2... I haven't booted into windows for quite a while (hence why I haven't bothered posting this question and the problem has existed for about 5 months! )

anyway... I used to have my cable modem hooked up to my PC via USB.. and dual booting between XP and ubuntu was fine.. worked instantly switching between the two OS without any issues.  A few months back I moved my PC but due to cable lengths, the USB cable wouldn't reach the PC so I set it up linking with an ethernet cable.

So, with this setup I am happily using Ubuntu, I decide I want to play a game so reboot into windows.. internet works fine and I get my jollies and reboot back to Ubuntu.... network connection showing as trying to obtain IP address, I wait a while and nothing.  I power down my PC, power down the cable modem, wait 30 seconds.. power up the modem.. power up the pc... still the same issue of obtaining IP.. usually after a few reboots it eventually works.

I once got around this by manually configuring the IP in ubuntu, but as my cable provider has a habit of changing my IP when I disconnect, it isn't really ideal and it was causing problems.

Any ideas (that don't cost money) or am I going to have to go back to USB and find some longer copper coax stuff for the cable modem?

---

### Post by gentine on 2007-07-30
Try and set your IP to static and configure it to work like you did before, static IP's won't change.

---

### Post by Metheos on 2007-07-30
It may be a limitation of your provider, I'm not sure.

What sort of modem is it? If it has routing ability built in (like many recent cable/DSL modems), then you could enable that, that way you wouldn't have to deal with requesting the IP from your provider, just from the modem itself.

Otherwise either request a static IP from your provider and assign it manually, or buy a router.. But those two options most likely aren't free.

---

### Post by shavenlunatic on 2007-07-30
> **gentine said:**
> Try and set your IP to static and configure it to work like you did before, static IP's won't change.

setting a modem to static IP won't force the ISP to provide me with the same IP when I reboot my cable modem.

hmm, looks like ill have to try find some longer coax and go back to the (not ideal) cable modem.. damn

I wouldn't have minded forking out for a router if I still had a network of pc's at home (as I used to) but now I only have my main pc so I feel reluctant to fork out for a networking tool when I have only 1 PC :)

/me begins hunt for cable

---

