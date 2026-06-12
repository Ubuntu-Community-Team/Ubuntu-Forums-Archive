---
title: "MP3 Player not working in Feisty Fawn"
date: 2007-02-19
forum: General Help
---

### Post by vishnu on 2007-02-19
I have a 256MB Diamond MP3 player.  Popped up as removable media in Dapper and Edgy but no luck with Feisty.  RhythmBox would always load up when I plugged it in but nothing happens on Feisty.  Am I missing something like editing a config file for USB devices?
Other than this Feisty runs great - please help
Thanks guys.

---

### Post by Spr0k3t on 2007-02-19
If you can still boot to Dapper/Edgy, compare the differences betwixt lsusb and that of Feisty.  That may be where your answer is.

---

### Post by vishnu on 2007-02-19
FEISTY LSUSB:
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 10d6:1100 Actions Semiconductor Co., Ltd MPMan MP-Ki 128 MP3 Player/Recorder
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  


DAPPER LSUSB:
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 10d6:1100 Actions Semiconductor Co., Ltd MPMan MP-Ki 128 MP3 Player/Recorder
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000

---

