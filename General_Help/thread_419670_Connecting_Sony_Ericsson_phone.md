---
title: "Connecting Sony Ericsson phone"
date: 2007-04-23
forum: General Help
---

### Post by singlemalt on 2007-04-23
I have a SE k750i which I want to use on my feisty installation.

I have read other reports of users plugging in and feisty instantly recognising the phone and mounting the memory card as a drive - no luck for me though. I am fiddling around at the moment with multisync to try and sync my contacts with evolution (with little success .... another time)

For now I would be happy to access the stuff on my memory stick - Any help for this relative newbie?

---

### Post by baddduh on 2007-04-23
I have the same problem with a 810i, in edgy it was working out of the box but no luck with feisty.

---

### Post by singlemalt on 2007-04-24
As a bit of a primer - I dis 'lsusb' before and after connection

Before:
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 07cc:0501 Carry Computer Eng., Co., Ltd 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 046d:c512 Logitech, Inc. 
Bus 001 Device 001: ID 0000:0000  

After:
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 07cc:0501 Carry Computer Eng., Co., Ltd 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 0fce:d016 Sony Ericsson Mobile Communications AB 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 046d:c512 Logitech, Inc. 
Bus 001 Device 001: ID 0000:0000  

I could probably search around and find out how to mount it manually - but I would like it to automount whenever I plug in.

Any help appreciated.

---

