---
title: "How do I verify dial-up connection status?"
date: 2005-05-27
forum: General Help
---

### Post by rothbart on 2005-05-27
This is a general Linux question, not necessarily Ubuntu related (although one of the machines is Ubuntu).

This seems like a no-brainer, but I've set up a Linux router (Smoothwall Express 2.0) and it's set to "dial on demand" for connecting to the net via an external modem.  Since this is a dial-ip connection with a dynamic IP, I've written a script to safely "phone home" every <arbitrary time period> and send me its IP, but I only want the script to run if the dial-up connection is already connected.  In other words, I don't want the periodic script to trigger that the router should dial into my ISP.  

My goal is to be able to use the IP sent to me to be able to ssh into the machines via the dial-up link but I don't want it dialing *only* because I ran this script.  Hope that makes sense.  

I'm sure there's a way to tell from the SmoothWall Express machine (but I don't know how).  If someone out there also knows how to tell from another machine connected to it, that'd be great.

---

### Post by MrTom on 2005-05-27
Can you set up a dynamic DNS address? (no-ip.com or similar) You can configure smoothwall to update this everytime it changes IP address. 

The only disadvantage is that if the machine is switched off the IP address may be stale.

---

### Post by rothbart on 2005-05-31
[QUOTE=MrTom]Can you set up a dynamic DNS address? (no-ip.com or similar) You can configure smoothwall to update this everytime it changes IP address. 

The only disadvantage is that if the machine is switched off the IP address may be stale.[/QUOTE]

I could, but with other things I'd like to do as well, it'd be better if I knew a way to determine if I was connected to the internet or not without triggering it to dial up.

---

