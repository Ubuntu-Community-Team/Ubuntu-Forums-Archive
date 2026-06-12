---
title: "Googleearth doesn't work after installing Nvidia drivers"
date: 2014-02-21
forum: General Help
---

### Post by sam_baker2 on 2014-02-21
hi,
I have a thumbnail drive on my laptop ( xubuntu 12.04 LTS,  kernel 3.2.0-59-generic 64 bit )

here are some specs on the laptop: 
```

uname -a:
3.2.0-59-generic #90-Ubuntu SMP Tue Jan 7 22:43:51 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

lspci -nn | grep VGA:
00:02.0 VGA compatible controller [0300]: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller [8086:0116] (rev 09)

```

google-earth ran just fine on it. The other day I thought I would try and plug the thumbnail into my
desktop that has the same OS, it ran ok, but I thought I would install the Nvida drivers for the
Nvidia card that is on the desktop.

here are some specs on the desktop:
```

uname -a:
3.2.0-59-generic #90-Ubuntu SMP Tue Jan 7 22:43:51 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

lspci -nn | grep VGA:
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GK107 [GeForce GTX 650] [10de:0fc6] (rev a1)

```
I did a driver update for the Nvidia drivers onto the thumbnail, ( Nvidia accelerated graphics driver version 331 recommended )
and the thumbail worked just fine on the desktop, ( and it was able to display the higher resolution - 1920x1080 ).

soooo... I plugged the thumbnail back into my laptop and the OS was smart enough to reconize that the graphics card
was an Intel, and the thumnail worked just fine, like before.
Except that now when I try to run google-earth using the terminal on the laptop, I get this message:
```
 
./googleearth-bin: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory

```

Aparently, installing the Nvidia drivers did something to libGL.so.1 , and google-earth can't find it now. 
I did a search for libGL.so.1 on the laptop, and the search results show that I do have it:
here is a screenshot of the search results:


Might anyone have a clue why google-earth can not find libGL.so.1 now?

---

### Post by sam_baker2 on 2014-02-21
pardon the term "thumbnail", I meant "thumbdrive"

---

### Post by monkeybrain20122 on 2014-02-21
Sorry, I can't understand what you wrote, it is very confusing.

So you have a thumb drive with Ubuntu installed on it and you have installed google earth in it. You usually  boot it off a laptop with an intel card and google earth works fine,  then one day you booted the usb drive off a desktop with a Nvidia card and you installed the Nvidia driver while in a session using the OS in the usb drive (so installed driver in the usb drive). Now when you boot it off the laptop again google earth doesn't work any more and it complains that libgl is missing.

So everything is happening on your thumb drive rather than the internal hard drives of the laptop and the desktop, is that it?? I don't know what you mean by "plug it in", I suppose you mean booting off the thumb drive?

---

### Post by sam_baker2 on 2014-02-21
The USB thumbdrive on the laptop has the OS on it. ( there is no HD on the laptop ).
Google-earth is on the USB thumbdrive and it did work just fine.
I plugged the USB thumbdrive into the desktop and booted the desktop ( using the USB thumbdrive )
It booted ok and worked. 
The desktop has a Nvidia card.
 I installed the Nvidia drivers from the desktop onto the USB thumbdrive.
The thumbdrive worked just fine on the desktop.
When I plugged the USB thumbdrive back into the laptop, it worked just as before.
Except google-earth does not work on the laptop now.
I get the mesage now that it cannot open libGL.so.1
A search for libGL.so.1 on the laptop gives the results as shown in the attached pic.
The laptop has an Intel graphics card.

---

### Post by monkeybrain20122 on 2014-02-21
Well if you boot a usb drive installed with the Nvidia blob off a machine without a Nvidia card it shouldn't even work at all (with open driver it would) Now you say it was working perhaps because it somehow automatically blacklisted the Nvidia driver and along with it some functionalities are missing? 

Try 

```

sudo updatedb
locate libgl.so.1
```

If you find it (so you haven't uninstalled it ) try to remove xorg-conf and reboot again (on the intel) and see if it works. If still not remove the Nvidia driver and reboot.

---

### Post by sam_baker2 on 2014-02-21
I did a search for xorg-conf and it shows "no files found"

---

### Post by monkeybrain20122 on 2014-02-21
Did you find libgl.so.1?

---

### Post by monkeybrain20122 on 2014-02-21
xorg-config isn't found because you haven't ran
sudo nvidia-xconfig 
after you installed the Nvidia driver, now are you sure you are even using the Nvidia driver when you boot off the desktop?

---

### Post by monkeybrain20122 on 2014-02-21
i think it is the same problem here, since google-earth is 32 bit just like skype.
[http://askubuntu.com/questions/257897/error-loading-libgl-so-1](http://askubuntu.com/questions/257897/error-loading-libgl-so-1)

---

### Post by sam_baker2 on 2014-02-21
yes, I got 8 hits on libglso.1
( see attached pic from my first post )

I have the USB thumbdrive on the laptop.
I can boot it off the desktop if you want.


 When I first plugged the USB thumbdrive into the desktop ( desktop has the Nvidia card )
the USB thumbdrive ran ok. The screen resolution I when I first plugged the
thumbdrive into the desktop was not very high. I installed the Nvidea drivers
rebooted the thumbdrive in the desktop and I got the very high resolution, ( 1920x 1080 ),
 so I am guesing that yes, the Nvideo drivers were working on the thumbdrive.

---

