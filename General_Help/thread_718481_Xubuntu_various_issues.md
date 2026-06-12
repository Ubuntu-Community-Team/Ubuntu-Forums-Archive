---
title: "Xubuntu various issues"
date: 2008-03-08
forum: General Help
---

### Post by yehudah2002 on 2008-03-08
Hello everyone,
I'm happy to become a part of the Xubuntu community, after installing Xubuntu alternate installtion (version 7.04).
However, there are some issues that I fail to understand while I'm working with Xubuntu:
1) The ".exe" type files won't work at all! They won't open or execute anything. Need help...
2) All of my MP3 files (as in songs) aren't playing at all on the Xubuntu attached media player. Need help with this one too. 
3) I don't know how to configure the internet connection with Xubuntu. I have a wireless connection, and my other computer is the host computer of the internet connection. If there is any way I can recieve help with this one, please let me know... (by the way, it's a "Thomson" router. Hope this helps).

I really want to get working with this OS. Please help me... :)

Regards,
yehudah2002

'Cuz U can't beat da best...'
:popcorn:

---

### Post by chewearn on 2008-03-08
> **yehudah2002 said:**
> Hello everyone,
I'm happy to become a part of the Xubuntu community, after installing Xubuntu alternate installtion (version 7.04).
However, there are some issues that I fail to understand while I'm working with Xubuntu:
1) The ".exe" type files won't work at all! They won't open or execute anything. Need help...

*.exe are Windows executables, and will not run as it is in Linux.  Some *.exe can be "fool" into running, if you install Wine.  Go to:
Xubuntu Top Panel Menu > Applications > System > Add/Remove...

Type in "wine" in the search box; the rest should be self explanatory.

To find out more about Wine: [http://www.winehq.org/](http://www.winehq.org/)

> 
2) All of my MP3 files (as in songs) aren't playing at all on the Xubuntu attached media player. Need help with this one too. 


By default, mp3 codec is not installed due to legal issues.  To install the codec, read this:
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
or
[http://ubuntuforums.org/showthread.php?t=661833](http://ubuntuforums.org/showthread.php?t=661833)

> 
3) I don't know how to configure the internet connection with Xubuntu. I have a wireless connection, and my other computer is the host computer of the internet connection. If there is any way I can recieve help with this one, please let me know... (by the way, it's a "Thomson" router. Hope this helps).


What happened when you click on the network icon in the notification area (or the tray, as they call it in Windows), can you see your wireless network listed?


Welcome to the community!:popcorn:

---

### Post by yehudah2002 on 2008-03-08
> **AstalaVista said:**
>  What happened when you click on the network icon in the notification area (or the tray, as they call it in Windows), can you see your wireless network listed?


Hi,
When I go to network, it says: "This network interface is not configured", and I don't have any symbol of the network in the notification area.

What should I do?

Thanks! :-)

---

### Post by chewearn on 2008-03-08
What kind of wireless hardware do you have?

You mentioned in your first post that you are running ver 7.04.  Is there a particular reason you avoid ver 7.10?  I believe there was a huge improvement in wireless support between 7.04 and 7.10.

---

### Post by yehudah2002 on 2008-03-09
Hi,
I'm running version 7.04 because I couldn't able to install version 7.10 with the live CD.
It got stuck all of the time, and I couldn't install at all.
Once I get the internet up and running, I'll get the version 7.10.
Can you help me on that one?

---

### Post by chewearn on 2008-03-09
Unfortunately, I no longer has a 7.04 installation, so I will have to work from memory.  As I mentioned, there is a big difference between 7.04 and 7.10 network set-up, notably the addition of the Network Manager.

So, first thing first; we need to check whether the hardware is detected, the driver support is available and properly loaded.

1. What is the wireless hardware you are using (brand and model number, or chipset)?

2. Is it a USB or PCI device?
In the terminal, the following command will list your USB devices:
```
lsusb
```
or for PCI device:
```
lspci
```

3. Are your wireless network set-up as open system, WEP, WPA or WPA2?

4. What is the IP configuration for your network?  I.e. is it DHCP enable or static IP assignment?


Some people like wicd: [http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)  You will probably have to temporary use wired network to install.

---

### Post by chewit on 2008-03-09
Yehudah, its defentily worth upgrading to 7.10. It solved my WiFi issue. You could just use an alternate CD for the 7.10 install. Or use Xubuntu 7.10

---

### Post by yehudah2002 on 2008-03-10
I've upgraded the Xubuntu to version 7.10 using alternate install.
What should I do now (and please... no manuals...)?

---

### Post by chewearn on 2008-03-10
Is your wireless still not working?  You should now get a network icon in the notification icon; just click on it.  If your wireless hardware is working and it is detecting your wireless network, select the network, and it should start connecting to it.

Else, go back to my previous post #6, and try to answer the questions.  It will help diagnose the problem.

---

