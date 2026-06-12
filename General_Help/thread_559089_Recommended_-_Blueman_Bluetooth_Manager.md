---
title: "Recommended - Blueman Bluetooth Manager"
date: 2007-09-24
forum: General Help
---

### Post by jamesjtucker on 2007-09-24
Greetings all, 
     I just wanted to share with the community as a whole a nifty little app i just picked up from gnomefiles called blueman. I dont work with or for anyone, but i have seen lots of threads asking for stuff this app offers and no posts about it in the archive...

From the website( [http://walmis.balticum.lt/](http://walmis.balticum.lt/)) :
Blueman is a GTK+ bluetooth management utility for GNOME using bluez dbus backend. The aim is to create a full featured graphical bluetooth manager for Linux.

Features:

    * Easy to use interface
    * Storing Favourite devices
    * Send files
    * Browse files on devices
    * List all seen devices
    * View Local/Remote Device information
    * Configure local devices
    * Manage Pairing (Bonding)
    * Host/Connect to Personal Area Networks
    * Bind services to /dev/rfcomm ports, for eg. connecting via gprs
    * Connect to Bluetooth headsets and use them as ALSA audio devices.

Works like a charm on my Thinkpad running Gutsy. I was able to pair my phone and browse the files in less than 2 minutes. Sweet stuff. 
 I stil cant get my Blueant X5 headset to work, (which is probably not blueman's fault) and nautilus throws an error when i try to hit the back or up buttons while browsing, but im sure it will get better.

---

### Post by SpiritIsReality on 2007-09-28
howdy

I was advanced searching, keywords recommended pda, titles only,  to see if I could help on a thread.
solid thread title.
real gem of info.
thanks

trails

---

### Post by vinutux on 2007-09-29
wonderfull app i am running it .

but 1 prob it lack support dialup connection........

any ideas?:guitar:

---

### Post by walmis on 2007-09-30
Hey people, glad you like my app, working hard on the new version.

> **jamesjtucker said:**
> Greetings all, 
     I just wanted to share with the community as a whole a nifty little app i just picked up from gnomefiles called blueman. I dont work with or for anyone, but i have seen lots of threads asking for stuff this app offers and no posts about it in the archive...

From the website( [http://walmis.balticum.lt/](http://walmis.balticum.lt/)) :
Blueman is a GTK+ bluetooth management utility for GNOME using bluez dbus backend. The aim is to create a full featured graphical bluetooth manager for Linux.

Features:

    * Easy to use interface
    * Storing Favourite devices
    * Send files
    * Browse files on devices
    * List all seen devices;
    * View Local/Remote Device information
    * Configure local devices
    * Manage Pairing (Bonding)
    * Host/Connect to Personal Area Networks
    * Bind services to /dev/rfcomm ports, for eg. connecting via gprs
    * Connect to Bluetooth headsets and use them as ALSA audio devices.

Works like a charm on my Thinkpad running Gutsy. I was able to pair my phone and browse the files in less than 2 minutes. Sweet stuff. 
 I stil cant get my Blueant X5 headset to work, (which is probably not blueman's fault) and nautilus throws an error when i try to hit the back or up buttons while browsing, but im sure it will get better.

blueman uses external program called btsco
You can see what's going on by typing

[PHP]
sudo modprobe snd_bt_sco
sudo btsco -v 11:22:33:44:55:66 
[/PHP]

This will print verbose output

> **vinutux said:**
> wonderfull app i am running it .

but 1 prob it lack support dialup connection........

any ideas?:guitar:

It doesn't handle dial up connections internally, no, but you can use gprs easy connect app to do that, but first you need to create a virtual rfcomm device, you can do that by going to the blueman's device properties > scan services > select dial-up connection gateway or something like that and click bind com port. After doing that sudo /etc/init.d/bluetooth restart (will be fixed in the next release)

Then in 'gprs easy connect' select /dev/rfcommX or /dev/.static/dev/rfcommX (if the first one doesn't work)

---

### Post by Jose Catre-Vandis on 2007-09-30
Running Edgy here so the deb won't install as it needs bluez-utils 3.9?

---

### Post by javaCachaca on 2007-10-10
Hi,
  The status bar of Blueman Bluetooth Manager show me the message:
       "No Adapters Found"

   But the command dmesg show-me:

[ 290.161259] powernow-k8: Found 2 AMD Turion(tm) 64 X2 Mobile Technology TL-52 processors (version 2.00.00)
[ 290.160736] powernow-k8: 0 : fid 0x8 (1600 MHz), vid 0x12
[ 290.160741] powernow-k8: 1 : fid 0x0 (800 MHz), vid 0x1e
[ 290.160991] powernow-k8: ph2 null fid transition 0x8
[ 295.453908] ppdev: user-space parallel port driver
[ 306.864914] vboxdrv: Trying to deactivate NMI watchdog permanently...
[ 306.864919] vboxdrv: Successfully done.
[ 307.302809] Bluetooth: Core ver 2.11
[ 307.302882] NET: Registered protocol family 31
[ 307.302884] Bluetooth: HCI device and connection manager initialized
[ 307.302889] Bluetooth: HCI socket layer initialized
[ 307.347007] Bluetooth: L2CAP ver 2.8
[ 307.347012] Bluetooth: L2CAP socket layer initialized
[ 307.376032] Bluetooth: RFCOMM socket layer initialized
[ 307.376047] Bluetooth: RFCOMM TTY layer initialized
[ 307.376049] Bluetooth: RFCOMM ver 1.8
[ 6271.326993] eth0: no IPv6 routers present

I have a notebook ASUS F3Tseries with Feisty (7.04)

How to enable/show my adapter ?

---

### Post by odzk on 2007-10-20
this one rocks. thanks alot for posting, ive been looking for this for decades

---

### Post by PmDematagoda on 2007-10-20
I was wondering when I would see a post like this:), I have used Blueman before and would recommend it for anyone who wants to get the maximum out of their bluetooth. 

Word of advice though, the "Browse" option still doesn't work properly and may very likely cause the OS to crash unless your file manager can access obex locations, but apart from that every thing is just great:).

---

### Post by paleozogt on 2007-11-09
As as 7.10 gutsy, blueman isn't in the repositories-- you can't use apt-get to install it and must download it from their webpage directly.  Why is this?  Furthermore, since blueman is so useful, why isn't it just included with the ubuntu distro by default?

---

### Post by paleozogt on 2007-11-09
I stand corrected... You *can* use apt-get.  I was searching for bluemon on packages.ubuntu.com and for some reason it's not showing up there, so I assumed it wasn't working for apt-get either.  I guess those two databases arent in synch. :confused:

Nevermind...

---

### Post by John Jason Jordan on 2007-11-13
Having read all the raves about blueman in this thread I decided to try it. It was listed in Synaptic in my Gutsy amd64 Thinkpad, so that's how I installed it. The installation went fine, but it did not install a launch entry item. From the command line I tried "blueman" but got "command not found." Then I tried "bluemon" and it took the command, the hard drive light flashed for a split second, and then nothing.

Stupid question: How do I launch it?

---

### Post by PmDematagoda on 2007-11-13
> **John Jason Jordan said:**
> Having read all the raves about blueman in this thread I decided to try it. It was listed in Synaptic in my Gutsy amd64 Thinkpad, so that's how I installed it. The installation went fine, but it did not install a launch entry item. From the command line I tried "blueman" but got "command not found." Then I tried "bluemon" and it took the command, the hard drive light flashed for a split second, and then nothing.

Stupid question: How do I launch it?

It seems that the install may not have gone well for you and by the way, there is no Blueman package on the repositories. I installed Blueman from the deb myself onto my Ubuntu 7.10 X64 OS and the menu entry was automatically made and the command is blueman and I have no problems concerning Blueman. Why don't you remove Blueman and install it using the deb again, maybe that could solve your problem. The deb can be found here:-

[http://blueman.tuxfamily.org/index.php?option=com_content&view=article&id=51&Itemid=56](http://blueman.tuxfamily.org/index.php?option=com_content&view=article&id=51&Itemid=56)

---

### Post by John Jason Jordan on 2007-11-13
> **PmDematagoda said:**
> It seems that the install may not have gone well for you and by the way, there is no Blueman package on the repositories. I installed Blueman from the deb myself onto my Ubuntu 7.10 X64 OS and the menu entry was automatically made and the command is blueman and I have no problems concerning Blueman. Why don't you remove Blueman and install it using the deb again, maybe that could solve your problem. The deb can be found here:-

[http://blueman.tuxfamily.org/index.php?option=com_content&view=article&id=51&Itemid=56](http://blueman.tuxfamily.org/index.php?option=com_content&view=article&id=51&Itemid=56)

Thanks. I did as you said and now it has a launch item under Applications > Accessories, and it appears to be working. I think the problem was that someone earlier in this thread typed it as "bluemon" and that is what I thought it was called. In fact, the "bluemon" in Synaptic is not the same thing. I don't know what it is, but it is unrelated to bluem*a*n.

Now to get a Sony DR-BT50 headset and see if I can get it working.

---

### Post by walmis on 2007-11-13
Try building the svn version, it's much more advanced. I need to iron out the remaining bugs until i can release the new deb though

---

### Post by John Jason Jordan on 2007-11-13
> **walmis said:**
> Try building the svn version, it's much more advanced. I need to iron out the remaining bugs until i can release the new deb though
I won't be able to acquire the DR-BT50 for a bit. I can get it from Amazon for $141 with free shipping, but their return policy sucks. However, I can get it from two local stores for $229 with 30-day return privilege and no questions asked. Unfortunately, both are located in distant suburbs, one without bus service. I plan to take my computer with me, buy the DR-BT50, walk out to the parking lot, and if it doesn't work, take it right back. But I can't do any of this until at least Friday, and maybe not until next week, as I have classes every day through Thursday, and a large project due Tuesday. Depending on my progress on the paper, I'll do it Friday, or Tuesday after I hand in the paper. 

I'd like to be able to report my findings on the DR-BT50 in either event, as I have googled all over and there is no report anywhere from a Linux user about it. Evidently Linux users don't buy stuff that has been out only a few months. Still, I have listened to these headphones played from a Sony Vaio with Vista, and the sound is awesome. Wired or unwired, you'd have to go a long way and spend a lot of money to find headphones that sound better. I really, really want them to work on my Gutsy amd64 laptop. However, the discussion of the DR-BT50 is getting off-topic for this thread, so I'll shut up now.

---

### Post by John Jason Jordan on 2007-11-17
> **John Jason Jordan said:**
> I'd like to be able to report my findings on the DR-BT50 in either event, as I have googled all over and there is no report anywhere from a Linux user about it. Evidently Linux users don't buy stuff that has been out only a few months. Still, I have listened to these headphones played from a Sony Vaio with Vista, and the sound is awesome. Wired or unwired, you'd have to go a long way and spend a lot of money to find headphones that sound better. I really, really want them to work on my Gutsy amd64 laptop. However, the discussion of the DR-BT50 is getting off-topic for this thread, so I'll shut up now.
Well, here is the report!

I bought the Sony DR-BT50 headphones at a store where I have 30 days to return them. Using blueman I got them paired up. Using Services > Headset Connection I entered the passkey according to the manual that came with the headphones, and it worked. 

That's the good news. The bad news is that I can't get sound to come out of the headphones instead of out of the laptop speakers. If I open the volume control in the gnome panel and go to File > Change Devices it now lists "BT Headset Alsa Mixer." Choosing that I turned the Master and Microphone all the way up, but still nothing out of the headphones. 

I'm pretty sure the DR-BT50 headphones will work fine with my Gutsy amd64 laptop, just as soon as I figure out how to direct the sound to the headphones instead of the speaker. At least the bluetooth in the laptop connects to the headphones just fine.

I have heard these headphones in a Sony store played from a Sony Vaio computer running Vista. The sound  quality is awesome. I can't wait to listen to stereo with these things! If anyone has any suggestions for how to get the sound to the headphones instead of the speakers, please let me know!

---

### Post by John Jason Jordan on 2007-11-18
Follow-up on how I got sound out of my new Sony DR-BT50 bluetooth headphones. Bluetooth is working fine and I managed to get the headphones paired up using Blueman. Blueman is not in the Ubuntu repositories, but you can download it and install it with Gdebi. However, although I got the headphones paired up fine, for a long time I couldn't get sound (e.g., from Rhythmbox) out of the headphones instead of the speakers or the headphone jack. I found the secret here:

[http://wiki.bluez.org/wiki/HOWTO/AudioDevices#Alsaconfiguration](http://wiki.bluez.org/wiki/HOWTO/AudioDevices#Alsaconfiguration)

I had to make a file ~/.asoundrc and put into it:

pcm.bluetooth {
	type bluetooth
	device 00:13:A9:B2:82:5F
}

Where the device is the address listed in Blueman. 

After getting the headphones paired up I found another item in the volume control dialog box. Previously under File > Change Device it listed "HDA Intel (Alsa mixer)" and "Analog Devices AD1984 (OSS Mixer)." Now there is a new one, "BT Headset (Alsa Mixer)." After checking it and making the .asoundrc file the headphones are working perfectly. The sound from these headphones is awesome. If you are a serious music fan you won't be disappointed.

I also have the volume buttons working (since flashing the BIOS). They work fine for controlling the sound from the speakers and the headphone jack, but they don't have any effect on the headphones. Oh well, the volume controls on the headphones work fine, and that is all I need.

---

### Post by imon9 on 2007-11-19
sorry guys, just wanna ask something:

if i have a bluetooth headset and a wacom bluetooth tablet, will both work simultanouesly?
my laptop have built-in bluetooth.

btw, do we need driver for bluetooth stuff like headset & tablet?

---

### Post by John Jason Jordan on 2007-11-20
> **imon9 said:**
> if i have a bluetooth headset and a wacom bluetooth tablet, will both work simultanouesly? my laptop have built-in bluetooth. btw, do we need driver for bluetooth stuff like headset & tablet?
Theoretically, both will work simultaneously. I think the limit is eight devices, but I may have misremembered that.

You should need no drivers as long as the devices are bluetooth compliant. I recommend installing the Blueman utility, as it's a big help.

---

### Post by hydraconsole on 2007-11-24
> **PmDematagoda said:**
> It seems that the install may not have gone well for you and by the way, there is no Blueman package on the repositories. I installed Blueman from the deb myself onto my Ubuntu 7.10 X64 OS and the menu entry was automatically made and the command is blueman and I have no problems concerning Blueman. Why don't you remove Blueman and install it using the deb again, maybe that could solve your problem. The deb can be found here:-

[http://blueman.tuxfamily.org/index.php?option=com_content&view=article&id=51&Itemid=56](http://blueman.tuxfamily.org/index.php?option=com_content&view=article&id=51&Itemid=56)

Hi, i'm a newbie here. i've downloaded the deb. how do i install it?

thanks

---

### Post by John Jason Jordan on 2007-11-25
> **hydraconsole said:**
> Hi, i'm a newbie here. i've downloaded the deb. how do i install it?
Right click on it, then "install with GDebi package installer."

---

### Post by Fredrik_b on 2007-11-30
Hi I get this error message when trying to connect an BT headset.

```
(blueman:8211): CRITICAL **: dbus_g_proxy_disconnect_signal: assertion `DBUS_IS_G_PROXY (proxy)' failed
```

what can be wrong?

---

### Post by Hashte on 2007-12-07
> **hydraconsole said:**
> Hi, i'm a newbie here. i've downloaded the deb. how do i install it?

thanks

PEOPLE, what deb are you talking about? There's no deb file on that page?:confused:
How can i get it installed? I add the repository, but when I enter the code for importing the GPG key into the terminal, it just download something and goes no further...

Please help me:(!

---

### Post by walmis on 2007-12-09
You need to enter your sudo password

---

### Post by hodge24 on 2007-12-09
Hi all,

I've got GPRS Easy Connect etc. installed, and it seems to work (fantastically!) 70% of the time. The rest of the time, unfortunately, it causes my system (Gnome/X Server) to crash. It happens when the "have you switched on your mobile?" message appears, when it can't connect, so I presume it's something to do with Gnome/X struggling to render the dialog correctly.

Has anyone else experienced this?

I'm running Ubuntu Gutsy (7.10) 64 bit, on an Acer Aspire 5052

---

### Post by walmis on 2007-12-09
i've had this problem too.

---

### Post by Paul In SF on 2007-12-31
> **John Jason Jordan said:**
> Follow-up on how I got sound out of my new Sony DR-BT50 bluetooth headphones. Bluetooth is working fine and I managed to get the headphones paired up using Blueman. Blueman is not in the Ubuntu repositories, but you can download it and install it with Gdebi. However, although I got the headphones paired up fine, for a long time I couldn't get sound (e.g., from Rhythmbox) out of the headphones instead of the speakers or the headphone jack. I found the secret here:

[http://wiki.bluez.org/wiki/HOWTO/AudioDevices#Alsaconfiguration](http://wiki.bluez.org/wiki/HOWTO/AudioDevices#Alsaconfiguration)

I had to make a file ~/.asoundrc and put into it:

pcm.bluetooth {
	type bluetooth
	device 00:13:A9:B2:82:5F
}

Where the device is the address listed in Blueman. 

After getting the headphones paired up I found another item in the volume control dialog box. Previously under File > Change Device it listed "HDA Intel (Alsa mixer)" and "Analog Devices AD1984 (OSS Mixer)." Now there is a new one, "BT Headset (Alsa Mixer)." After checking it and making the .asoundrc file the headphones are working perfectly. The sound from these headphones is awesome. If you are a serious music fan you won't be disappointed.

I also have the volume buttons working (since flashing the BIOS). They work fine for controlling the sound from the speakers and the headphone jack, but they don't have any effect on the headphones. Oh well, the volume controls on the headphones work fine, and that is all I need.

How do I make that file, and where do I put it?  Answer in format suitable for dummies much appreciated!

---

### Post by olavjunior on 2008-01-03
I get this error: ```
Traceback (most recent call last):
  File "/usr/bin/blueman", line 159, in <module>
    Globals.main_list = main_list(xml)
  File "/usr/lib/python2.5/site-packages/blueman/Gui/main_list.py", line 75, in __init__
    sw.add(self)
AttributeError: 'NoneType' object has no attribute 'add'

```

I've installed the svn. Any ideas?

---

