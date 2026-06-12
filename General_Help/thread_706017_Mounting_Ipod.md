---
title: "Mounting Ipod"
date: 2008-02-24
forum: General Help
---

### Post by bigearl on 2008-02-24
hey, i installed gtkpod for my ipod touch but i don't really know what to do. i know i need to get my ipod to mount but i don't know how. i click on load ipod(s) but nothing happens. can anyone give me a step by step instructions on this? or have a link to something useful?

thanks

---

### Post by Crafty Kisses on 2008-02-24
> **bigearl said:**
> hey, i installed gtkpod for my ipod touch but i don't really know what to do. i know i need to get my ipod to mount but i don't know how. i click on load ipod(s) but nothing happens. can anyone give me a step by step instructions on this? or have a link to something useful?

thanks

You may find this useful.

[https://help.ubuntu.com/community/PortableDevices/iPod]("https://help.ubuntu.com/community/PortableDevices/iPod")

---

### Post by bigearl on 2008-02-24
i need help on mounting my ipod touch.

---

### Post by bigearl on 2008-02-24
anyone? when i plug in my ipod touch the only thing that pops up is something about a camera lol

---

### Post by fwre01 on 2008-02-24
does the ipod appear in the Places > Computer?

---

### Post by bigearl on 2008-02-24
theres something there that says ipod but its there even if my ipod isnt pluged in and when i click on it, it says "Unable to mount the selected volume" then i click on show more details and it says "mount: special device /dev/sdc2 does not exist"

---

### Post by bigearl on 2008-02-24
anyone please help me?

---

### Post by fwre01 on 2008-02-24
when the ipod is plugged in can you see the Ipod in the Hardware Information menu?

I dont have an ipod touch, i have a G5, but my /dev file is /dev/sdc2 and that is mounted in /media/AW_IPOD

i think we need to find out where the /dev file is first, what output do you get from "lsusb"

if you open a terminal and cd to /dev, what output do you get from ls -l sd*

---

### Post by bigearl on 2008-02-24
can you put that in simpler terms..lol im kinda new

---

### Post by fwre01 on 2008-02-24
sure... firstly
1) ensure the ipod is plugged in (mine displays the do not disconnet logo appear)
2) go to System > Preferences > Hardware Information
3) can you see your ipod listed there anywhere?

If you can, click on it and click the advanced tab and it should display the block.device with a string similar to /dev/sdc

Also...

open a terminal window and type "lsusb" you should see something like this....

Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 005: ID 05ac:1209 Apple Computer, Inc.
Bus 004 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000

---

### Post by bigearl on 2008-02-24
when i do the second thing you told i see 
```
Bus 005 Device 004: ID 05ac:1291 Apple Computer, Inc. 
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000 
```

and when i do the hardware thing i see Ipod with usb imaging interface and usb raw device access so i highlighted ipod and when to advance but i do not see what you said i should , closest one is /dev/5-4

---

### Post by fwre01 on 2008-02-24
OK, the first bit looks ok

I dont think u drilled down far enough in the second bit, in my hardware information menu i have "ipod" as a menu, but i can the expand that to 
> USB Mass Storage Interface
     > SCSI Host Adaptor
          > SCSI Device
Finally....   > iPod

Thats the one you want to be looking at, then from the advanced tab you should see the correct /dev file

---

### Post by bigearl on 2008-02-24
all i have is those i listed above i don't see anything else involving ipods there

---

### Post by fwre01 on 2008-02-24
do you have a file called sdc? sdc1? or sdc2? in the /dev directory?

---

### Post by bigearl on 2008-02-24
no i do not.

---

### Post by bigearl on 2008-02-24
bump

---

### Post by fwre01 on 2008-02-24
it seems the ipod touch does not mount as a normal ipod

see if this guide helps

[https://help.ubuntu.com/community/PortableDevices/iPhone](https://help.ubuntu.com/community/PortableDevices/iPhone)

---

### Post by bigearl on 2008-02-24
no it doesnt since i cant jail break my ipod cuz i have 1.1.3 and i dunnoh ow to downgrade on linux. anyone know how to fix this?

---

### Post by bigearl on 2008-02-24
bump PLEASE HELP ME

---

