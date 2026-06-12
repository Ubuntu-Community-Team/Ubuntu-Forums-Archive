---
title: "Verizon DSL Setup?"
date: 2006-11-18
forum: General Help
---

### Post by misterbeetz on 2006-11-18
Does anyone here know how to setup/activate Verizon DSL using only Ubuntu machines?  Verizon sent me a starter kit that apparently uses a Windows/Mac setup CD.  I'm not sure if it helps but I tried to run the setup.exe on the CD in Wine.  It didn't seem to do much aside from just opening a blank window.

Any help in this matter would be much appreciated.


- Misterbeetz

---

### Post by jimbren on 2006-11-18
There was a story on this posted to Digg a few days ago, but most of the comments seem to debunk the claim that you have to "activate" the service.  I would read through the comments and the article and judge for yourself...

jimbo

---

### Post by misterbeetz on 2006-11-26
To follow up on my situation:  

I have switched from Comcast Cable to Verizon DSL.  Everything seems to be running fine with no tweaking involved for my Ubuntu machines.  I'm using the modem/router combo that they provided which handles things like PPPoe on its own.  The only drawback is (like mentioned in the previous post) that the service needs to be activated using a provided installation CD that supports only mac/win machines.  The CD installer didn't run in WINE so I had to borrow my brother's Macbook to do the activation.  Thankfully I can pay less for internet now.

- misterbeetz

---

### Post by vtel57 on 2006-11-26
No activation necessary. Nor do you need any of the bloatware on that Verizon disk. Ubuntu should auto-detect your ethernet and LAN setup with no troubles.

---

### Post by misterbeetz on 2006-11-27
Interesting.  Thats good news for the Linux community then.  The verizon people made me feel like the only way to get the service working was through the their CD.  I'm glad they are wrong.

- misterbeetz

---

### Post by justin whitaker on 2006-11-27
> **misterbeetz said:**
> Interesting.  Thats good news for the Linux community then.  The verizon people made me feel like the only way to get the service working was through the their CD.  I'm glad they are wrong.

- misterbeetz

I use verizon dsl, and I do not activate. You can set up your account online, and after that, you are fine. 

Use pppoe, and you are good to go. If you run into any trouble, the DNS servers are posted in the Verizon Online help pages.

---

### Post by fragos on 2006-11-27
AT&T/SBC DSL required setup with a Windows machine.  Comcast is the same way but wine and IE6 allowed me to register before deleting that IE horror from my machine.  Believe it or not, both of these high technology networking carriers told me I had to buy Windows to use the Internet.  As a matter of note what you will be registering is the modem and not whats connected to it.  Once the modem is registered Linux and the likes of Firefox operate quite nicely.

---

### Post by jimbren on 2006-11-28
I've got ATT\SBC DSL, and when I got the modem kit in the mail (with the CD mentioned above) I tried to be a good little monkey and install it on one of the Windows machines in my house.  The installation hung, so I called their support and got everything going with one of their techs.

All the CD does is brand IE and install the yahoo toolbar and IM client.  There is absolutely no need to use the CD.

jimbo

---

### Post by zetaz7680 on 2006-11-28
Here is what I would recommend. Call the Verizon tech support and just complain that the CD provided is scratched. Then they will instruct you how to manually log into the router/modem and their online website to activate the account.

---

### Post by timcredible on 2006-11-28
you don't need windows to set this up with verizon, all you need to do is configure the dsl modem yourself (not hard).  open firefox, go to the dsl modem (192.168.1.1), login with username admin, password is password, then put in the correct vpi/vci (usually 35/0), contact verizon to make sure.  you have to then put in the username/password for your verizon account, which you have to ask verizon for.  don't let them give you crap, just tell them you need the info.  i've setup 4 of them (mine plus relatives), not a problem.

---

### Post by justin whitaker on 2006-11-28
> **fragos said:**
> Believe it or not, both of these high technology networking carriers told me I had to buy Windows to use the Internet.

I had that issue initally....when I asked if they were going to release me from the contract with no penalty because they mandated that I use an operating system that I was not willing to use, they changed their tune real fast. :mrgreen:

---

### Post by misterbeetz on 2006-11-28
> **fragos said:**
> Believe it or not, both of these high technology networking carriers told me I had to buy Windows to use the Internet.

Yeah, after I told the Verizon representative that I only have Linux at home, she told me that the installation would not be possible and that I should send the modem/installation kit back to them.  Total crap if you ask me.

-misterbeetz

---

