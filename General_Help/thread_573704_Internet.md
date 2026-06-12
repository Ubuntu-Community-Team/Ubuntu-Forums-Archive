---
title: "Internet"
date: 2007-10-11
forum: General Help
---

### Post by navneets on 2007-10-11
ok iv had ubuntu for ages just i havnt been using it because i dont know hwo to set up my wireless internet on it people said i have to type the IP in than hte password for it but it doesnt have a password for some reason lol. and i forgot how i  typed in the IP  can any one tell me how to set it up so i can sue the net on it?

---

### Post by Pumalite on 2007-10-11
[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuidep://www.linux.com/feature/56946](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuidep://www.linux.com/feature/56946)

---

### Post by navneets on 2007-10-11
yea i know how to set it up now but when i go to network my wireless card isnt htere..

---

### Post by navneets on 2007-10-11
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsByVersion](https://help.ubuntu.com/community/WifiDocs/WirelessCardsByVersion)  my card on there says  Unknown so that site doesnt really help me.

---

### Post by navneets on 2007-10-11
i did all the stuff on those sites and none of them helped me for what needs to be done i do the commands and nothing happends.

---

### Post by Sef on 2007-10-12
> i dont know hwo to set up my wireless internet

1. What type of card do you have?  

2. System specs?

---

### Post by navneets on 2007-10-12
my wireless card is - DWL-G520M Wireless 108G MIMO PCI

---

### Post by navneets on 2007-10-12
if any one replys on how i can do this i wont be able to read it for the next 2 days cause im going away but il post asap if it helps or nto

---

### Post by navneets on 2007-10-14
bump for help :-)

---

### Post by navneets on 2008-01-10
bump after a few months still havnt been able to do it............

---

### Post by zionpsyfer on 2008-01-10
I didn't see the DWL-G520M  listed on the [ Supported Wireless Cards List](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported).  You may try NDISwrapper, the G520M isn't on the supported cards, but the G520 is.  


Sorry for the bad news. :(

---

### Post by navneets on 2008-01-10
> **zionpsyfer said:**
> I didn't see the DWL-G520M  listed on the [ Supported Wireless Cards List](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported).  You may try NDISwrapper, the G520M isn't on the supported cards, but the G520 is.  


Sorry for the bad news. :(

dam are there any other types of linux that can work with my wireless card?

---

### Post by zionpsyfer on 2008-01-10
Probably not.  A quick query on google shows people in fedora, mandriva and suse have the same issues.  

If you look at the link below, you'll get an idea why supporting cards is so difficult without manufacturer support.  Pay attention to the Chipset column, it's a crapshoot on which chipset is in a particular model.  The 520 series has three different chipsets it could be.  All requiring a different driver.

[http://linux-wless.passys.nl/query_part.php?brandname=D-Link](http://linux-wless.passys.nl/query_part.php?brandname=D-Link)


I would give NDISwrapper a shot though as it might just work for you.  There are some great walkthroughs.  Here are two.

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)
[http://ubuntuforums.org/showthread.php?t=31926](http://ubuntuforums.org/showthread.php?t=31926)


It will look pretty intimidating if this is your first time doing something this involved with linux.  But if you've got some time, and don't mind trying it then I'd go for it.  I learned quite a bit the first time I played with NDISwrapper which helped with figuring out  other problems.

---

