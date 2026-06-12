---
title: "synaptic smart update XCRASH!!"
date: 2005-06-24
forum: General Help
---

### Post by boosted on 2005-06-24
I had 16 updates pending so I used synaptic and did smart update, afterwards it gave me some errors about firefox-gnome-support386.deb something like that.  it let me just click OK. then I restarted the comp and get a "blue-screen" with a grey box in the middle that says it can't start X Server and would I like to see the output? 

well in the output it has codes for stuff like a Warning is (WW)

so here are the warnings:
i had some font warnings but didn't seem to important.. then I had this:

(EE) NVIDIA(0): Fail to load the NVIDIA kernel module!
(EE) NVIDIA(0): ***Aborting***
(II) UnloadableModule: 'nvidia"
(EE) Screen(s) found, but none have a usable configuration

Fatal server error:
no screens found


on a side note: a couple weeks ago I updated to the K7 for my AMD but when I selected the K7 kernel on boot I would get the above error mentiond, so I have just been selecting the 386 kernel and it works fine and so did the nvidia driver.  All I did was do the smart update and got this crap!  now 386 or K7 doesn't work! Please Help!  I need to finish my web site!!

---

### Post by Lunde on 2005-06-24
[QUOTE=boosted]I had 16 updates pending so I used synaptic and did smart update, afterwards it gave me some errors about firefox-gnome-support386.deb something like that.  it let me just click OK. then I restarted the comp and get a "blue-screen" with a grey box in the middle that says it can't start X Server and would I like to see the output? 

well in the output it has codes for stuff like a Warning is (WW)

so here are the warnings:
i had some font warnings but didn't seem to important.. then I had this:

(EE) NVIDIA(0): Fail to load the NVIDIA kernel module!
(EE) NVIDIA(0): ***Aborting***
(II) UnloadableModule: 'nvidia"
(EE) Screen(s) found, but none have a usable configuration

Fatal server error:
no screens found


on a side note: a couple weeks ago I updated to the K7 for my AMD but when I selected the K7 kernel on boot I would get the above error mentiond, so I have just been selecting the 386 kernel and it works fine and so did the nvidia driver.  All I did was do the smart update and got this crap!  now 386 or K7 doesn't work! Please Help!  I need to finish my web site!![/QUOTE]
 Your problem may be that you have upgraded something to do with your kernel. Your Nvidia drivers are probably built for a previous version.

OK, first see if this helps:
$ sudo apt-get install nvidia-kernel-common

$ sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak

$ sudo pico /etc/X11/xorg.conf

Edit the "section device" set the nvidia to nv

        Driver          "nv"

maybe you have to remove the special nividia options to, but try without first.
if not put a # in fron like this. 

#        Option        "AGPMode" "4"
#        Option        "AGPFastWrite" "True"
#        Option        "RenderAccel"   "on"
#        Option        "EnablePageFlip" "True"

If this works, you'll be able to start X, but you have to reinstall your Nvidia drivers after

Hope this helps..

---

### Post by boosted on 2005-06-28
sorry I was away for a while,  anyway I tried your idea and X started, I log in and got a hard freeze ..nothing will work????  No key combination or anything!

---

### Post by Lunde on 2005-06-28
[QUOTE=boosted]sorry I was away for a while,  anyway I tried your idea and X started, I log in and got a hard freeze ..nothing will work????  No key combination or anything![/QUOTE]
 How did you install your Nvidia drivers the first time? DId you just use the ubuntu .deb or did you compile it your self?

Try this before you log in to X:

$ sudo apt-get install nvidia-kernel-common

If this helped, you can also try to change back "nv" to "nvidia" under the device section in xorg.conf 

If you still have problems, I reccomend reinstalling the nvidia drivers.

---

### Post by boosted on 2005-06-28
i just used apt-get to install my nvidia driver before
 oh and when I did the apt-get install nvidia-kernel-common   That was the first thing you told me to try well it said it Was already the Newest Version!??
should I do it again?

how do I go about re-installing the nvidia driver???

---

### Post by Lunde on 2005-06-28
[QUOTE=boosted]i just used apt-get to install my nvidia driver before
 oh and when I did the apt-get install nvidia-kernel-common   That was the first thing you told me to try well it said it Was already the Newest Version!??
should I do it again?

how do I go about re-installing the nvidia driver???[/QUOTE]
 Sorry, just had a quick look, did'nt remember that. So you did get the nvidia-kernel-common, did you try to change back to "nvidia" in xorg.conf?

Reinstalling the Nvidia:

1.)
You can can reinstall the drivers in Synaptic, just right click and choose "Mark for reinstallation"

2.)
If you have problems in X you can do this by:

$ apt-get remove packet_name 

Use the same packet_names as discribed in the guide below 

then reinstall like discribed in this guide
[http://www.ubuntuguide.org/#installnvidiadriver](http://www.ubuntuguide.org/#installnvidiadriver)

---

### Post by boosted on 2005-06-28
uumm while attempting to do this I got unmet dependencies of firefox-gnome-support  i did the apt-get -f   and it asked if I wanted to install it i said Y then it started installing .....  then I get this MSG all accross the screen that just keeps going:

NTFS-fs error (device hda1): ntfs_ucstonls(): Unicode name contains characters that cannot be converted to character set cp437

I have no idea what is going on now!!!

---

### Post by Lunde on 2005-06-28
[QUOTE=boosted]uumm while attempting to do this I got unmet dependencies of firefox-gnome-support  i did the apt-get -f   and it asked if I wanted to install it i said Y then it started installing .....  then I get this MSG all accross the screen that just keeps going:

NTFS-fs error (device hda1): ntfs_ucstonls(): Unicode name contains characters that cannot be converted to character set cp437

I have no idea what is going on now!!![/QUOTE]
 You are one unlucky geek... there are other faults in your system too, this message means it's something wrong reading your ntfs parttiton. I suggest you deal with that later, and do the following:
 
$ sudo gedit /etc/fstab

 Use a # to comment out the NTFS partitions you have mounted.

then:
$ sudo umount -a
$ sudo mount -a

Then proceed with the upgrading of your drivers.

---

### Post by boosted on 2005-06-30
ok, I removed all nvidia packages then re-installed them and did all the settings ..  I then typed    reboot    so it starts doing it's shut down thing but I have a Fail in Postfix: something about host_name???
then it gets to 
*Deconfiguring Network interfaces.....
irq 16: nobody cares (try booting with the "irqpoll" option.
handlers:
[<e0be980d>] (ohci_irq_handler+0x0/0x77f [ohci1394])
[<e0c25a0f>] (rtl8169_interrupt+0x0/0x11b [r8169])
Disabling IRQ #16

it has been sitting here for about 10 min.!?!?!?

---

### Post by boosted on 2005-06-30
anyone?

edit:
I hit the reset button.. ..  X loads the login screen, I log in and again X has a hard freeze???  WTF... someone please help me out!

---

### Post by Lunde on 2005-07-01
[QUOTE=boosted]anyone?

edit:
I hit the reset button.. ..  X loads the login screen, I log in and again X has a hard freeze???  WTF... someone please help me out![/QUOTE]
 I'm not to familiar with your problem, but I've seen similar under Windows. so here's a thought. Can you remove your network card and boot without it? There may be a conflict between the network card and screen card. If it does'nt crash then we have at least located your problem

---

### Post by boosted on 2005-07-03
so if this works, then how do I go about fixxing the conflict?

---

