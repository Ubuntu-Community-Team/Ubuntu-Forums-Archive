---
title: "No alsa support with Nvidia nforce 410 (Realtek ALC655 codec)?"
date: 2005-10-25
forum: General Help
---

### Post by compless on 2005-10-25
I've got this board:
[http://www.biostar.com.tw/products/mainboard/board.php?name=GeForce%206100-M7](http://www.biostar.com.tw/products/mainboard/board.php?name=GeForce%206100-M7)

Unfortunatly I am Only able to get nvidias official OSS driver working. No alsa.

And as alsaconf is ripped out of ubuntu I get it that the card should get detected automaticly. Or am I wrong?
Cause this card should be supported right?  

Best regards,
Rikard Wissing

EDIT: Well I got it working now... It works fine with the latest realtek audiopack..

---

### Post by atif on 2005-11-04
I have the same motherboard and I can not get the audio working. It does not detect the sound card. :( I am using Breezy Badger (5.10). How did you get it working? Please let me know.
Also did you have any luck with getting the video working with Nvidia driver?

---

### Post by mkaylor on 2006-02-02
My soudcard is not detected on my Biostar motherboard.  Any help would be appreciated!!

Thanks,
Mike

---

### Post by atif on 2006-02-03
I downloaded the latest Nvidia driver from their website. Installed and configured following the instructions. After that go to the Preferences and Sound settings (can't remeber actual name). Their select the OSS from dropdown, instead of ALSA. The Nvidia driver is OSS only. This should get you going.

Regards
Atif Khan

---

