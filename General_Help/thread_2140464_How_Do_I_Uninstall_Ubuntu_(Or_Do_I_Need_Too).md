---
title: "How Do I Uninstall Ubuntu? (Or Do I Need Too?)"
date: 2013-04-29
forum: General Help
---

### Post by CharleyGnarlyP290 on 2013-04-29
Here is my situation:
I have used Ubuntu before about three years ago. Got a new computer and  just haven't messed with it since. i got the urge again and tried 13.04.  I created my disc with no issues, and booted my computer. At first I  just had a black screen. rebooted and the the Ubuntu stuff came up. So I  went through the install process. Everything seemed to go fine, but  when I reboot my machine it boots right into Windows as if I didn't  install Ubuntu. I want to have the option of choosing which OS to use  when I start my computer. 
After reading up more I am thinking I would rather use 12.04 LTS because  I don't want to have to monkey around alot with the OS especially since  it is so new. 
So, how do I get rid of whatever I installed of 13.04? Or, is it even there?
Here are my specs
[[IMG]http://i5.photobucket.com/albums/y193/onaway/2013-04-29_07-45-36_528_zps0aa12dad.jpg[/IMG]]("http://s5.photobucket.com/user/onaway/media/2013-04-29_07-45-36_528_zps0aa12dad.jpg.html")

---

### Post by Frogs Hair on 2013-04-29
Open the windows disk utility and find out if you  successfully created a Ubuntu partition.

---

### Post by r.stiltskin on 2013-04-29
It sounds like you may have simply installed Grub incorrectly, so you might want to try performing one of the fixes explained here: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows").  Don't be put off by the title; it should work for you.

But if you still want to reinstall Ubuntu using 12.04 LTS, don't worry about removing 13.04.  The 12.04 installer will find it (assuming it actually is on your hard disk) and let you install 12.04 in the same partition, replacing the 13.04 installation.  Also, if somehow it's not there, that will become obvious when you run the 12.04 LiveCD.

---

