---
title: "Ubuntu wont boot with ryzen - Using asus b350 motherboard"
date: 2017-04-27
forum: General Help
---

### Post by cgameing on 2017-04-27
I have seen many people on the internet get linux working on the asus b350 plus motherboard but I am yet to find a working configuration.
I can get the ubuntu installer to boot up, but whenever I get to the tab where you format partitions the installer crashes and the bios boots up again. I have also tried install ubuntu on a harddrive then just using that in my pc, but I get a " Kernal panic not syncing attempted to kill init ryzen "exitcode 0x000000009" " error code. This persists between 4.10 and 4.11.

Pc specs:
Motherboard: Asus prime b350-plus
CPU: Ryzen 7 1700
Ram: 1 x 8gig corsair 2133Mhz
Harddrive: WDC Blue 500Gig
GPU's: Rx 460, r7-240 (not in crossfire just for dual monitor support)

Kernals tested:
4.10 
4.11


Am I missing any important bios configurations?
Any help is very much appreciated.

---

### Post by pete-br on 2017-04-28
The Ryzen CPU where released in 2017.

Another post about exactly the same error message is dated from 2015:
[https://askubuntu.com/questions/651974/kernel-panic-not-syncing-attempted-to-kill-init-exitcode-0x00000009](https://askubuntu.com/questions/651974/kernel-panic-not-syncing-attempted-to-kill-init-exitcode-0x00000009)

Using an older kernel with Ryzen shouldn't be a problem. It's only that you might not get the full performance when using Ryzen together with an old kernel.
Using an older kernel could mean problems with other hardware. Like an ACL1220 soundchip for example. Your motherboard is using ALC887, should be fine.
Maybe you can look at newer bios firmware updates and/or hdd firmware updates.

---

### Post by pete-br on 2017-04-28
[https://www.asus.com/Motherboards/PRIME-B350-PLUS/HelpDesk_Download/](https://www.asus.com/Motherboards/PRIME-B350-PLUS/HelpDesk_Download/)
[COLOR=#333333][FONT=Arial][FONT=inherit]Version[/FONT] [FONT=inherit]0609[/FONT][/FONT][/COLOR]
[TABLE="class: table table-bordered, width: 1"]
[TR]
[TH="class: width20 bg-gray, bgcolor: #EEEEEE, align: left"][FONT=inherit]Description[/FONT][/TH]
[TD="class: width80"][FONT=inherit]PRIME B350-PLUS BIOS 0609
Improve memory stability[/FONT][/TD]
[/TR]
[TR]
[TH="class: width20 bg-gray, bgcolor: #EEEEEE, align: left"][FONT=inherit]File Size[/FONT][/TH]
[TD="class: width80"][FONT=inherit]5.84 MBytes[/FONT][COLOR=#999999][FONT=inherit]update[/FONT][/COLOR] [COLOR=#999999][FONT=inherit]2017/04/25[/FONT][/COLOR][/TD]
[/TR]
[TR]
[TH="class: width20 bg-gray, bgcolor: #EEEEEE, align: left"][FONT=inherit]Download from[/FONT][/TH]
[TD="class: width80"][Global]("http://dlcdnet.asus.com/pub/ASUS/mb/SocketAM4/PRIME_B350-PLUS/PRIME-B350-PLUS-ASUS-0609.zip")[/TD]
[/TR]
[/TABLE]
A newer bios firmware could improve compatibility with your new Ryzen CPU. It could also improve many other things.

---

### Post by cgameing on 2017-04-28
First just to point out its DEFINITELY ryzen I put the chip in myself a few days ago.
I updated the bios and I am still getting this issue.

Also aparently the errorcode ends with a b and not a 9 so its actually
---[ end Kernal panic - not syncing: Attempted to kill init! exitcode=0x0000000b

---

