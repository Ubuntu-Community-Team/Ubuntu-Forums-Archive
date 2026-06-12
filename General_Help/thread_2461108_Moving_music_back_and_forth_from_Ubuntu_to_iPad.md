---
title: "Moving music back and forth from Ubuntu to iPad"
date: 2021-04-24
forum: General Help
---

### Post by jgwphd on 2021-04-24
I have installed the Libimobiledevice software on my Ubuntu 20.04 Dell Vostro (sudo apt-get install libimobiledevice-utils libimobiledevice-dev libgpod-dev)  Now with Nautilus I am able to see some things on the USB attached iPad (like photos and some miscellaneous directories) but NOT any music files and I can't move around in the iPad directory structure. The iPad is 6 years old. If I attempt to write an .mp3 file to the iPad I get errors. 

Also, using Rythmbox the iPad does not show up under "Devices" (it doesn't recognize the iPad). I followed the instructions 5/2019 here: [https://www.groovypost.com/howto/howto/sync-your-iphone-or-ipod-touch-in-ubuntu/](https://www.groovypost.com/howto/howto/sync-your-iphone-or-ipod-touch-in-ubuntu/) but I did not bother to do the upgrade to libimobiledevice package since I just installed it (I assume I get the latest and greatest when I do a fresh install - am I wrong?). I am looking for suggestions to solve my problem of moving mp3 files between Ubuntu and the iPad. Thanks for any assistance.

---

### Post by yancek on 2021-04-24
I would not expect that you would be able to navigate the Ipad and probably will only see a few directories.  I move photo and music files between my iphone and Linux using an app on the iphone called vlc for ios which you can download from the Ipad App Store  I don't use Ipad but I expect this would be available as it is with an iphone.  Once you install vlc for ios on the Ipad, you should be able to open a web browser on Ubuntu and enter the IP address of the Ipad in the address bar and copy to/from there.   Before opening your browser, make sure vlc for ios is open on the Ipad.

To get the IP address for devices, you can use nmap which is explained at the link below.  Apple devices should be displayed showing Apple somewhere in the output so if you have multiple Apple devces, you will have to try each.  

[https://vitux.com/find-devices-connected-to-your-network-with-nmap/](https://vitux.com/find-devices-connected-to-your-network-with-nmap/)

Just so you are aware, an update of the ios version on the Ipad will often make changes and you may have problems copying.  The percentage of Apple/Ipad/Iphone users using Linux is not that large so there isn't much reason to put a lot of effort into this keeping the software up to date.  Apple of course doesn't care.  You can do an online search for 'using vlc for ios on Ubuntu' to find more information.

---

### Post by Holger_Gehrke on 2021-04-24
How about inverting the situation and accessing the Ubuntu Machine from the iPad ? Get a SFTP-client for the iPad and install the ssh server on Ubuntu and configure it to also serve sftp. Then you should be able to copy anything the client has access to on the ipad to the Ubuntu machine and anything you have access to on the Ubuntu machine to the iPad. I do it like that with my Android phone and it's usually faster (older phone with USB 2, and connections with mtp over USB mounted through gvfs are ... "wonky" is a good word for it ).

Holger

---

### Post by jgwphd on 2021-04-28
I want to thank everyone for their suggestions, but I have been side tracked on some other things. I hope to try out your suggestions in a few days and get back to you. I didn't want you to think I was ignoring you. I truly appreciate your assistance.

---

