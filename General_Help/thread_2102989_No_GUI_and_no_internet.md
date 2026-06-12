---
title: "No GUI and no internet"
date: 2013-01-08
forum: General Help
---

### Post by tabarnak on 2013-01-08
I dual boot 12.10 with Windows 8 on a UEFI system. The other day, I was installing some python stuff when apt-get suggested I run a dpkg command (I have no familiarity with how dpkg works), and that appeared to mess everything up on the next reboot.

I booted into Ubuntu only to find no GUI. I then ran startx, which told me it could not start the server and that no screens were found. I then looked at the logs and determined that my graphics drivers were gone; fglrxinfo yielded "no command found".

When I ran sudo apt-get install fglrx fglrx-amdcccle, apt responded with Could not resolve us.archive.ubuntu.com. Doing ping google.com, ping 72.14.207.99, and ifconfig all seem to confirm the fact that I was not connected to the internet.

I'm not sure what to do now. I'm not too familiar with UNIX/Linux networking or graphics. I don't have any updates to roll back to, but my Ubuntu installation is fairly new. Ideally, I want to fix my issues in place, without having to resort to a live CD/USB.

I have integrated graphics: AMD Radeon HD 7660G.

Any help is appreciated! :)

---

### Post by ScottDeagan on 2013-01-08
Could you ping us.archive.ubuntu.com? I tried from here in the UK and was able to ping it:

```

scott@scott-700Z7C:~/workspace/cpp_projects$ ping us.archive.ubuntu.com
PING us.archive.ubuntu.com (91.189.91.15) 56(84) bytes of data.
64 bytes from likho.canonical.com (91.189.91.15): icmp_req=1 ttl=47 time=89.5 ms
64 bytes from likho.canonical.com (91.189.91.15): icmp_req=2 ttl=47 time=89.1 ms
64 bytes from likho.canonical.com (91.189.91.15): icmp_req=3 ttl=47 time=90.0 ms

```

Perhaps those servers and currently experiencing problems, you could always try in another 30 minutes or an hour (not very helpful, sorry).

I don't have much experience with AMD drivers (but I'm planning on trying a Radeon GPU in my desktop soon). The only other thing I can suggest is you try to download and install the AMD Catalyst drivers directly from AMD. There are a number of posts that explain how to do this:

[http://www.upubuntu.com/2012/10/install-amd-catalyst-1210-driver-on.html](http://www.upubuntu.com/2012/10/install-amd-catalyst-1210-driver-on.html)

(just be very careful!)

---

### Post by kaushikgaurav on 2013-01-08
try this

sudo service lightdm start

---

### Post by d4rk0wl on 2013-01-08
If attempting the ^ above command ^ does not work you might need to generate a new xorg.conf file. Ubuntu does not create one by default but perhaps somehow during configuration of the AMD drivers it might of.
Log into the command line and type:
```
sudo X -configure
```
this will generate a new xorg.conf in your home directory, now you just need to move it to /etc/
```
sudo mv xorg.conf /etc/x11/
```Also, what was the command that dpkg asked you to run? That could help a bunch too.

Regards,
- D4rk0wl

---

### Post by tabarnak on 2013-01-08
Starting lightdm doesn't work. It freezes in the middle of starting. There is definitely no network access.

Will try generating a new xorg.conf.

---

### Post by tabarnak on 2013-01-08
The command I ran before this mess happened was dpkg --configure -a.

I tried sudo X -configure, only to get "number of created screens does not match number of determined devices".

---

### Post by kaushikgaurav on 2013-01-08
do you have dual monitor?
try this

sudo amdconfig --initial -f

For Installing Proprietary Drivers a.k.a. Catalyst/fglrx: [http://wiki.cchtml.com/index.php/Ubuntu_Quantal_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Quantal_Installation_Guide")

---

### Post by tabarnak on 2013-01-09
I only have one monitor. In fact, I think it's not detecting any screens. In any case, the driver simply doesn't appear to be there. I will try amdconfig and see if it works.

---

### Post by tabarnak on 2013-01-09
amdconfig does not work. Would be nice to have internet so I can reinstall the display driver...

---

### Post by Luigi2012SM64DS on 2013-01-09
Maybe a reinstall?

---

### Post by steeldriver on 2013-01-09
well I guess you could try to bring up your wired interface manually - either by editing /etc/network/interfaces and restarting the networking service, or using ifconfig - although apparently ifconfig has been deprecated in favor of 'ip' so you could try something like

```
sudo dhclient eth0
sudo ip link set dev eth0 up
```(that's assuming you are connected to a router with a working DHCP server). If that works you should be able to ping remote hosts at least by IP - if you still can't ping by name at that point you would need to add a nameserver, after that you should be able to pull down the replacement drivers

---

### Post by tabarnak on 2013-01-09
> Maybe a reinstall?

I would prefer not to do this. If I have to, I would prefer to do this in place, and without affecting GRUB. I am (was) running Secured-Remix on a UEFI secure boot system that didn't behave very well for a short while after Ubuntu installation, and I definitely don't want to repeat the process and the anxiety associated with it.

---

### Post by tabarnak on 2013-01-10
Tried sudo dpkg-reconfigure xserver-xorg to no avail.

---

### Post by tabarnak on 2013-01-10
Bit the bullet and reinstalled. Not worth the time in trying to figure out how to solve this issue. Anyways I still appreciate the help.

---

### Post by d4rk0wl on 2013-01-10
What about attempting to restart gdm3?
```
sudo service gdm3 restart
```

Also, as far as the network issue goes, could you tell us the output of:
```
ifconfig eth0
```

Regards,
- D4rk0wl

---

### Post by tabarnak on 2013-01-10
@d4rk0wl

I wiped my Ubuntu partition (could not reinstall due to installer bug) and did a clean install. 

Regardless, I appreciate everyone's assistance.

---

