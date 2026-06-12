---
title: "Ubuntu not recognizing external HDD via USB"
date: 2008-03-01
forum: General Help
---

### Post by JimBuntu on 2008-03-01
I have an external hdd that has worked on my windows computer and my Ubuntu laptop, so I tried multiple times to plug it into my desktop computer but for some reason it is not recognizing it. Is there something that I am missing here? The hard drive turns on when plugged in and I can here it running, it is just not being recognized on my Ubu Desktop.

---

### Post by JimBuntu on 2008-03-01
bump

---

### Post by JimBuntu on 2008-03-01
Last chance to answer. Ill just figure nobody knows...

---

### Post by JimBuntu on 2008-03-01
maybe today????

---

### Post by PuckstopperGA on 2008-03-02
I have the same problem. BIOS sees my external USB drive, and i can even see it in 'hardware information' under the preferences menu. But for whatever reason it won't show up under nautilis... Hoping someone out there has an idea...

---

### Post by FXEF on 2008-03-02
> **PuckstopperGA said:**
> I have the same problem. BIOS sees my external USB drive, and i can even see it in 'hardware information' under the preferences menu. But for whatever reason it won't show up under nautilis... Hoping someone out there has an idea...

If the USB drive does not show in Nautilus file browser, it is not mounted.  Manual mount the drive.

---

### Post by PuckstopperGA on 2008-03-05
Well I figured out my problem - I accidentally deleted the partition table of the drive. I was attempting to install Windows 98 on another hard drive and turned that USB drive off, yet when the computer powered on it turned the drive on automatically (what a lovely feature!). As a result, when I installed 98 I believe it wiped out the table on the USB drive as well as the drive I had asked it to install on. I used a recovery program and then was able to mount the drive normally. Hope this helps the OP.

---

### Post by MultipleSargasms on 2008-03-05
Automatic mounting might have been disabled somehow. Just like FXEF said, you should try to manually mount the drive. [This might help]("http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=4432348"). Good luck :)

---

### Post by JimBuntu on 2008-03-07
So, how do you do that? I know I've seen something that said automatic mount and I could've swore it was turned on, so how do I check this?

---

