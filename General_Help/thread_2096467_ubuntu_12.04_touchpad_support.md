---
title: "ubuntu 12.04 touchpad support"
date: 2012-12-20
forum: General Help
---

### Post by NyoGoat on 2012-12-20
I installed ubuntu 12.04 using the windows installer, it did everything and there was no customization on my part yet.  I'm a pretty new linux user.  I am using an Asus laptop A55VD.  My touchpad does not work as well as it does in windows, and there is no right click capability right now.  I found on an Ubuntu help wiki[ here]("https://wiki.ubuntu.com/DebuggingTouchpadDetection") Instructions

> Enabling right button click for clickpads on Ubuntu 12.04 LTS

Ubuntu 12.04 LTS added support for clickpads. The buttons are pressed by pressing the surface of the trackpad itself. All known clickpads, with the exception of the Apple Magic Trackpad, have indications on the trackpad for where the left and right buttons are. Clicking in the right button area should cause a right button click action. However, right button click support was added too late in the 12.04 LTS development cycle to be enabled by default. It is enabled by default in Ubuntu 12.10 and on.

Fortunately, the right click functionality is present and working in the release. It simply needs to be enabled. The attached enable-rightbutton.sh script may be used to simplify the process. After downloading the script, execute the following:


chmod a+x enable-rightbutton.sh
./enable-rightbutton.sh <device id|device name>
Be sure to use the device id or name of your specific trackpad. You can list the devices on your computer using the "xinput" command.

I did the first part, but i'm not sure how to enter in the second line where it asks for <device id/Device name>  From running "xinput" it looks like I have ETPS/2 Elantech Touchpad   id+13  [slave pointer (2)]  

I tried entering ./enable-rightbutton.sh <13> but that is wrong.

Thanks for any help!

---

### Post by 3rdalbum on 2012-12-20
Delete the <> symbols and try again.

This is a good example of "why new users should install the latest Ubuntu". It's just too bad that so many people say things like "Don't install version x, I don't like this change they have made, use an earlier version instead."

---

