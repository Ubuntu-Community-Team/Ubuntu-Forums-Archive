---
title: "XWT-745VIA PCMCIA firewire card, Sony cameras PD170 and HC20E"
date: 2014-03-23
forum: General Help
---

### Post by Windoze Refugee on 2014-03-23
Hi Folks, 
Im trying to set up a camera on my kids laptop so they can have a go at animation.
The latop is an old Acer 5600. (2 x 1.6ghz 1g ram. running Ubuntu 12.04.2 LTS Kernel: Linux 3.2.0-37-generic-pae (i686)

The problem I'm having is that ubuntu wont recognise the pcmcia firewire card 

Any ideas?

Cheers
WR

---

### Post by Windoze Refugee on 2014-03-23
Further: 
This is a dual boot win xp machine and the card is recognised just fine under windoze. 
Puzzled...

---

### Post by mörgæs on 2014-03-24
Which PCMCIA card?

---

### Post by tgalati4 on 2014-03-24
tgalati4@Mint14-Extensa ~ $ apropos pcmcia
lspcmcia (8)         - display extended PCMCIA debugging information
pccardctl (8)        - PCMCIA card control utility

---

### Post by Windoze Refugee on 2014-03-24
> **mörgæs said:**
> Which PCMCIA card?

HI. 
Its a farily cheap unbranded mdoel XWT-745VIA
Cheers for your input

---

### Post by Windoze Refugee on 2014-03-24
> **tgalati4 said:**
> tgalati4@Mint14-Extensa ~ $ apropos pcmcia
lspcmcia (8)         - display extended PCMCIA debugging information
pccardctl (8)        - PCMCIA card control utility

Sorry - missed this before. How do I install and/or run these?
Cheers
WR

---

### Post by Windoze Refugee on 2014-03-24
Ahhh. OK so I ran lspcmcia and got the following:

0a:09.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller
0b:00.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev 46)

Texas is the on baord bus controller, and VIA is the firewire card.

Quite what I do wth the info now tho, I have no idea :)
Cheers
WR

---

### Post by Windoze Refugee on 2014-03-24
so..either the driver for the card is missing, or the video driver is. Either way I dont knwo how to acquire or install either :(
Little help?
Cheers
WR

---

### Post by tgalati4 on 2014-03-24
It appears that Ubuntu does recognize the firewire card.  Try plugging in a firewire disk drive (like a LaCie drive) and see if mounts and you can read the files.  The issue is probably that the camera is not recognized.

Open a terminal, plug in the camera and post any helpful information from:

```
dmesg | tail -40
```

You might share the model of the camera with us.  My guessing skills do not reach across the Pond.

---

### Post by Windoze Refugee on 2014-03-24
Hi.
Thanks again for your input.
I dont know if I have any other firewire kit, buI'll have a look around
I've been trying two different cameras, boht Sony. ONe is a PD170 the other is HC20E.
With the PD170 connected I ran the terminal code and got the following:

[  963.894024] firewire_core: rediscovered device fw1
[  963.894044] firewire_core: phy config: card 0, new root=ffc1, gap_count=5
[  963.894366] firewire_core: IRM is not 1394a compliant, making local node (ffc0) root.
[  963.894375] firewire_core: phy config: card 0, new root=ffc0, gap_count=5
[  966.103200] firewire_core: phy config: card 0, new root=ffc1, gap_count=5
[  966.174851] firewire_core: skipped bus generations, destroying all nodes
[  966.600100] firewire_core: giving up on config rom for node id ffc0
[  966.672186] firewire_core: rediscovered device fw0
[  966.672204] firewire_core: giving up on config rom for node id ffc0
[  966.988136] firewire_core: phy config: card 0, new root=ffc1, gap_count=5
[  967.524169] firewire_core: giving up on config rom for node id ffc0
[  968.176205] firewire_core: phy config: card 0, new root=ffc1, gap_count=5
[  968.755285] firewire_core: phy config: card 0, new root=ffc1, gap_count=5
[  969.156737] firewire_core: phy config: card 0, new root=ffc1, gap_count=5
[  969.252104] firewire_core: giving up on config rom for node id ffc0
[  969.527576] firewire_core: phy config: card 0, new root=ffc1, gap_count=5
[  969.592770] firewire_core: skipped bus generations, destroying all nodes
[  969.656093] firewire_core: giving up on config rom for node id ffc0
[  970.092150] firewire_core: rediscovered device fw0
[  970.092234] firewire_core: phy config: card 0, new root=ffc1, gap_count=5
[  970.408140] firewire_core: giving up on config rom for node id ffc0
[  970.604273] firewire_core: skipped bus generations, destroying all nodes
[  970.815867] firewire_core: skipped bus generations, destroying all nodes
[  971.104085] firewire_core: giving up on config rom for node id ffc1
[  971.104099] firewire_core: giving up on config rom for node id ffc0
[  971.312163] firewire_core: rediscovered device fw0
[  971.312198] firewire_core: phy config: card 0, new root=ffc1, gap_count=5
[  972.999798] firewire_core: phy config: card 0, new root=ffc1, gap_count=5
[  973.096099] firewire_core: giving up on config rom for node id ffc0
[  973.320196] firewire_core: giving up on config rom for node id ffc0
[  973.496086] firewire_core: giving up on config rom for node id ffc0
[  973.547282] firewire_core: phy config: card 0, new root=ffc1, gap_count=5
[  974.137688] firewire_core: rediscovered device fw1
[  974.266800] firewire_core: skipped bus generations, destroying all nodes
[  974.764220] firewire_core: rediscovered device fw0
[  974.764238] firewire_core: giving up on config rom for node id ffc0
[ 3096.321459] firewire_core: phy config: card 0, new root=ffc1, gap_count=5
[ 3096.820210] firewire_core: giving up on config rom for node id ffc0
[ 3201.784052] firewire_core: phy config: card 0, new root=ffc1, gap_count=5
[ 3202.371485] firewire_core: created device fw1: GUID 08004601043c9fe8, S100

---

### Post by Windoze Refugee on 2014-03-24
ok. If IM reading this right, the code just configured te card (right?) . If so, all I need to do now is configure the cam and/or dv capture driver ( i thin?
Cheers
WR

---

### Post by Windoze Refugee on 2014-03-24
OK. I've got the camera running in Kino! WooHoo.
Now, my next hurdle is to get it running with Stop Motion (or another animation package if not)
Stop Motion offers a DV capture setting, but it doesnt see the Sony cam. Hmmm
Any ideas how to get ubuntu to see the cam without running Kino?
Cheers
WR

---

### Post by Windoze Refugee on 2014-03-25
Anyone have any ideas how to initiate a dv cam so Stop Motion will recognise it?

---

