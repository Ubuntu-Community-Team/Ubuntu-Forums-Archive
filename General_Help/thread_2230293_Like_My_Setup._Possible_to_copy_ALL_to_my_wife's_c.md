---
title: "Like My Setup. Possible to copy ALL to my wife's computer?"
date: 2014-06-18
forum: General Help
---

### Post by 777funk on 2014-06-18
I ended up loosing my Ubuntu install a few weeks ago due to an accident with the shred command #-oBut the good thing was, I needed to do some maintenance anyways and it gave me excuse to upgrade to a new machine (i7 4770S processor) and got a great deal. Today I finally have my system setup similarly to how I had it but 64 bit instead of 32 bit and Xubuntu instead of Ubuntu. Even Win7 flies on this machine... so it's no workout for Xubuntu. I was amazed even under what was a hrd load for my old machine... the heat sink on the CPU isn't even warm. Before it'd be toasty to hot on the old machine. So wow! Maybe I should be happy about the Shred incident.

Anyways, enough of the background... just excited about the new setup. So... now I have things how I like them. Can I install Xubuntu on my wife's machine, copy my /Home partition to hers, and have it setup just like I am setup? 

Could I just copy the entire install so I don't have to download all the install files and updates again? We have a very slow connection (512k on a good day) so if that could work I'd be thrilled!

---

### Post by CaptainMark on 2014-06-18
You could try to clone a hard drive but this is probably not the best thing to do or the easiest. I would make a fresh install and then copy various configuration files across to her home folder, ~/.config and ~/.local would contain most of your configuration files.

---

### Post by TheFu on 2014-06-18
Yes, you can just copy the entire partitions over, but then manually fix the partitions, network MAC and re-install GRUB, but there are risks and on a new pre-installed Windows box, this probably won't work. Why not?  UEFI.

So ... besides the base installation, you can capture a list of installed packages and you can most certainly migrate the $HOME over without fear at all. [http://blog.jdpfu.com/2013/12/11/how-to-migrate-debian-ubuntu-systems-and-data-overview](http://blog.jdpfu.com/2013/12/11/how-to-migrate-debian-ubuntu-systems-and-data-overview) explains ... except the UEFI stuff. Start here [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) for info on that.

---

