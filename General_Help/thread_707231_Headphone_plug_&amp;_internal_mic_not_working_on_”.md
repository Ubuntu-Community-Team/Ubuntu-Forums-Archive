---
title: "Headphone plug &amp; internal mic not working on ”Acer Aspire 4315”"
date: 2008-02-25
forum: General Help
---

### Post by ostekongen on 2008-02-25
I am running Ubuntu 7.10 on my Acer 4315.  My sound card seem to be working fine and i get sound from the build in speakers. But when i plug in headphones in the mini jack in I still get sound from the speakers and no sound from the headphones.

Furthermore the build in mic does not seem to work. 

[QUOTE="lspci"]00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Contoller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8039 PCI-E Fast Ethernet Controller (rev 15)
04:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)[/QUOTE]

Thanks for your help!

---

### Post by ostekongen on 2008-02-25
Okay...

```
sudo apt-get install linux-backports-modules-generic
```

...installing the alsa-driver-1.0.15, seemed to do the trick. I now have the option of "Headphone" in the mixer panel. However the volume level from the headphone-out is _very low_ and when I plug in a headphone... sound still comes out the laptop speakers?

---

### Post by matiasgatti on 2008-03-02
Y try what you said, and now i have output sound but very low volume.

But the microphone still doesn't work..


Anyone have the same problem? and SOLUTION ? 


Thanks in advanced

---

### Post by hyperandy on 2008-03-16
I have an Acer 4720Z with a 
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)

My sound was working after building alsa drivers from source but my mic was not working in the sound recorder or skype

I had to add a line to rc.local
I ran:
sudo gedit /etc/rc.local

and I added 
amixer set 'Capture' cap

above the exit 0 line!
then I ran: 
sudo shutdown -r 0

to reboot the computer

Then I double clicked on my volume icon to bring up the sound mixer and 
went to edit --> prefs --> and checked "input source"
it then made an "options" tab on my mixer panel and I selected "Front Mic"
and after that both Skype and the sound recorder worked! Good luck!

---

### Post by Nidding on 2008-03-27
Sorry if this is a really lame question, but how do I build the alsa drivers from source? 

...yes, I'm a total newbie to Linux, so please lend a hand. A link to a how to, would be just fine ;)

---

### Post by hyperandy on 2008-04-03
#######From a post by felipefoz on an earlier post#######

Sound - High Definition Audio

You might be asking yourselves, why installing sound before video. I don't know why, but installing sound after the video may break nvida installation. ???? . So let's do the sound before the video. The solution is simple, downloading latest alsa drivers and compiling them. "Question: I've seen an alternative solution with ubuntu's "linux-backport-modules", isn't easier?". Actually, that solution is pretty quicker than this one, but with that one, the microphone was not working with me, so I compiled it myself.
This tip I got partially from [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto). And also from another thread here in forums [http://ubuntuforums.org/showthread.php?t=577699](http://ubuntuforums.org/showthread.php?t=577699)
I am passing all the process here, but at the end I have made some modifications in the script from this post [http://ubuntuforums.org/showpost.php...2&postcount=13](http://ubuntuforums.org/showpost.php...2&postcount=13), and you may want to download to automate the process. Then you should run these steps.
Code:

sudo sh alsa_1.sh
reboot
sudo sh alsa_2.sh
reboot

Sound should be working, I used this script and worked very well.
Otherwise you may want to do it manually. With the following steps.

Install dependencies:
Code:

 apt-get install build-essential libncurses5-dev gettext linux-headers-`uname -r`

Alsa Driver, Lib and Utils:
Code:

wget [ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.16.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.16.tar.bz2)
wget [ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.16.tar.bz2](ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.16.tar.bz2)
wget [ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.16.tar.bz2](ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.16.tar.bz2)

Extracting them and removing tarballs:
Code:

tar -xjf alsa-driver*.tar.bz2
tar -xjf alsa-lib*.tar.bz2
tar -xjf alsa-utils*.tar.bz2
rm alsa*.tar.bz2

Making the directory for compiling the source:
Code:

sudo mkdir -p /usr/src/alsa
sudo mv alsa-* /usr/src/alsa

Compiling and installing alsa-driver
Code:

cd /usr/src/alsa/alsa-driver*
sudo ./configure --with-cards=hda-intel
sudo make
sudo make install

Compiling and installing alsa-libs
Code:

 cd /usr/src/alsa/alsa-lib*
sudo ./configure
sudo make
sudo make install

Compiling and installing alsa-utils
Code:

cd /usr/src/alsa/alsa-utils*
sudo ./configure
sudo make
sudo make install

Reboot the machine and run more these comands:
Code:

sudo cp -v /lib/modules/2.6.22-*/kernel/sound/pci/hda/snd-hda-intel.ko /lib/modules/2.6.22-*/ubuntu/media/snd-hda-intel/snd-hda-intel.ko
sudo cp -v /usr/src/alsa/alsa-driver*/modules/* /lib/modules/2.6.22-*/kernel/sound/
sudo depmod -a

Reboot once more. And the next time will have sound working, no extra tweaks needed, like adding some line to /etc/modprobe.d/alsa-base. The steps above must solve the problem with sound and mic. The mic will work after enabling all boxes in the Gnome mixer applet. Change the input source to "front mic" or "mic" depending on which microphone you are gonna use. That's it.

---

### Post by The Dig on 2008-04-20
> **hyperandy said:**
> I have an Acer 4720Z with a 
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)

My sound was working after building alsa drivers from source but my mic was not working in the sound recorder or skype

I had to add a line to rc.local
I ran:
sudo gedit /etc/rc.local

and I added 
amixer set 'Capture' cap

above the exit 0 line!
then I ran: 
sudo shutdown -r 0

to reboot the computer

Then I double clicked on my volume icon to bring up the sound mixer and 
went to edit --> prefs --> and checked "input source"
it then made an "options" tab on my mixer panel and I selected "Front Mic"
and after that both Skype and the sound recorder worked! Good luck!


Many  many thanks for this, the machine mic  / skype on my Acer aspire 7720 is now working   =D>  switch to front mic in (options) see above, and an earpiece mic plugged in the front of the machine  pink / black jacks also works, I,m playing with a usb headset currently.

---

### Post by Coolhand_EL on 2008-04-26
hyperandy FTW!!!

I have 64 bit Hardy running on an Acer Aspire 5580 laptop. The audio chip is:

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

Your instructions worked like a charm on the internal mic!

---

### Post by Coolhand_EL on 2008-04-26
> **hyperandy said:**
> I have an Acer 4720Z with a 
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)

My sound was working after building alsa drivers from source but my mic was not working in the sound recorder or skype

I had to add a line to rc.local
I ran:
sudo gedit /etc/rc.local

and I added 
amixer set 'Capture' cap

above the exit 0 line!
then I ran: 
sudo shutdown -r 0

to reboot the computer

Then I double clicked on my volume icon to bring up the sound mixer and 
went to edit --> prefs --> and checked "input source"
it then made an "options" tab on my mixer panel and I selected "Front Mic"
and after that both Skype and the sound recorder worked! Good luck!

Was refering to this instruction - I didn't need to recompile anything... :)

---

### Post by blakesle on 2008-04-26
> **hyperandy said:**
> I have an Acer 4720Z with a 
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)

My sound was working after building alsa drivers from source but my mic was not working in the sound recorder or skype

I had to add a line to rc.local
I ran:
sudo gedit /etc/rc.local

and I added 
amixer set 'Capture' cap

above the exit 0 line!
then I ran: 
sudo shutdown -r 0

to reboot the computer

Then I double clicked on my volume icon to bring up the sound mixer and 
went to edit --> prefs --> and checked "input source"
it then made an "options" tab on my mixer panel and I selected "Front Mic"
and after that both Skype and the sound recorder worked! Good luck!

Thank you!!!

This worked and I now have a mic for Skype!

---

### Post by Simon Bridge on 2008-05-01
@ostekongen: how goes that 4315 - all the solutions I see are for other models.

Have you seen:
[http://www.hbclinux.net.nz/acer4315.html](http://www.hbclinux.net.nz/acer4315.html)

---

### Post by Nidding on 2008-05-01
> **hyperandy said:**
> #######From a post by felipefoz on an earlier post#######

Sound - High Definition Audio

You might be asking yourselves, why installing sound before video. I don't know why, but installing sound after the video may break nvida installation. ???? . So let's do the sound before the video. The solution is simple, downloading latest alsa drivers and compiling them. "Question: I've seen an alternative solution with ubuntu's "linux-backport-modules", isn't easier?". Actually, that solution is pretty quicker than this one, but with that one, the microphone was not working with me, so I compiled it myself.
This tip I got partially from [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto). And also from another thread here in forums [http://ubuntuforums.org/showthread.php?t=577699](http://ubuntuforums.org/showthread.php?t=577699)
I am passing all the process here, but at the end I have made some modifications in the script from this post [http://ubuntuforums.org/showpost.php...2&postcount=13](http://ubuntuforums.org/showpost.php...2&postcount=13), and you may want to download to automate the process. Then you should run these steps.
Code:

sudo sh alsa_1.sh
reboot
sudo sh alsa_2.sh
reboot

Sound should be working, I used this script and worked very well.
Otherwise you may want to do it manually. With the following steps.

Install dependencies:
Code:

 apt-get install build-essential libncurses5-dev gettext linux-headers-`uname -r`

Alsa Driver, Lib and Utils:
Code:

wget [ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.16.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.16.tar.bz2)
wget [ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.16.tar.bz2](ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.16.tar.bz2)
wget [ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.16.tar.bz2](ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.16.tar.bz2)

Extracting them and removing tarballs:
Code:

tar -xjf alsa-driver*.tar.bz2
tar -xjf alsa-lib*.tar.bz2
tar -xjf alsa-utils*.tar.bz2
rm alsa*.tar.bz2

Making the directory for compiling the source:
Code:

sudo mkdir -p /usr/src/alsa
sudo mv alsa-* /usr/src/alsa

Compiling and installing alsa-driver
Code:

cd /usr/src/alsa/alsa-driver*
sudo ./configure --with-cards=hda-intel
sudo make
sudo make install

Compiling and installing alsa-libs
Code:

 cd /usr/src/alsa/alsa-lib*
sudo ./configure
sudo make
sudo make install

Compiling and installing alsa-utils
Code:

cd /usr/src/alsa/alsa-utils*
sudo ./configure
sudo make
sudo make install

Reboot the machine and run more these comands:
Code:

sudo cp -v /lib/modules/2.6.22-*/kernel/sound/pci/hda/snd-hda-intel.ko /lib/modules/2.6.22-*/ubuntu/media/snd-hda-intel/snd-hda-intel.ko
sudo cp -v /usr/src/alsa/alsa-driver*/modules/* /lib/modules/2.6.22-*/kernel/sound/
sudo depmod -a

Reboot once more. And the next time will have sound working, no extra tweaks needed, like adding some line to /etc/modprobe.d/alsa-base. The steps above must solve the problem with sound and mic. The mic will work after enabling all boxes in the Gnome mixer applet. Change the input source to "front mic" or "mic" depending on which microphone you are gonna use. That's it.
Thanks. I had to add "front" in the mixer and turn it up before I had soun in the regular speakers. Apart from that, it's all good.

---

### Post by tqprvn on 2008-06-27
> **ostekongen said:**
> Okay...

```
sudo apt-get install linux-backports-modules-generic
```

...installing the alsa-driver-1.0.15, seemed to do the trick. I now have the option of "Headphone" in the mixer panel. However the volume level from the headphone-out is _very low_ and when I plug in a headphone... sound still comes out the laptop speakers?
same laptop, same problem, but running 8.04, so when I try and install the backports, I get a no-such-thing error back.

Any ideas?

---

### Post by tqprvn on 2008-07-01
any ideas?

---

