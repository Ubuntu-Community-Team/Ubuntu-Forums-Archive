---
title: "NdisWrapper - How to??"
date: 2004-10-30
forum: General Help
---

### Post by Pjeir on 2004-10-30
Hello!
Yesterday I've installed Ubuntu and I'm completely new to Linux and Ubuntu. Everything seems to work fine for now, except I can't get NdisWrapper to work. I need it because I have a wireless network card which isn't recognized during Ubuntu installation, so I don't have internet access for now. I downloaded ndiswrapper-0.11.tar.gz and the driver for my card (SMC 2635W) on another system (winXP), and I wrote NdisWrapper and the INF-file on a cdrom. This is where I'm starting to get stuck. I try to follow the instructions from [How To - Set up Ndiswrapper](http://www.ubuntulinux.org/support/documentation/howto/helpcenterhowto.2004-10-07.7773155363), but the first 2 already are a little bit too hard.
> # Fire Up synaptic or whatever you like to use and update your repository.
# Install the packages "ndiswrapper-utils" and "linux-image-2.6.8.1-3-386"
In synaptic it seems the linux-image files are already installed, but I can't find the ndiswrapper-utils anywhere. Where do I go from here?

Many thanks!

---

### Post by JConnell on 2004-10-30
Hi Pjeir :)

Here is how I would accomplish this task:

**1)** Install ndiswrapper-utils:

pjier@ubuntu:~ $ sudo apt-get install ndiswrapper-utils

**2)** Burn any .inf files and any other files (especially .sys) that were in the driver .zip file to your cdrom. (It sounds like you copied only the .inf?)

**3)** Make sure your SMC 2635W is inserted, then install the driver:
```

pjeir@ubuntu:~ $ sudo ndiswrapper -i /mnt/cdrom/blah.inf

```
**4)** Check to see if it installed properly:
```

pjeir@ubuntu:~ $ ndiswrapper -l

```
**5)** Install the ndiswrapper module
```

pjeir@ubuntu:~ $ sudo modprobe ndiswrapper

```
**6)** Configure your card

Computer->System Configuration->Networking
or
gedit /etc/network/interfaces

---

### Post by Pjeir on 2004-10-31
I'm sorry, but I'm completely new to all of this and I still seem to be doing something wrong. When I try "sudo apt-get install ndiswrapper-utils" from the terminal it gives this error: (translated) "Couldn't find packet ndiswrapper-utils". What am I doing wrong here? Thanks.

---

### Post by Pjeir on 2004-11-01
Please someone help me out on this one! It can't be too hard, and once I have internet on my laptop I can start sorting these things out myself. What do I have to do to install ndiswrapper? Thanks!

---

### Post by Enygma on 2004-11-01
You can't apt-get it because you need internet access first. And you can't get internet access without the wireless card. 

I downloaded the ndiswrapper-utils package from here:
[http://archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/](http://archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/)

I guess you need all the files in that directory. 

When you've got those files install the utils by doing 
'sudo dpkg -i  ndiswrapper-utils_0.10-1_i386.deb'

This should install it in the same way apt-get would have.
Now follow the instructions as per the HOWTO.

This worked fine for me.

---

### Post by hyde on 2004-11-01
Hi!

I've wlan card which is not supported by the kernel, so I needed also ndiswrapper.

Switch to consol and type *lspci* and you should find line something like this:
*0000:02:00.0 Network controller: Broadcom Corporation BCM94306 802.11g (rev 03)*
This reveals your wlan chipset. I have Broadcom chipset, as you can see. 

I had to take my lappie with me and walk to my bedroom, where my ADSL modem and AirStation lives. I found network cable and plugged it in. Now I'm not sure if ndiswrapper was there already or not...? I think it wasn't there, so I probably loaded it via Synaptic Package Manager and have it installed. I needed my internet connection to load Windows XP drivers for my card (didn't found it on XP filesystem..?)

Then I copied the bcmwl5.inf and *.sys files to my home directory. Then I got into root console and wrote *ndiswrapper -i bcmwl5.inf *, then* modprobe ndiswrapper *.

At this point I made new network connection; Computer-> System Configuration->Networking. There "Add", "Wireless", wrote "wlan0" to Wireless device, you probably know your networks name and WEP key, type them in. Now you should have configured your wireless network. 

Now it is time to kick your wlan card into action; go back to root console and write *ifup wlan0*. You should see some messages on screen. Hopefully not any errors. Check is your connection working, open Firefox and try, or ping your router etc.

If everything is working fine (as it shoud), go to root console and write* ndiswrapper -m *

Then add line ndiswrapper to your /etc/modules file. This will start your wlan on bootup.

I did it pretty much like this and it worked out well. Hope you can make it too.
Look instructions on [http://ndiswrapper.sourceforge.net/wiki/index.php/Installation](http://ndiswrapper.sourceforge.net/wiki/index.php/Installation) if you need more help.

---

