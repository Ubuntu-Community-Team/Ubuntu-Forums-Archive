---
title: "unable to boot into ubuntu"
date: 2007-05-14
forum: General Help
---

### Post by luke9511 on 2007-05-14
ok im using ubuntu 6.10 and just managed to get it installed on my desktop and i was working on getting my videocard working (which is an ATI Radeon X1600 Pro PCI-E 512mb) and i some how got it to work and so i started installing my games, i installed cedega and crossover office and before i had the problem i was installing counter strike source through cedega and i decided to reboot the computer, when it got to the loading screen with the orange bar it would go all the way to the end and then just stops, it doesnt bring up the login window or anything, i dont know what happend, if anyone can give me advice on this please let me know and thanks in advace for any help/advice.

---

### Post by floke on 2007-05-14
Can you boot in recovery mode?

---

### Post by luke9511 on 2007-05-14
> **Steve.K said:**
> Can you boot in recovery mode?
yes i can

---

### Post by floke on 2007-05-14
can you startx from the terminal? (sudo startx); or, failing that also 'sudo /etc/init.d/gdm restart'? Does thius get you in?

---

### Post by luke9511 on 2007-05-14
> **Steve.K said:**
> can you startx from the terminal? (sudo startx); or, failing that also 'sudo /etc/init.d/gdm restart'? Does thius get you in?

i did the first one and i get an error saying no screens found

---

### Post by floke on 2007-05-14
What about the second one?

You could also try 'sudo dpkg-reconfigure xserver-xorg'

---

### Post by luke9511 on 2007-05-14
> **Steve.K said:**
> What about the second one?

You could also try 'sudo dpkg-reconfigure xserver-xorg'
the 2nd command gave me the same thing and the command you just gave me didnt work either

---

### Post by luke9511 on 2007-05-15
anyone else got any ideas?

---

### Post by floke on 2007-05-15
Are you using gnome or KDE? My thinking is perhaps that if you are using gnome, then you could pull KDE off the repos, select KDM rather than GDM as the default manager, and see if that does any good - if something to do with gnome was broken then this would skirt round it and identify the problem (i.e. broken gnome) - for which you could then try deleting your configuration files (.gnome .gconf .gconf2 .xauthority .iceauthority etc.) so that gnome would reset them (this would mean you losing your configurations, but they look lost at the moment as it is).

---

### Post by floke on 2007-05-15
You could also try booting in verbose mode and seeing where it hangs (I think this is something like ctrl-F1/F2 etc. or ctral-alt-F1 etc. on bootup)

---

### Post by luke9511 on 2007-05-15
yes im using gnome how would i go about useing kde instead cause that sounds like a good idea

---

### Post by luke9511 on 2007-05-15
i figured out how to get kde but im getting the same problem that i was getting gdm, so im guessing it may have something to do with maybe my xorg.conf file cause when i try to use the sudo startx command its accessing xorg.conf, is there any way to access this and edit it in recovery mode?

---

### Post by luke9511 on 2007-05-16
is it posible to reinstall the xserver without reinstalling ubuntu? cause i want to try that before i have to reinstall

---

### Post by iAlta on 2007-05-16
You rarely have to reinstall the OS.

I'm not sure how to help you, you could try using 'mesa', I believe that's what it's called.

Simply add 'mesa' in the xorg.conf file where it says 'ati' or something like that.

If you have access to internet with decent speed, and have some time, try taking a listen to this: [http://www.linuxreality.com/podcast/episode-54-xorgconf/](http://www.linuxreality.com/podcast/episode-54-xorgconf/)

---

### Post by luke9511 on 2007-05-16
> **iAlta said:**
> You rarely have to reinstall the OS.

I'm not sure how to help you, you could try using 'mesa', I believe that's what it's called.

Simply add 'mesa' in the xorg.conf file where it says 'ati' or something like that.

If you have access to internet with decent speed, and have some time, try taking a listen to this: [http://www.linuxreality.com/podcast/episode-54-xorgconf/](http://www.linuxreality.com/podcast/episode-54-xorgconf/)

well i dont know how to edit xorg.conf through the recovery console

---

### Post by iAlta on 2007-05-16
first it's 'vesa'

well I don't think I have ever been in recovery mode, but you should have a terminal, right?

try this:

```
cd /etc/X11
```
to change to the X11 direcotory.

```
nano xorf.conf
```
nano is a text editor to edit the xorg.conf file.

EDIT: you may need root privilages. To achieve this use 'sudo' (super user do):

```
sudo nano xorg.conf
```

---

### Post by luke9511 on 2007-05-16
> **iAlta said:**
> first it's 'vesa'

well I don't think I have ever been in recovery mode, but you should have a terminal, right?

try this:

```
cd /etc/X11
```
to change to the X11 direcotory.

```
nano xorf.conf
```
nano is a text editor to edit the xorg.conf file.

EDIT: you may need root privilages. To achieve this use 'sudo' (super user do):

```
sudo nano xorg.conf
```yup thats what the problem was, it was those stupid ati drivers, now if i could just get it working again without the drivers breaking ubuntu

---

### Post by iAlta on 2007-05-16
I have now officially help my first fellow user!\\:D/

---

### Post by luke9511 on 2007-05-16
> **iAlta said:**
> I have now officially help my first fellow user!\\:D/

congrats and thanks for the help and you wouldnt by chance know how to get an ati video card to work without breaking ubuntu do you?

---

### Post by luke9511 on 2007-05-16
ok i just found out that the fglrx drivers is what messed up my ubuntu, is there any way i can get direct rendering and that stuff to play games with, without using those drivers?

---

### Post by luke9511 on 2007-05-16
how do i keeop fglrx from breaking the xserver?

---

### Post by iAlta on 2007-05-17
I have no idea, try the unofficial wiki for the ATI Linux drivers:

[http://wiki.cchtml.com/index.php/Main_Page](http://wiki.cchtml.com/index.php/Main_Page)

[http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide)

---

### Post by luke9511 on 2007-05-17
> **iAlta said:**
> I have no idea, try the unofficial wiki for the ATI Linux drivers:

[http://wiki.cchtml.com/index.php/Main_Page](http://wiki.cchtml.com/index.php/Main_Page)

[http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide)

thats what i've been using and everytime i follow it and do everything to the letter the drivers end up breaking the xserver

---

### Post by iAlta on 2007-05-17
I used it just now, and it worked flawlessly...

Are you sure Linux finds your card, have you tried 'lspci' ?

---

### Post by luke9511 on 2007-05-17
well heres the output from lspci. please note that i have an onboard ati graphics card and a PCI-E ati video card so just letting you know and the onboard is disabled

```
root@trey-desktop:~# lspci
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:02.0 PCI bridge: ATI Technologies Inc RS480 PCI-X Root Port
00:12.0 IDE interface: ATI Technologies Inc ATI 4379 Serial ATA Controller
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: ATI Technologies Inc RV530 [Radeon X1600]
01:00.1 Display controller: ATI Technologies Inc RV530 [Radeon X1600] (Secondary)
02:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:05.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
02:09.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 07)
02:09.1 Input device controller: Creative Labs SB Live! MIDI/Game Port (rev 07)
02:0a.0 Multimedia controller: Philips Semiconductors SAA7130 Video Broadcast Decoder (rev 01)

```

---

### Post by iAlta on 2007-05-18
> **luke9511 said:**
> 
```

01:00.0 VGA compatible controller: ATI Technologies Inc RV530 [Radeon X1600]
01:00.1 Display controller: ATI Technologies Inc RV530 [Radeon X1600] (Secondary)

```

Well it is definitely recognized, but I have no idea how to help you. I recommend creating a new thread that will get into the 'New Posts' section and get some attention from some more experienced users...

---

### Post by 13u11fr09 on 2007-05-18
> **luke9511 said:**
> well heres the output from lspci. please note that i have an onboard ati graphics card and a PCI-E ati video card so just letting you know and the onboard is disabled

```
root@trey-desktop:~# lspci
...
01:00.0 VGA compatible controller: ATI Technologies Inc RV530 [Radeon X1600]
01:00.1 Display controller: ATI Technologies Inc RV530 [Radeon X1600] (Secondary)
...

```


my initial thought is that X is trying to use the onboard card and bombing.  Could you post you xorg.conf file?  You *may* need a line in the "Device" section for your graphics card that reads:

```

   BusID       "PCI:1:0:0"

```
or
```

   BusID       "PCI:1:0:1"

```

---

