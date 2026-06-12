---
title: "Grub problems"
date: 2013-08-16
forum: General Help
---

### Post by Gregor_s on 2013-08-16
Hi,

I have a dual boot laptop with Ubuntu 12.04 LTE and Ubuntu 13.04 installed. Everything worked fine until a couple of days ago when I was logged in 12.04 and installed updates. Right after first installation another popped up and I pressed install again - that was a different behaviour then normal. Usually only one installation is required at once. Felt odd.

After this I now have problems with my Grub. Instead of normal options I had to either boot in 13.04 (default) or 12.04 plus some save modes I now have these options (around 20 options already):
- Ubuntu, with Linux 3.2.0-51- generic pae
- Ubuntu, with Linux 3.2.0-51- generic pae (recovery)
- Previous Linux versions
- Memory test (memtest 86++)
- Memory test (memtest 86++, serial console 115200)
- Ubuntu, with Linux 3.8.0-27- ... long text...
-Ubuntu, with Linux 3.8.0-26- ...
.
.
.

First option with Linux 3.2.0... takes me to Ubuntu 12.04 and Linux 3.8.0... to Ubuntu 13.04. Both OS work, but I installed new updates for 13.04 and got another option now Ubuntu' --class ubuntu... long text...

I would like to clean my Grub options and stop adding to it with every update I'm going to do. I tried Boot Repair but it did not help. 
Please advise me what to do.

[http://paste.ubuntu.com/5993381/](http://paste.ubuntu.com/5993381/)

---

### Post by GwL3eNC on 2013-08-16
It's normal. grub adds new entrys. One easy way to fit the list like you want is to use grub customizer

sudo add-apt-repository ppa:danielrichter2007/grub-customizer
 sudo apt-get update
sudo apt-get install grub-customizer

Install it, start it, delete listitems you dont want and save. Ready.

I think you cant stop grub doing this. after every dist-upgrade you get new items.
Thats the way it works.

---

### Post by Petro Dawg on 2013-08-16
You can also uninistall older kernals using Synaptic Package Manager (filter installed packages with "linux-image" to see all installed kernals).  Just be careful not to delete your latest stable one.  This would have to be repeated everytime the kernal is updated (which is often).

---

