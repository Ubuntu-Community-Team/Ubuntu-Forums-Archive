---
title: "Ubuntu Live USB + Secure boot"
date: 2023-03-27
forum: General Help
---

### Post by biomecanoid on 2023-03-27
Hello,


I have made a live persistent Ubuntu USB and it was working fine with Secure boot on my laptop. There are a few day now that it stopped working and I have to disable secure boot form the bios for the USB to boot. How do I fix this ?

I believe I updated the OS on the live USB and that somehow messed up its ability to boot with secure boot on.

I would like to fix this preferably without wiping the data on the drive

Thank you
Chris

---

### Post by guiverc on 2023-03-27
You haven't given any details as to what Ubuntu product/release you're asking about, nor if it was kept fully-upgraded.

You are aware that there have been recent *key revocations* which meant your system needed to be updated prior to the date the key revocation occurred; otherwise you'd have to disable secure boot to get an non-updated machine to boot.

eg. [https://fridge.ubuntu.com/2023/03/23/ubuntu-20-04-6-lts-released/](https://fridge.ubuntu.com/2023/03/23/ubuntu-20-04-6-lts-released/) 

(the new keys were placed on [22.04.2 media]("https://fridge.ubuntu.com/2023/02/24/ubuntu-22-04-2-lts-released/"); it was one of the reasons that [22.04.2 release was delayed]("https://discourse.ubuntu.com/t/ubuntu-22-04-2-delayed-until-february-23/33319")  )

My guess is your system was updated on the correct day by that or another system you use (*Ubuntu, Windows & all OSes updated on an agreed date with SHIM/boot related changes*), and it should not have been a problem if the other OSes were updated in the day+ prior to the revocation of the keys (*which is the last change rolled out*).

With persistence media; re-creating the media is usually the easiest fix.  Changes are not made to the original ISO (*it's read-only*) meaning it'll still have *deprecated* keys and your boot firmware won't follow the *linked-list* of changes stored in the *persistence* area of your media; as those are loaded after boot, thus it *abends* (*abnormal end*) with error message.

How you created the persistence really matters here, and you provided no clues, but I'd just re-create it.

---

### Post by biomecanoid on 2023-03-28
You haven't given any details as to what Ubuntu product/release you're asking about, nor if it was kept fully-upgraded.




------------
[B]I used ubuntu-22.10-desktop-amd64.iso live and from there i installed mkusb to make a persistent live ubuntu usb
[/B]------------


You are aware that there have been recent key revocations which meant your system needed to be updated prior to the date the key revocation occurred; otherwise you'd have to disable secure boot to get an non-updated machine to boot.


eg. [https://fridge.ubuntu.com/2023/03/23...-lts-released/](https://fridge.ubuntu.com/2023/03/23...-lts-released/)


(the new keys were placed on 22.04.2 media; it was one of the reasons that 22.04.2 release was delayed )


------------
**I made the USB about 2 weeks ago and seems that secure boot would "break" when I installed something that needs to update the OS**
------------










My guess is your system was updated on the correct day by that or another system you use (Ubuntu, Windows & all OSes updated on an agreed date with SHIM/boot related changes), and it should not have been a problem if the other OSes were updated in the day+ prior to the revocation of the keys (which is the last change rolled out).


With persistence media; re-creating the media is usually the easiest fix. Changes are not made to the original ISO (it's read-only) meaning it'll still have deprecated keys and your boot firmware won't follow the linked-list of changes stored in the persistence area of your media; as those are loaded after boot, thus it abends (abnormal end) with error message.


------------
**I have several games/apps on my persistent live USB I would prefer not to wipe it and start over can the existing USB be saved ?** 
------------






How you created the persistence really matters here, and you provided no clues, but I'd just re-create it.


------------[B]
I used mkusb and followed the procedure found here: 
[https://www.howtogeek.com/14912/create-a-persistent-bootable-ubuntu-usb-flash-drive/#:~:text=Ubuntu%20itself%20claims%20it%20needs,least%206%20GB%20in%20size](https://www.howtogeek.com/14912/create-a-persistent-bootable-ubuntu-usb-flash-drive/#:~:text=Ubuntu%20itself%20claims%20it%20needs,least%206%20GB%20in%20size).

[/B]
------------

_Note that the original "_**ubuntu-22.10-desktop-amd64.iso**_" live USB still works fine only the persistent live USB made with mkusb does not work _

If you need more details let me know

---

