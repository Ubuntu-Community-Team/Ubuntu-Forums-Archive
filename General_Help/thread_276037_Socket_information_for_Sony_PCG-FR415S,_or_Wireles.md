---
title: "Socket information for Sony PCG-FR415S, or Wireless info"
date: 2006-10-12
forum: General Help
---

### Post by Coffee_Time on 2006-10-12
Hi new to the forum and ubuntu,

I have been looking around the forum and can not find how to solve this problem.  When the card (linksys WPC54GV5) is slotted into the PCMCIA socket  it is showing no power to it (1 green lights), I have so far installed ndiswrapper, PCMCIA-cs, looked at the installation of the card driver and none have yet to solve the problem.

I have tried cardctl info which shows this when the card is not installed
~$ cardctl info
PRODID_1=""
PRODID_2=""
PRODID_3=""
PRODID_4=""
MANFID=0000,0000
FUNCID=255
PRODID_1=""
PRODID_2=""
PRODID_3=""
PRODID_4=""
MANFID=0000,0000

and this when it is 

PRODID_1=""
PRODID_2=""
PRODID_3=""
PRODID_4=""
MANFID=0000,0000
FUNCID=255
PRODID_1="Marvell Semiconductor"
PRODID_2="88W8310 802.11g Cardbus PC Card"
PRODID_3="83"
PRODID_4="01"
MANFID=02df,8310
FUNCID=6

When looking through the pcmcia text it state that I need to know the socket number, is this correct or I am going down the wrong path?

Can anyone please help get my wireless to work ](*,)

---

### Post by l.tambiah on 2006-10-18
I found this at a blog, it may be the driver you are using.

Card: Linksys #[WPC54G v5], 54mbps — [link here|List#WPC54G v5]
      · Chipset: Marvell 88w8335
      · pciid: 11ab:1faa
      · Driver: [http://www.linksys.com/servlet/Satellite?blobcol=urldata&blobheadername1=Content-Type&blobheadername2=Content-Disposition&blobheadervalue1=application%2Fzip&blobheadervalue2=inline%3B+filename%3DWPC54Gv5.zip&blobkey=id&blobtable=MungoBlobs&blobwhere=1130950145165&ssbinary=true](http://www.linksys.com/servlet/Satellite?blobcol=urldata&blobheadername1=Content-Type&blobheadername2=Content-Disposition&blobheadervalue1=application%2Fzip&blobheadervalue2=inline%3B+filename%3DWPC54Gv5.zip&blobkey=id&blobtable=MungoBlobs&blobwhere=1130950145165&ssbinary=true)
      · Other: The ridiculous URL above appears to be the only way to get at the official driver, since there’s nothing obvious at the Linksys ftp site. Unpack WPC54Gv5.zip, then ndiswrapper -i LSMVNDS.inf. I used FC3, kernel 2.6.12-1.1381_FC3 unmodified (despite the 4K page warning). There’s an UNIMPLEMENTED warning which looks serious, but from the mailing list archive can apparently be ignored. AP is Linksys WAG354G.
      · Other: The above driver did not work for me, but this other driver (for a card with the same pciid) did: [http://www.airnetusa.com/downloads/driver/DRXP_AWD_AWN154_v11.zip](http://www.airnetusa.com/downloads/driver/DRXP_AWD_AWN154_v11.zip) 

Website:- [http://gabston-howell.org/wl/2006/06/12/wireless-woes-reloaded/](http://gabston-howell.org/wl/2006/06/12/wireless-woes-reloaded/)

Your card may come to life using the driver from above. Give it a try, if it dont work then yes it could be related to the PCMCIA slot not detecting the card.

---

