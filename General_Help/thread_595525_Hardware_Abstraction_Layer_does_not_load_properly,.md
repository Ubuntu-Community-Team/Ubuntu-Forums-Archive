---
title: "Hardware Abstraction Layer does not load properly, ethernet is inoperable"
date: 2007-10-28
forum: General Help
---

### Post by Nzer24 on 2007-10-28
Well....

I just used this guide on some internet wiki that told me how to make ubuntu run significantly faster. Maybe I should have seen this coming. I made most of the recommended tweaks, and used telinit to reboot my X environment. Crap, there's a window that says,

Internal Error
HAL not loaded (or something similar)

I assume HAL is "Hardware Abstraction Layer". This is strange, however, because my high-end video card that needed a special driver still was processing my desktop effects smoothly, and therefore with normal hardware acceleration. This led me to believe that the HAL fault happened exclusively on one piece of hardware.  I notice that while firefox does load about three times faster, it doesn't have a connection to the internet. Oh, the irony. I happen to have a very finicky onboard ethernet card, so I just try and recompile the driver. After an X reboot, this still doesn't work.

Now I try to reverse the changes that I made that would have an impact on my internet and HAL. First, I delete the file that I made called bad_list in /etc/modprobe.d. No effect. I comment the changes that I made to /etc/sysctl.conf and run sudo sysctl -p to refresh the sysctl setup. The stuff that I was told to add to the file seemed to be focused on networking and ip, and was also setting limits and defaults. There was no instance of the parameters before. I reboot the X environment again, and still nothing happens. I then comment my modification to vm.swappiness, but this time the whole computer freezes up. I think I can reboot it, or at least get a recovery terminal. I also have Widows XP installed on a dual boot if it's helpful. 

Hardware:
Intel DP35DPM motherboard (P53 and ICH9) with onboard ethernet and audio
Intel Core 2 Quad Q6600 processor
nVidia GeForce 8800GTS video card
2 GB 800MHz ram
Running Ubuntu Gutsy Kernel 2.6.22-14 and Windows XP SP2 via GRUB bootloader

---

### Post by khughitt on 2007-10-28
Hey,

Try changing the line "**CONCURRENCY=shell**" back to "**CONCURRENCY=none**" and that should do the trick. I was having the same problem earlier. The tweak used to work with edgy / feisty, but not so much with Gusty.

Take care,

---

### Post by Nzer24 on 2007-10-29
Thanks, I hadn't tried that. Do you think the other tweaks will still work, because they really seemed to help my computer...

I'll reply if it worked.

---

### Post by Nzer24 on 2007-10-29
Yep, that was the problem. As far as I know the rest of the tweak still works, because it is nice and snappy with loading, so I think I'll be fine. Maybe you should find someone registered with that wiki to give a warning about using that part with gutsy. 

Thanks!

---

### Post by khughitt on 2007-10-29
Glad I could help. :)

Which wiki did you find the info on? Most of the other tweaks have worked fine for me too, but you should still be careful.

---

### Post by kyfho23 on 2007-11-01
> **pwnedd said:**
> Glad I could help. :)

Which wiki did you find the info on? Most of the other tweaks have worked fine for me too, but you should still be careful.


For the record: I found the concurrency tweak here: [http://tvease.net/wiki/index.php?title=Tweak_ubuntu_for_speed](http://tvease.net/wiki/index.php?title=Tweak_ubuntu_for_speed)

and here: 

[http://www.linuxmonitor.net/blog/2007/03/ultimate-ubuntu-performance-tweaking.html](http://www.linuxmonitor.net/blog/2007/03/ultimate-ubuntu-performance-tweaking.html)

It may be in other places. Those were the ones that appear in my google notebook big list of tweak sites. 
: :)

And for the record, this worked fine up until Gutsy. [http://ubuntuforums.org/images/smilies/confused.gif](http://ubuntuforums.org/images/smilies/confused.gif)  

& BTW, see vnevoa's thread at [http://ubuntuforums.org/showthread.php?t=583940&highlight=%252Fetc%252Finit.d%252Frc+CONCURRENCY%253Dshell](http://ubuntuforums.org/showthread.php?t=583940&highlight=%252Fetc%252Finit.d%252Frc+CONCURRENCY%253Dshell)  
 he really put some serious skull sweat into this.

---

