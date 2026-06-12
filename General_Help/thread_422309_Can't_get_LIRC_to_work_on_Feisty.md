---
title: "Can't get LIRC to work on Feisty"
date: 2007-04-25
forum: General Help
---

### Post by tranquillion on 2007-04-25
Hi,

I followed the instructions at [https://help.ubuntu.com/community/Install_Lirc_Feisty](https://help.ubuntu.com/community/Install_Lirc_Feisty) to install LIRC for my Hauppauge remote. However, when I start irw for testing purposes, irw is exiting right away, so according to the instructions some modules are not loading correctly. The relevant lines from dmesg are:
```
[   50.156492] lirc_dev: IR Remote Control driver registered, at major 61
[   50.172942] lirc_pvr150: no version for "lirc_unregister_plugin" found: kernel tainted.
[   50.218763] lirc_pvr150: chip found with RX and TX
[   50.219440] lirc_dev: lirc_register_plugin: sample_rate: 0
[   50.231127] lirc_pvr150: firmware haup-ir-blaster.bin not available (-2)

```
I'm not planning to use the IR blaster, but I don't know if the missing firmware causes the module to fail. Any pointers would be appreciated!

Thanks
Klaus

---

### Post by superm1 on 2007-04-25
If you aren't planning to use the blaster, there is no need to build the pvr150 module.  Just need the lirc_i2c module.  Rebuild with just that and you should be fine.

---

### Post by tranquillion on 2007-04-26
Ok, thanks; I removed pvr150 in both the dpkg-reconfigure dialog, and in /etc/lirc/hardware.conf.  Now the only lirc-related message I see in dmesg is 

[   53.879014] lirc_dev: IR Remote Control driver registered, at major 61 

However, irw still exits immediately... any suggestions where to look for the problem?

Thanks
Klaus

---

### Post by superm1 on 2007-04-26
> **tranquillion said:**
> Ok, thanks; I removed pvr150 in both the dpkg-reconfigure dialog, and in /etc/lirc/hardware.conf.  Now the only lirc-related message I see in dmesg is 

[   53.879014] lirc_dev: IR Remote Control driver registered, at major 61 

However, irw still exits immediately... any suggestions where to look for the problem?

Thanks
Klaus
You should still be getting a lirc_i2c module loading, can you attempt to modprobe it.

```
sudo modprobe lirc_i2c
```

---

### Post by tranquillion on 2007-04-26
> **superm1 said:**
> You should still be getting a lirc_i2c module loading, can you attempt to modprobe it.

```
sudo modprobe lirc_i2c
```

Oh, maybe I've read the instructions at [https://help.ubuntu.com/community/Install_Lirc_Feisty]("https://help.ubuntu.com/community/Install_Lirc_Feisty")  wrong! I took the MODULES line literally from the instructions for the pvr-150 on-card blaster and added only lirc-dev and lirc-pvr150. Now I realize that this probably activates *only* the blaster, and I should also have lirc-i2c in there. Is that correct?

I'll try this when I get home...

Thanks
Klaus

---

### Post by tranquillion on 2007-04-26
Or is this a simple misprint in the instructions? Should the line in /etc/lirc/hardware.conf read
```
MODULES="lirc_i2c lirc_pvr150"
```?

Klaus

---

### Post by superm1 on 2007-04-26
It should be

MODULES="lirc_i2c" 
if you don't need the blaster.

MODULES="lirc_i2c lirc_pvr150"
if you do need the blaster.

---

### Post by tranquillion on 2007-04-26
> **superm1 said:**
> It should be

MODULES="lirc_i2c" 
if you don't need the blaster.

MODULES="lirc_i2c lirc_pvr150"
if you do need the blaster.

Thanks! I've updated the documentation.

Klaus

---

### Post by cmchugh on 2007-05-02
I also got stuck at the point where irw does not work as described in the guide. I fixed it by quiting lircd if it is running (note that if you try to run irw and it returns with no response, it will also stop lircd if is running). Then I  did the following:

sudo ln -s /etc/lirc/lircd.conf /etc/lircd.conf

Then start lircd with:

sudo lircd -d /dev/lirc/0

the irw command should now work as expected and you can continue with the procedure.

Lircd will have to be started using the sudo lircd -d /dev/lirc/0 command after a reboot unless you get it to load that way at boot.

I found most of this information at:

[http://forum.byopvr.com/dvr/index.php/topic,2819.msg14297.html](http://forum.byopvr.com/dvr/index.php/topic,2819.msg14297.html)

I don't know if this will work for everyone  but it worked for me in edgy and feisty...

---

### Post by superm1 on 2007-05-03
> **cmchugh said:**
> I also got stuck at the point where irw does not work as described in the guide. I fixed it by quiting lircd if it is running (note that if you try to run irw and it returns with no response, it will also stop lircd if is running). Then I  did the following:

sudo ln -s /etc/lirc/lircd.conf /etc/lircd.conf

Then start lircd with:

sudo lircd -d /dev/lirc/0

the irw command should now work as expected and you can continue with the procedure.

Lircd will have to be started using the sudo lircd -d /dev/lirc/0 command after a reboot unless you get it to load that way at boot.

I found most of this information at:

[http://forum.byopvr.com/dvr/index.php/topic,2819.msg14297.html](http://forum.byopvr.com/dvr/index.php/topic,2819.msg14297.html)

I don't know if this will work for everyone  but it worked for me in edgy and feisty...
If you are stuck using these workarounds, then you don't have the init script from the ubuntu lirc package installed.  You are using an init script from a source tgz typically.

---

### Post by cmchugh on 2007-05-03
> **superm1 said:**
> If you are stuck using these workarounds, then you don't have the init script from the ubuntu lirc package installed.  You are using an init script from a source tgz typically.

Well, I followed the procedure  at [https://help.ubuntu.com/community/Install_Lirc_Feisty](https://help.ubuntu.com/community/Install_Lirc_Feisty) and lircd would start at boot, but it would not work, and running irw would kill it. Don't know why...

If anyone knows any good docs on using lirc with mythtv and a digital set-top box (Motorola dct1700)  using a pvr-3560 card, please let me know.

Thanks

---

### Post by Blackie_Chan on 2007-05-04
**ATI Remote Wonder & Lirc Working**

I finally got lirc to work properly on my machine. I have an ATI Remote Wonder, and I followed the instructions on [https://help.ubuntu.com/community/Install_Lirc_Edgy](https://help.ubuntu.com/community/Install_Lirc_Edgy) which didn't work for me (I kept getting could not open /dev/lirc in /var/log/syslog)

Then I found out from googling that the modules: ati_remote and lirc_atiusb do not play together so I did the following 

Renamed ati_remote.ko and ati_remote2.ko
```
user@ubuntu:~$ cd /lib/modules/2.6.20-15-generic/kernel/drivers/usb/input
user@ubuntu:/lib/modules/2.6.20-15-generic/kernel/drivers/usb/input$ sudo mv ati_remote.ko ati_remote.ko-disabled
user@ubuntu:/lib/modules/2.6.20-15-generic/kernel/drivers/usb/input$ sudo mv ati_remote2.ko ati_remote2.ko-disabled

```

Updated the modules list (I don't know if it's neccessary)
```

user@ubuntu:/lib/modules/2.6.20-15-generic/kernel/drivers/usb/input$ sudo depmod -a 
```

Then I rebooted. After reboot lircd was running successfully. 

```

user@ubuntu:~$ ps auxw | grep lircd
root      5099  0.0  0.1   2880   564 ?        Ss   23:35   0:00 /usr/sbin/lircd --device=/dev/lirc0

```

Source: [http://mythtv.org/pipermail/mythtv-users/2005-February/076556.html](http://mythtv.org/pipermail/mythtv-users/2005-February/076556.html)

---

### Post by direwolf08 on 2007-06-04
Hi, I am new to these forums.  

I also am having a similar problem, where I can start lirc, but irw kills it (I am using an MCE remote and usb IR receiver).  

When I see type: 
```
ls /dev/lirc*
```  

all I have is a lircd file, no lirc or lirc0 (even when the lirc deamon is running via the sudo /etc/init.d/lirc command)

Here is what I have in dmesg:
```
[   36.500000] lirc_dev: IR Remote Control driver registered, at major 61 
[   36.504000] lirc_mceusb2: no version for "lirc_get_pdata" found: kernel tainted.
[   36.508000] 
[   36.508000] lirc_mceusb2: Philips eHome USB IR Transciever and Microsoft MCE 2005 Remote Control driver for LIRC $Revision: 1.25 $
[   36.508000] lirc_mceusb2: Daniel Melander <lirc@rajidae.se>, Martin Blatter <martin_a_blatter@yahoo.com>

```

---

### Post by hazica on 2007-06-07
Hello, direwolf8.

I also use the MCE remote with the USB IR receiver and I used to have the same issue as you do.
My output of dmesg was identical with yours.

How I solved the problem? I switched the ir sensor to an usb 2.0 port. And it worked.

Hope this helps.

---

### Post by lingenfr on 2007-09-19
I went back through the installation. I assume a kernel upgrade hosed the previous one. I followed the directions here:

[https://help.ubuntu.com/community/Install_Lirc_Feisty](https://help.ubuntu.com/community/Install_Lirc_Feisty)

What started me on the upgrade quest in the first place was that the guide quit working. I found out why here:

[http://forums.gentoo.org/viewtopic-t-580340.html?sid=f8e1e6eaf1f8067f8e2ad6b7574e3122](http://forums.gentoo.org/viewtopic-t-580340.html?sid=f8e1e6eaf1f8067f8e2ad6b7574e3122)

I am signing up for schedulesdirect. I would have gladly paid them without this hassle. Crap like this with the guide and lirc make it hard to sell these project to spouses.

---

### Post by superm1 on 2007-09-19
> **lingenfr said:**
> I went back through the installation. I assume a kernel upgrade hosed the previous one. I followed the directions here:

[https://help.ubuntu.com/community/Install_Lirc_Feisty](https://help.ubuntu.com/community/Install_Lirc_Feisty)

What started me on the upgrade quest in the first place was that the guide quit working. I found out why here:

[http://forums.gentoo.org/viewtopic-t-580340.html?sid=f8e1e6eaf1f8067f8e2ad6b7574e3122](http://forums.gentoo.org/viewtopic-t-580340.html?sid=f8e1e6eaf1f8067f8e2ad6b7574e3122)

I am signing up for schedulesdirect. I would have gladly paid them without this hassle. Crap like this with the guide and lirc make it hard to sell these project to spouses.
Do note that 0.20.2 is on feisty-updates and edgy-updates for universe.

---

### Post by NeoFax on 2007-10-03
I have tried most LIRC tutorials including the Ubuntu WIKI provided one to no avail.  irw exits immediately and the KDE lirc server never registers a lirc server.  The instructions inside the /etc/lirc/hardware.conf file does not work either a they say you can put /dev/lirc in the devices string and devfs will register the lirc device at /dev/lirc/0 which never happens.  However, for some miraculous reason some of the remotes keys work and some do not.  I would like to be able to click on a key and then tell lirc the corresponding key sequence to send based off of this key press.  Any help would be greatly appreciated. :(

---

### Post by suffice on 2007-10-13
I have to use that command {sudo lircd -d /dev/lirc0 }after reboot too, which for me is fine, but if my girl has to do it, its just not going to work out, so i want to set up a script to run it at startup......

im not sure how to use a sudo in a script, ive seen someone say at it so some sudoers dir, or use it without sudo in the script, or run it as sudo, but its still going to be placed in >sessions> and would need a password...

any ideas?

> **cmchugh said:**
> I also got stuck at the point where irw does not work as described in the guide. I fixed it by quiting lircd if it is running (note that if you try to run irw and it returns with no response, it will also stop lircd if is running). Then I  did the following:

sudo ln -s /etc/lirc/lircd.conf /etc/lircd.conf

Then start lircd with:

sudo lircd -d /dev/lirc/0

the irw command should now work as expected and you can continue with the procedure.

Lircd will have to be started using the sudo lircd -d /dev/lirc/0 command after a reboot unless you get it to load that way at boot.

I found most of this information at:

[http://forum.byopvr.com/dvr/index.php/topic,2819.msg14297.html](http://forum.byopvr.com/dvr/index.php/topic,2819.msg14297.html)

I don't know if this will work for everyone  but it worked for me in edgy and feisty...

---

