---
title: "one external hard drive making another one disconnect it seems ...."
date: 2023-10-05
forum: General Help
---

### Post by shantiq on 2023-10-05
EDIT >>   [Solution]("https://ubuntuforums.org/showthread.php?t=2491368&p=14160310#post14160310")


just added a 1TB external drive in a caddie (Seagate) to my setup which has already got 500GB external drive in a caddie (Seagate also) and the new one makes the older one disconnect within a few minutes not sure what why and how this is possible. I have tested that multiple times ie if i remove the new one the old one STAYS connected throughout session




these are entered thus in the /etc/fstab


```
#the old 500 HDD
UUID="3896450861F69058"   /media/shan/500  ntfs  nofail,user,fmask=0111,dmask=0000   0   0   


#the new 1TB HDD
UUID="5E255CB15803AB33"   /media/shan/new1Tb  vfat  nofail,user,fmask=0111,dmask=0000   0   0
```  


Any idea why it might do doing this?    Thanx in advance for learned info here


PS    my DE here is LXDE if that is relevant

---

### Post by oldfred on 2023-10-05
Are they USB powered or have separate power adapters.

I have an USB adapter with USB power and it works great with my SSD, but HDD will not even power up. 
USB ports have a limit on amount of power. Do not know if that is total for all USB ports or not?

---

### Post by shantiq on 2023-10-06
[COLOR=#000000]hi Oldfred

[/COLOR][COLOR=#000000]Thanx for input.  [/COLOR][COLOR=#000000]separate power adapters. 
Also the USB leads I have placed in 2 separate ports now; one 2.0 at the front; other blue 3.0 at the back
If I start the 500Gb 2.0 it is fine. Then I plug the 1TB in the 3.0 and then we will see :) 
I have also now moved the adaptor so they are NOT in the same socket

I thought it might be this to do with leads and plugs; I also read folks writing about Power management ie the PC does not like too many externals running at once and "decides" to disconnect or put to sleep the excess. No idea. That is why i am posting this

  Have moved all leads away from each other USB and adaptor both.    Will wait a bit see how it goes and report[/COLOR]

---

### Post by dragonfly41 on 2023-10-06
I suggest that you use a port expander only on USB 3.0 (back port nearest motherboard) since USB 2.0 is slow.
I drive multiple SSD's through dualport Startech docking bay (powered) but I also have for other devices a USB 3.0 port expander (powered).

---

### Post by shantiq on 2023-10-06
thanx Dragonfly never heard of those ; the one i have is not powered. Will probably get one thanx

current one is only this :) [[IMG]https://i.postimg.cc/ykf8Q2ts/IMG-9183.jpg[/IMG]]("https://postimg.cc/ykf8Q2ts")

---

### Post by dragonfly41 on 2023-10-06
If you go for external Startech dual docking bay be aware that you also require a caddy box for each SSD (but you appear to have only HDD and not SSD).
I use EZConvert Series - Icy DOCK
2.5 to 3.5 SAS/SATA HDD and SSD converter.
The nice feature is that I can plug in SSD drives easily. And you can mix SSD and HDD.

But if you have purchased HDD containers already then a USB 3.0 expander (powered) should do the trick.

I still retain an old USB 2.0 USB expander like yours and keep it only for charging Logitech Bluetooth mouse, keyboard and also a security key.

---

### Post by shantiq on 2023-10-08
> **oldfred said:**
> 
***USB ports have a limit on amount of power***. 


Thanx for this. Looks like therein was the issue. So to make sure to have [COLOR=#800000]*separate ports for separate External drives*[/COLOR] (one would surmise caddied or otherwise)
Truth is even with the little gizmo for a wireless mouse the wireless mouse WILL NOT function right ie it will drag if put in a multiple usb setup with the external caddied drive ...   it can only handle one item here

*Of note also* (not related)  **Fat** only allows 4Gb transfer so to pick **ntfs** if one wants the ability to transfer bigger sizes then 4Gb

So thank you again Oldfred; definitely barking up the correct tree here :)

Marked as solved (again thanx to The Community)

---

