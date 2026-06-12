---
title: "G202 dongle assistance please!"
date: 2007-10-23
forum: General Help
---

### Post by Radiolad on 2007-10-23
Hiya, RADIOLAD here    :)
**Has anyone had any luck running a Zyxel G202 dongle** with Ubuntu    :confused:

I'm using a G202 with a ZYXEL 660HW receiver on my X86 P3 using **windows 98SE.**  I'm running Ubuntu 6.06 on an Imac G3 but todate have only managed to use it online with a SPEEDTOUCH 330 ADSL modem.
I have ordered an Ubuntu 7.10  disk and intend to run it on a spare ** X86 P3 **machine,  but again I would like to connect it to the internet with a G202.
Ideally I would also like to use the Imac with a G202 but so far have been 'mind-boggled' reading the information todate!

Can anyone advise me please?  I am a relative newbie when it comes to Ubuntu and 'command lines', so an **'idiot guide' **is about my level !

Cheers, Radiolad.

---

### Post by James_478 on 2007-10-29
Wait for your 7.10 the G-202 adapter just works :) I installed 7.10 and then halfway through it loading I thought, oh crap I am not gonna have net. It loaded and found all Wireless networks and connected straight away :D

---

### Post by Radiolad on 2007-10-30
> **James_478 said:**
> Wait for your 7.10 the G-202 adapter just works :) I installed 7.10 and then halfway through it loading I thought, oh crap I am not gonna have net. It loaded and found all Wireless networks and connected straight away :D

Hi, Radiolad back again  :)  I've just logged on and seen your reply  :popcorn:   Yippee!
So .... all I've got to do now is await the arrival of the 7.10 ...fantastic !
**For confirmation**:  When you say "...*halfway through it loaded* ..."  do you mean the 7.10 OS disk has the 'dongle-drivers' required within it,  or the ZYXEL G202 disk  which would normally have to be installed AFTER the OS had been installed ?  (N.B. I will be doing a FRESH install  of 7.10 on an 'empty'  HDD ) 
Cheers, Radiolad.

---

### Post by elggarc on 2007-11-03
Hello

I have G-202 USB dongle and it DID NOT work first time with Feisty or Gutsy.

I had quite the faf to get it working (recompile kernel etc).  I used instructions from here:

([Click Here]("http://yoten.blogspot.com/2007/07/zyxel-zyair-g-202-in-linux-step-by-step.html"))

I think the ProductID of the adapter has changed and was not listed in kernel 2.6.22 (the one Gutsy shipped with).  Perhaps because I've only recently bought my USB key?  Or maybe I'm wrong.

I'd be interested to know how you guys get on connecting to your network.  Esspecially if you have decent security (I'm about to start attempting to connect the G-202 to a WLAN with WPA2-PSK security).

C

---

### Post by Radiolad on 2007-11-23
> **elggarc said:**
> Hello

I have G-202 USB dongle and it DID NOT work first time with Feisty or Gutsy.

I had quite the faf to get it working (recompile kernel etc).  I used instructions from here:

([Click Here]("http://yoten.blogspot.com/2007/07/zyxel-zyair-g-202-in-linux-step-by-step.html"))

I think the ProductID of the adapter has changed and was not listed in kernel 2.6.22 (the one Gutsy shipped with).  Perhaps because I've only recently bought my USB key?  Or maybe I'm wrong.

I'd be interested to know how you guys get on connecting to your network.  Esspecially if you have decent security (I'm about to start attempting to connect the G-202 to a WLAN with WPA2-PSK security).

C

Hi, I've got the G202 up and running on Gutsy on my i386 PC but have had no luck so far with Dapper (using an iMac)

For i386/Gutsy I downloaded ndiswrapper plus its associated 'ndis... files' (common and util)   using SYNAPTIC..... and BINGO !!!  I had to put my security code in to gain access to my Zyxel 660 Router. I'm actually getting a better Wireless link strength (98% with Gutsy) than with my WindowsXP machine (approx 63%)  from the same position in the room !!

I'm having to run the iMac via a Wired Ethernet connection back to the Zyxel660 so I'll be glad if and when I get that sorted !

Cheers, Radiolad

---

