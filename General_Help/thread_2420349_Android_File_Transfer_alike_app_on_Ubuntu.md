---
title: "Android File Transfer alike app on Ubuntu?"
date: 2019-06-03
forum: General Help
---

### Post by mars1990 on 2019-06-03
Replaced old Win 7 with Ubuntu and it is kind of fun. However, One question annoys me as I can't find a reliable way to connect Android to Ubuntu like I did on Windows 7. Need some advice on this for Android device management.

---

### Post by Xian on 2019-06-03
You didn't explain much on the statement "[COLOR=#000000]like I did on Windows 7". 

However .... if via wireless you may find this helpful: 

[https://www.omgubuntu.co.uk/2018/11/connect-android-ubuntu-gsconnect](https://www.omgubuntu.co.uk/2018/11/connect-android-ubuntu-gsconnect)[/COLOR]

---

### Post by kurt18947 on 2019-06-08
I bought a new phone - Asus Zenphone Max plus or something like that and couldn't connect like I could with the old Android phone. Problem turned out to be that I needed to enable USB data transfer on the phone. Did you check that?

---

### Post by yetimon_64 on 2019-06-08
You may need to install a package called mtp-tools on Ubuntu so you can browse to the files and manage files from your normal file browser on Ubuntu.

To install mtp-tools on Ubuntu open a terminal and use ...
```
sudo apt install mtp-tools
```

With it installed plug in your android device and set the access for "file transfers" on the drop down settings menu, like ...
[ATTACH=CONFIG]283399[/ATTACH]
Then open your usual file manager, in my case I am using caja, and navigate to the files on the android device. From there you can copy, paste, create and delete files etc. If the files on the android device are hidden you probably won't be able to see them in the file manager on Ubuntu even with hidden files showing. In such a case you will need to unhide them on the android device first. Next screenshot is my android phone mounted in the caja file manager on Xubuntu 18.04...
[ATTACH=CONFIG]283400[/ATTACH]

Regards, yeti.

---

### Post by freebird54 on 2019-06-10
There are other ways to get this functionality as well. I have Samba enabled on my systems, and an app called ES File Explorer (pro) (there are others, but this seems quickest) on Android devices can login to your setup wirelessly. I run a couple of tablets as well as a phone, and find this capability useful, wherever I am in the house. I have been known to dload a video to a tablet, then cast it to a TV out in the back yard... and of course my library of ebooks is also on the desktop. Of course, direct connect works too :)

freebird

---

### Post by mars1990 on 2019-06-11
> **kurt18947 said:**
> I bought a new phone - Asus Zenphone Max plus or something like that and couldn't connect like I could with the old Android phone. Problem turned out to be that I needed to enable USB data transfer on the phone. Did you check that?

Yes, USB debugging and data transfer (MTP) are enabled

---

### Post by anser11 on 2019-06-13
As for how to transfer Android file,it depends on where you want to transfer them? compuetr or other mobile phones?
Bluetooth is good for transferring Android data/file quickly, but for large files it may not be safe to do so.
USB cable can also do that,but you need to install a Android transfer app on computer for it.
As for the advice on this for Android device management:
[https://www.androidphonesoft.com/resources/android-device-manager-software-reviews.html](https://www.androidphonesoft.com/resources/android-device-manager-software-reviews.html)

---

### Post by yetimon_64 on 2019-06-13
> **anser11 said:**
> ...USB cable can also do that,but you need to install a Android transfer app on computer for it.
With a USB cable you only need to install the mtp-tools package, which integrates access to the android device into whichever file manager is in use on ubuntu. Not a separate app as such. "mtp-tools" provides mtp filesystem support to the Ubuntu OS. See the second screenshot in post #4 for it in action with direct file manager access to a Samsung Android phone, the only package I added there was mtp-tools.

---

