---
title: "Kensington Bluetooth USB Micro Adapter"
date: 2008-04-06
forum: General Help
---

### Post by sekinto on 2008-04-06
So I got this Bluetooth adapter:
[http://us.kensington.com/html/14409.html](http://us.kensington.com/html/14409.html)
and I'm trying to get it to work.

I plugged it in and turned on my computer and when Ubuntu's splash bar was almost full it started showing text output and gave me a bunch or read errors. It was too fast so I couldn't write the exact errors down. If there is some log with the errors I'd be happy to copy and paste them for you though.

Anyway, Ubuntu isn't detecting it either, I think an icon is supposed to show up in the tray... it isn't though.

---

### Post by sekinto on 2008-04-06
Bump.

---

### Post by sekinto on 2008-04-06
Anyone?

---

### Post by the-edmeister on 2008-04-06
Did you try plugging that in once Ubuntu is running?

---

### Post by sekinto on 2008-04-07
Ah, it worked. Thanks. Weird.

---

### Post by signul9 on 2008-04-09
Ack - same issue, same device.  dmesg gives 'cannot enable port 1. maybe the usb cable is bad?'  Device works find in that other OS made by that Bill guy.  

Also, on yank out dmesg gives 'new full speed USB device using uhci_hcd'

I've tried popping it out and in at all sorts of times... 

Anyone?

---

### Post by signul9 on 2008-04-09
[SOLVED]

Official answer = WTF.

Couldn't get new Kensington USB Micro to work at all - so I made the above post.  (Multiple attempts, reboots, terminal commands etc.) 

Rebooted.

Stuck in old USB adapter, some belkin teardrop looking thing.  Device found, set laptop into bluetooth discovery mode.  Everybody happy.  

Ran dmesg saw it found it/assigned Belkin adapter fine.  
  
Pulled out Belkin, stuck in Kensington - flash of blue light from Kensington adapter......????

Ran DMESG - liked the results.... 

Kensington adapter now working perfectly...

---

### Post by nlippincott on 2008-04-28
I just purchased one of these adapters, being attracted to it by its small size. This discussion thread was the only reference I found to this particular adapter, so I was fairly confident I could get it working.

I plugged it in to a Dell laptop running Hardy Heron (just 3 days after its release), and the bluetooth icon popped right up. Worked perfectly.

I then tried booting the machine with the adapter in. Again, it worked perfectly.

I have not tried any previous Ubuntu versions, but if you are using Hardy, I would certainly recommend this adapter.

---

