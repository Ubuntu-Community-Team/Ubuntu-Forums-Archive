---
title: "Android connectivity issue"
date: 2014-09-05
forum: General Help
---

### Post by gregory6 on 2014-09-05
Hello all,

First of all, I apologize if this has already been posted. I've search around and found similar issues but nothing has worked for me. 

I'm running 14.04 LTS and just simply want to connect my android phone (Galaxy Nexus) to my pc to transfer data, etc. When I plug it in via usb, it charges the phone but there is no recognition of the device in ubuntu. adb devices returns nothing. lsusb does not show the phone being connected (no samsung devices listed), but lists one port as "micromax" (probably because I'm using the usb cord from a kindle). I've updated, installed phablet tools, nothing seems to work. When I connect the android to my windows PC it recognizes it immediately. When I connect my iphone to the ubuntu PC, it is also recognized immediately. Anyone experienced this? What can I do to get the android recognized in ubuntu?
I'm not sure if I just need to reinstall adb or what... in case it's not evident based on my language and this being my first post I'm quite new to this OS.
Thanks in advance!

---

### Post by raptir on 2014-09-05
The Galaxy Nexus uses MTP to connect to your computer. MTP should be fully supported out of the box in Ubuntu 13.04 and later.  I am not sure what these phablet tools are supposed to do, but you shouldn't need them. You actually shouldn't even need adb/fastboot installed to get the device connected to transfer files. 

Since you do have adb installed, what happens if you run:

```
adb devices
```

Do you get any devices detected? Even though the USB cable works in Windows, do you have any other USB cables you can try?

---

### Post by gregory6 on 2014-09-05
Thanks for the reply. When I run adb devices it simply returns
```

List of devices attached



```

So it refuses to recognize that the phone is connected. I tired borrowing a friends usb cord and it made no difference. Is there a way to update mtp or would that have been included when I ran sudo apt-get update? 

Thanks again

---

### Post by e1ektrob0y on 2014-09-06
You could install SSHDroid on your phone and transfer files from Ubuntu with scp. It means you don't need to plug the phone in to anything, as long as it's connected to the same network as your Ubuntu pc...

---

### Post by gregory6 on 2014-09-06
> **e1ektrob0y said:**
> You could install SSHDroid on your phone and transfer files from Ubuntu with scp. It means you don't need to plug the phone in to anything, as long as it's connected to the same network as your Ubuntu pc...

Sweet, I'll check out that option. Unfortunately my main goal here is to install ubuntu on the nexus, which would require it to be in fastboot mode; so I think the only way to go about it is to get a usb connection working. I plugged it into my buddy's laptop which is also running 14.04, so the problem is definetely ubuntu not wanting to recognize it. Is there a permission I need to change? Anybody know if there's something I need to do beyond unlocking and enabling usb debugging on the phone? Appreciate the help and insight, thanks again.

---

