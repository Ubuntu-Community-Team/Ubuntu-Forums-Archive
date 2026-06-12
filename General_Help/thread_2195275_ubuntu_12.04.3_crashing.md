---
title: "ubuntu 12.04.3 crashing"
date: 2013-12-23
forum: General Help
---

### Post by iebo on 2013-12-23
hello 

so i have upgraded from ubuntu 10.04 to (precise) 

i thought everything will work smoothly but so far i noticed some  problems that force me to shutdown the system ... the desktop panels   keep crashing/freezing frequently sometimes my ubuntu screen blinks too . is this  graphic card fault or other compatibility issue after upgrade?

now i'm runing ubuntu using the old kernal of 10.04 since WLAN isnt  recognized at all on the latest kernal its say -unclaimed interface-  however this issue was present with diff kernals even before the major upgrade  

please notice : i have rt3090 wireless  network adapter and hp 620 laptop i think they are not fully supported on ubuntu

sometimes when crash happens i get report with following line :

/usr/lib/unity/unity-panel-service


i dislike the global menu (i'm not sure  what that mean but i guess i know ) also the non movable panels kills me  :sad: i want drag them to bottom

thank u

---

### Post by mörgæs on 2013-12-23
The rt3090 should not be difficult to deal with. How does 13.10 work in a live boot (not the wireless, but rest of the system)?

---

### Post by iebo on 2013-12-24
hi morgaes , unfortunately  i don&#8217;t have 13.10 live cd ... 12.04.3 was available via  LTS upgrade using internet connection  

tnx.. i need someone to help me to fix this :

1. video card problem (i suspect )
2.no reliable internet connection - if tried installing  the rt3090 dkms module from ppa i might stay with no connection  
3.desktop crashing ...  
4.sound doesn&#8217;t work sometimes after reboot or just only function from headphones  (this on old kernal  2.6.32-28)

i haven&#8217;t had troubles using ubuntu for years with acer laptop but not anymore since moved to this stupid hp

---

### Post by mörgæs on 2013-12-24
A live boot works best from USB. 

There are lots of people here ready to help, but as I mentioned first we would like to hear how it works in a live boot. Your present system sounds like an upgrade going haywire.

---

### Post by iebo on 2013-12-24
hello again 
 
i don&#8217;t have usb storage  neither i can use cd r/w atm, is broken  :(
 
help...

---

### Post by iebo on 2013-12-25
i kinda solved the network problem i hope it will last . i did  white-list this  module rt2800pci

---

### Post by iebo on 2013-12-25
any assistance about disabling  -global menu/bar and moving applications bar to bottom ?

---

