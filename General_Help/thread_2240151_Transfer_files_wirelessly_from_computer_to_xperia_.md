---
title: "Transfer files wirelessly from computer to xperia c1505"
date: 2014-08-18
forum: General Help
---

### Post by t0p on 2014-08-18
Please don't shoot me down in flames for posting this, I *have* googled but can't find what I want, honest! I've been given a Sony Xperia C1505 android phone, no manual.  I know I should be able to transfer files to/from phone and computer, I actually read it somewhere but can't remember where... anyway that's what I want to do, put music files etc onto my phone from my computer via wifi.  Computer running Ubuntu 12.04, phone running Android 4.1.1.

Cheers.

**EDIT:** Just thought to add, I don't know how to transfer files via USB either.  I connect the phone to the computer with the USB cable, check USB Tethering in Settings on the phone, but the computer sees the phone as an internet connection.  I've tried telling Ubuntu to disconnect this new internet connection, but that just makes the computer ignore the phone's existence instead of seeing it as a folder (which I thought might happen).

Any thoughts?

---

### Post by sotiris2 on 2014-08-18
Well you could try installing [airdroid](https://play.google.com/store/apps/details?id=com.sand.airdroid&referrer=utm_source%3Dairdroid%26utm_medium%3Dhomepage) That is an appl for your phone that will allow you to manage your phone via your webrowser (you ll probably type in your phones ip which i guess the app will show.) It is supposed to be able to manage your sms contacts etc if you want. But I haven't tried it.

Or if that doesn't work (or you need a 'premium' edition to actually do anything useful) you could configure samba in ubuntu either via [command line](https://help.ubuntu.com/community/How%20to%20Create%20a%20Network%20Share%20Via%20Samba%20Via%20CLI%20(Command-line%20interface/Linux%20Terminal)%20-%20Uncomplicated,%20Simple%20and%20Brief%20Way!) or via [GUI](http://www.unixmen.com/how-to-configure-samba-using-a-graphical-interface-in-ubuntu/). Then you can use [this app](https://play.google.com/store/apps/details?id=lysesoft.andsmb) on your phone to access the shared folder and download to your phone. I 've tested this and it works without having to pay for any premium versions. Its just a basic file manager with samba access.

---

### Post by Harsh_Parikh on 2014-08-18
> **sotiris2 said:**
> Well you could try installing [airdroid]("https://play.google.com/store/apps/details?id=com.sand.airdroid&referrer=utm_source%3Dairdroid%26utm_medium%3Dhomepage") That is an appl for your phone that will allow you to manage your phone via your webrowser (you ll probably type in your phones ip which i guess the app will show.) It is supposed to be able to manage your sms contacts etc if you want. But I haven't tried it.



Well,I tried this and even running it till date....The main purpose of this app is what you want-Transfer Media-... Instead that,it may be helped to find the phone if it losts...
And many more other features you would like it...

---

### Post by t0p on 2014-08-18
Thanks for the responses, sotiris2 and [COLOR=#000000]Harsh_Parikh.  For now, I am using a bluetooth dongle to transfer music to my phone.  I will check out your suggestions though, as my computer doesn't have bluetooth built-in and I don't generally carry my bluetooth dongle around with me (it's such a tiny thing, I could easily lose it).[/COLOR]

---

