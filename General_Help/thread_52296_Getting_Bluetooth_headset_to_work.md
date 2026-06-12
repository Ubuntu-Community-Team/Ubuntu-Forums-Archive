---
title: "Getting Bluetooth headset to work"
date: 2005-07-27
forum: General Help
---

### Post by ubuntuuser on 2005-07-27
Hi,

has anyone here tried the HOWTO at [http://bluetooth-alsa.sourceforge.net](http://bluetooth-alsa.sourceforge.net)?

They say I need a 2.6.11 Kernel with integrated ALSA support. I have the regular 2.6.10 Kernel that comes with Hoary. Now I've got a few questions:

Is it possible to simply uninstall the 2.6.10 kernel and install 2.6.11?
Will the programs compiled with the old kernel still run or do I have to recompile?
Does this 2.6.11 have integrated ALSA support?
What problems will I most likely have when changing the kernel?
Is there an easier way to use Skype with my BT headset?

My headset is the Motorola HS801.

Thanks very much for your help.

---

### Post by kaiesh on 2005-08-05
I'm trying to fiddle with that now, using instructions at:
[http://www.gargan.org/linux/snd-bt-sco/README](http://www.gargan.org/linux/snd-bt-sco/README) 
[http://www.dcs.gla.ac.uk/~jp/snd-bt-sco/](http://www.dcs.gla.ac.uk/~jp/snd-bt-sco/) 
and at
[http://bluetooth-alsa.sourceforge.net/](http://bluetooth-alsa.sourceforge.net/) 

Like you, I am using Hoary, and I get up to the point where I need to
```

cd kernel
make
make install

``` 
under the btsco directory. At that point make complains:
```

make: *** /lib/modules/2.6.10-5-386/build: No such file or directory.  Stop.
make: *** [default] Error 

```

And I presume this is because the kernel doesn't have alsa built in? I have no idea though. I've built other modules from this kernel source before, but I don't really know much about ALSA at all.  ](*,) 

Do you get any further?
Any help from someone that's done this before would be appreciated.

K

---

### Post by ubuntuuser on 2005-08-08
I have put that back on my "things to do later" list :) but I think I will read through the links you provided and try it again. Thanks for those, btw.

---

### Post by Tolomir on 2005-08-16
On the german site we created a complete wiki entry about that topic.

[http://www.ubuntuusers.de/wiki/mobil:bluetooth_headset](http://www.ubuntuusers.de/wiki/mobil:bluetooth_headset)
(Don't blame me for my translation, typos are for amusement...)

**Bluetooth preparations**


To get bluetooth support, all you need to do is to install this softwarepacket:

    * bluez-utils

After installation, you can communicate with the bluetooth dongle.

Start a terminal session and enter this command

$ sudo hciconfig hci0 revision

As output you must get a rowentry like “SCO mapping: HCI”. Without it you can stop, you need some different dongle.

Now one can start to look after bluetooth devices. Use the command:

$ hcitool scan

to get a list of all recognized devices. It might be neccessary to enable the pairing mode of the devices, a long pressed on/off button of the headset might enable this mode:

Scanning ...
        00:0D:44:03:6B:8A       Logitech HS01-V16

In the 1st column one can see the address of the bluetooth device, that will be needed later to initialize the sound driver.

**Soundsystem**
Sound in- and output is based on the bluetooth-alsa project.
In this part you will get a sound device right for the headset in use.
Sad to say, there are no ubuntu packages available, so one has to compile the package on his own. To accomplish this task you need some additional packets:

    * cvs
    * automake1.7
    * libbluetooth-dev
    * libasound2-dev
    * linux-headers-[kernel version]

The kernel-headers modul should be installed in a terminal using this command, to ease the problem, what current kernel version is in use:

$ sudo apt-get install linux-headers-`uname -r`

After the installation of all packets, the sources have to be downloaded and compiled. These commands have to be executed in a root-shell:

$ cd /usr/src
$ cvs -d:pserver:anonymous@cvs.sf.net:/cvsroot/bluetooth-alsa co btsco
$ cd btsco
$ ./bootstrap
$ ./configure
$ make
$ make install
$ cd kernel
$ make
$ make install

The compiled module is saved in the folder /lib/modules/2.6.10/extra, a place where it cannot be located by the system. So it has to be moved to the correct location.

$ mv /lib/modules/2.6.10/extra /lib/modules/2.6.10-5-386

Please modify the version numbers according to the system.

After the move, dependecies have to be corrected.

$ depmod -e

To automatize the loading of the modul, there is a small initialisationscript quite usefull, that is executed each time the bluetooth dongle is plugged in. A file called  /etc/hotplug/usb/hci_usb is to be written with an editor and needs this content:

#!/bin/sh
modprobe snd_bt_sco
hciconfig hci0 voice 0x0060

To make it executable:

$ chmod +x /etc/hotplug/usb/hci_usb

Now each time the bluetooth dongle in connected, and this command entered

$ dmesg

An output like this should be the result:

...
usb 3-1: new full speed USB device using uhci_hcd and address 2
Bluetooth: HCI USB driver ver 2.7
usbcore: registered new driver hci_usb
snd-bt-sco revision 1.6 $
snd-bt-sco: snd-bt-scod thread starting

Additionally a new sound device should exist:

$ cat /proc/asound/cards

With this output:

0 [Live           ]: EMU10K1 - Sound Blaster Live!
                     Sound Blaster Live! (rev.4) at 0xe000, irq 12
1 [Headset   ]: Bluetooth SCO - BT Headset
                     BT Headset 1

It might be well proved, to assign ID 0 to the standard soundcard. Otherwise the IDs will change  each time the headset is en- or disabled. To get this result, the name of the standard soundcard module should be added to the file /etc/modules .

Is the name of the soundcardmodul unknown, 

$ lsmod

should help. The correct module should be in the line “snd_pcm”.

During bootup of KDE, the aRts soundserver might complain, a soundcard might be unavailable. (Because the headset, wasn't already connected via bluetooth)
The user should open the KDE-Controllcenter “Sound System &#8594; Hardware &#8594; Hardware-devicefile” and change the entry to hw:1,0 

Annotation: hw:x,y with x = number (counted from 0!) of the output device, y = subnumber (also starting from 0). So an entry of  hw:1,0 would be the second device with subnumber 1.

Now one can try to get the first tunes out of the headset:
On the first connection, the headset should be in the pairing-mode. On the computer one has to enter the pin of the headset. If this is by any means not functioning, one can blame the “PIN helper”. That is a small program, that is executed during the pairing procedure. Since it is started just once, it can be exchanged by a small script, here with the PIN “0000” (modify it to your needs):

$ echo '#!/bin/sh' > /tmp/bluepin.sh
$ echo 'echo "PIN:0000"' >> /tmp/bluepin.sh
$ chmod +x /tmp/bluepin.sh

Open the file /etc/bluetooth/hcid.conf  and locate the line “pin_helper” to set it to  /tmp/bluepin.sh .

Now a connection with the headset should be possible. The parameter is the address, that was shown after a “hcitool scan” (s.a.).

$ btsco -v 00:0D:44:03:6B:8A

With output:

btsco v0.4c
Device is 1:0
Voice setting: 0x0060
RFCOMM channel 1 connected

In a second terminal, the soundcard can be started:

$ aplay -B 1000000 -D plughw:Headset sound.wav

In skype one has to change the audio output device to /dev/dsp1 .

In xmms click on  “O &#8594; Settings (alternative CTRL+p) &#8594; Output I/O Plugin &#8594; Output Plugin: e.g. OSS driver &#8594; configuration  &#8594; devices”

Audiodevice: BT SCO PCM (Duplex)
Mixer: BT Headset Mixer

Confirm with OK two times. The press play. If everything went right and the hardware is willing, sound should play out of the headset.

Good luck. 

Tolomir

---

### Post by chruesu on 2005-08-27
thanks for this great howto

unfortunately it's not working on my pc:

btsco -v XX:XX:XX:XX:XX:XX
```
btsco v0.4c
Device is 1:0
Error: Failed to connect to SDP server: Invalid exchange
Assuming channel 2
Voice setting: 0x0060
Can't connect RFCOMM channel: Invalid exchange
```

 ](*,) 

So, do I need the new kernel? At the momment I'm still using 2.6.10-something-586
Sound configuration is really a horrible thing with linux...  :| 

Suggestions? Anybody?

---

### Post by kaiesh on 2005-08-29
Thanks for the brilliant howto! I followed your instructions, and finally got it to work!

I had a couple of problems with "Permisison Denied" errors from the SDP server, and authentication, but that was because of slight variants with my system and its setup.
 
chruesu, I'm sorry you're having problems, but I don't understand your errors... could you supply a dump of your /etc/bluetooth/hcid.conf ?

That might reveal a couple of things... While you're at it, provide a dump given by the execution of the command
dmesg

I'm not sure what I'm looking for, but I can compare it to mine and see if I can help in some way....  :roll: 

Thanks for the howto Tolomir!

K

---

### Post by kaiesh on 2005-08-29
By the way, I've been tinkering around with bluetooth in linux for a while, and have accumulated some links over time... so some of my stuff may have been setup by accident through other things... You can check out:

[http://del.icio.us/kaiesh/bluetooth](http://del.icio.us/kaiesh/bluetooth)

to see if there are some howto's which you've missed.

Hope that helps.

K

---

### Post by chruesu on 2005-08-30
> chruesu, I'm sorry you're having problems, but I don't understand your errors... could you supply a dump of your /etc/bluetooth/hcid.conf ?
That might reveal a couple of things... While you're at it, provide a dump given by the execution of the command
dmesg
I'm not sure what I'm looking for, but I can compare it to mine and see if I can help in some way

hey  kaiesh!
thanks a lot for this friendly offer.
i was already thinkin' that i have to try to change some settings in hcid.conf
however, until now without any result...
all the same, here is my config-file:
(I'll follow your instructions  ;-)  )

cat /etc/bluetooth/hcid.conf
```
#
# HCI daemon configuration file.
#
# $Id: hcid.conf,v 1.4 2004/04/29 20:14:21 holtmann Exp $
#

# HCId options
options {
        # Automatically initialize new devices
        autoinit yes;

        # Security Manager mode
        #   none - Security manager disabled
        #   auto - Use local PIN for incoming connections
        #   user - Always ask user for a PIN
        #
        security auto;

        # Pairing mode
        #   none  - Pairing disabled
        #   multi - Allow pairing with already paired devices
        #   once  - Pair once and deny successive attempts
        pairing multi;

        # PIN helper
        pin_helper /tmp/bluepin.sh;

        # D-Bus PIN helper
        dbus_pin_helper;
}

# Default settings for HCI devices
device {
        # Local device name
        #   %d - device id
        #   %h - host name
        name "%h-%d";

        # Local device class
        class 0x100;

        # Default packet type
        #pkt_type DH1,DM1,HV1;

        # Inquiry and Page scan
        iscan enable; pscan enable;

        # Default link mode
        #   none   - no specific policy
        #   accept - always accept incoming connections
        #   master - become master on incoming connections,
        #            deny role switch on outgoing connections
        #
        #lm accept,master;
        #
        lm accept;

        # Default link policy
        #   none    - no specific policy
        #   rswitch - allow role switch
        #   hold    - allow hold mode
        #   sniff   - allow sniff mode
        #   park    - allow park mode
        #
        #lp hold,sniff;
        #
        lp rswitch,hold,sniff,park;

        # Authentication and Encryption
        #auth enable;
        #encrypt enable;
}
```



dmesg |grep snd
```
snd-bt-sco revision 1.6 $
snd-bt-sco: snd-bt-scod thread starting
```

dmesg |grep Blue
```
Bluetooth: Core ver 2.7
Bluetooth: HCI device and connection manager initialized
Bluetooth: HCI socket layer initialized
Bluetooth: L2CAP ver 2.7
Bluetooth: L2CAP socket layer initialized
Bluetooth: RFCOMM ver 1.5
Bluetooth: RFCOMM socket layer initialized
Bluetooth: RFCOMM TTY layer initialized
Bluetooth: HCI USB driver ver 2.7
```

BTW: here the specs of the manufacturer:
Bluetooth compliance:
Bluetooth version 1.2 specifications
Supported Bluetooth profiles:
Bluetooth headset and hands-free profiles
Pairing passkey or PIN:
0000
Please note that the Headset is designed to work optimally with devices that support the Bluetooth Handsfree profile


I use (better: i would like to use) the headset in connection with my laptop

---

### Post by chruesu on 2005-09-02
Hi everybody!

ok. i tried to change some settings and now I've got a different error:

```
btsco -v 00:07:A4:21:84:FC
```
btsco v0.4c
Device is 1:0
Error: Failed to connect to SDP server: Function not implemented
Assuming channel 2

Voice setting: 0x0060
Can't connect RFCOMM channel: Resource temporarily unavailable


please, somebody! Any idea what I have to do in order to get my bt-headset workin' ???

---

### Post by ubuntuuser on 2005-09-04
Hey, thank you very much for making this HOWTO available.

I get some error messages during the compilation, maybe one of you can help me with that.

./bootstrap works fine. Then I type ./configure and get the following output ( I have marked an interesting line:
```
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... none
checking for a BSD-compatible install... /usr/bin/install -c
checking for ranlib... ranlib
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking bluetooth/bluetooth.h usability... yes
checking bluetooth/bluetooth.h presence... yes
checking for bluetooth/bluetooth.h... yes
checking for hci_open_dev in -lbluetooth... yes
checking for sdp_connect in -lbluetooth... yes
checking for ALSA CFLAGS...
checking for ALSA LDFLAGS...  -lasound -lm -ldl -lpthread
checking for libasound headers version >= 1.0.3... found.
checking for snd_ctl_open in -lasound... yes
[COLOR=Red]**./configure: line 4182: XIPH_PATH_AO: command not found**[/COLOR]
configure: creating ./config.status
config.status: creating Makefile
config.status: creating sbc/Makefile
config.status: creating avdtp/Makefile
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands
```

Ignorant as I am I type make anyway, and get (translated from German):

```
cd . && /bin/sh /usr/src/btsco/missing --run autoheader
touch ./config.h.in
cd . && /bin/sh ./config.status config.h
config.status: creating config.h
config.status: config.h is unchanged
make  all-recursive
make[1]: changing to directory »/usr/src/btsco«
Making all in sbc
make[2]: changing to directory »/usr/src/btsco/sbc«
make[2]: Nothing to do for the target »all«.
make[2]: leaving directory »/usr/src/btsco/sbc«
Making all in avdtp
make[2]: changing to directory »/usr/src/btsco/avdtp«
make[2]: Nothing to do for the target »all«.
make[2]: leaving directory »/usr/src/btsco/avdtp«
make[2]: changing to directory »/usr/src/btsco«
gcc  -Wall -O2   -o a2play  a2play.o -lbluetooth -lbluetooth sbc/libsbc.a -lbluetooth
a2play.o(.text+0x1837): In function `main':
: undefined reference to `pthread_create'
a2play.o(.text+0x1988): In function `main':
: undefined reference to `pthread_join'
collect2: ld returned 1 exit status
make[2]: *** [a2play] error 1
make[2]: leaving directory »/usr/src/btsco«
make[1]: *** [all-recursive] error 1
make[1]: leaving directory »/usr/src/btsco«
make: *** [all] error 2

```

What can I do?

---

### Post by guix on 2005-09-08
had the same, and filed the bug : [http://sourceforge.net/tracker/index.php?func=detail&aid=1285498&group_id=116589&atid=678258](http://sourceforge.net/tracker/index.php?func=detail&aid=1285498&group_id=116589&atid=678258)

---

### Post by pangloss on 2005-09-22
With respect to the a2play compile bug:

Just change your Makefile to include "-lpthread" for a2play, i.e. at line 131:

replace
```
a2play_LDADD =  -lbluetooth -lbluetooth sbc/libsbc.a
```
with
```
a2play_LDADD =  -lbluetooth -lpthread -lbluetooth sbc/libsbc.a
```

Now if someone could help with the problem I'm seeing:

```
$ sudo btsco -v 00:00:00:00:00:00
btsco v0.4c
Device is 1:0
Error: Failed to connect to SDP server: Permission denied
Assuming channel 2

Voice setting: 0x0060
Can't connect RFCOMM channel: Permission denied
```

I don't know what this means, so I'm a little lost on troubleshooting it.

---

### Post by pangloss on 2005-09-23
FWIW, I got everything working.

Here's what helped me:

[list]
[*][http://www.gentoo.org/doc/en/bluetooth-guide.xml](http://www.gentoo.org/doc/en/bluetooth-guide.xml) 
[*][http://www.freebsd.org/doc/en_US.ISO8859-1/books/handbook/network-bluetooth.html](http://www.freebsd.org/doc/en_US.ISO8859-1/books/handbook/network-bluetooth.html) 
[/list]

---

### Post by kaiesh on 2005-09-24
chruesu - sorry for the exceedingly delayed reply, there's been lots up at this end, I went through the output you provided, and noticed some differences...

in my hcid.conf, I have the following:

```
 
# Local device class
class 0xff0101;

``` 

You may want to try changing that and restarting hcid...

Also, in your btsco output, it indicated that you only had version 1.6, and your thread seemed be stuck in the starting phase, but this is the output of my same query (dmesg | grep snd)

```

[COLOR=Red]snd-bt-sco revision 1.7 $[/COLOR]
snd-bt-sco: snd-bt-scod thread starting
snd-bt-sco: playback_open
snd-bt-sco: capture_open
snd-bt-sco: prepare ok bps: 16000 size: 672 count: 42
snd-bt-sco: playback_trigger 1
snd-bt-sco: setting playback to bspcm
snd-bt-sco: playback_trigger 0
snd-bt-sco: setting playback to NULL

```

Are you sure that you have the latest files for everything?

---

### Post by kaiesh on 2005-09-24
On a slightly different note - I've managed to get my bluetooth headset to connect and can hear audio through it as well as have Ubuntu use the microphone - but I'm getting a strange problem with it all...

I'm using the [Logitech bluetooth HS01](http://www.logitech.com/index.cfm/products/details/GB/EN,CRID=2193,CONTENTID=9473) (first gen), and it actually seems to induce lag...

The problem is kind of hard to describe, but I use my headset mainly with Skype - so when I'm having discussions, the lag between my actually saying something and my conversant hearing it (and therefore being able to respond) increases over time... so much so, that at the beginning of the conversation there will be no noticeable lag - but 20 minutes into the conversation, and there's at least 10 seconds between my saying something and it arriving at the other ed. I'm not sure entirely which way the lag is being induced, but it's definitely there.

The worst part is, if I disconnect the Skype call, break the connection between the PC and the headset, and re-establish everything, then it works fine again. Basically screaming that the problem is inherent in some configuration of mine of btsco (or so I think). ](*,) My first guess was that the audio is not being processed at the correct rate - but then it's not as though the pitch in the audio has noticeably changed between the headset or copmuter speakers. Does anybody have a similar problem? Or an idea as to where to look for the solution for this?

---

### Post by kaiesh on 2005-09-24
[COLOR=DarkRed]Sorry pangloss, I only noticed after posting that you had resolved any problems you had, I'll leave this here for anyone else though...[/COLOR]

pangloss - are you actually trying to connect to the address 00:00:00:00:00 ?

Because that's a broadcast address (as far as I'm aware) and you're unlikely to ever get permission to send a connection request to a broadcast address... If you're trying a different address (i.e. not 00:00), then - although odd - try sudo'ing the command you're issuing.

The command I execute to connect to my headset is:
```
btsco -v 00:0D:44:01:10:63
```

and to find the address of my headset, I put it in discoverable mode and did the following:
```

kaiesh@computer:~$ hcitool scan
Scanning ...
        00:0D:44:01:10:63       Logitech HS01


```

---

### Post by pangloss on 2005-09-24
[QUOTE=kaiesh]pangloss - are you actually trying to connect to the address 00:00:00:00:00 ?[/QUOTE]

No =)

As for the lag you reported...I haven't used my headset yet for any significant length of time yet, so I haven't noticed such a problem on my end.

---

### Post by bag on 2005-09-28
Anyone know in which package btsco is installed?

I'm using Ubuntu Breezy and their is no tool like btsco.

Thx for your help.

---

### Post by dannemil on 2005-12-22
I have followed all of the steps for getting my Jabra BT200 headset to work, but when I get to the ./bootstrap command I get the following messages:

root@ubuntu:/home/dannemil/downloads/btsco # ./bootstrap
automake: configure.in: installing `./install-sh'
automake: configure.in: installing `./mkinstalldirs'
automake: configure.in: installing `./missing'
configure.in: 1121: installing `./config.guess'
automake: alsa-plugins/Makefile.am: warning: automake does not support libasound_module_pcm_a2dp_la_LDFLAGS being defined conditionally
automake: alsa-plugins/Makefile.am: warning: automake does not support libasound_module_pcm_headset_la_LDFLAGS being defined conditionally

If I then go on to try to ./configure I get the message that there is no configure file.

Any help on this?

---

### Post by chiefofthejojos on 2006-02-09
>  Any help on this?

I had this error and fixed it by installing automake1.7 instead of automake1.4

---

### Post by meyerman on 2006-12-08
Thanks for the howto: I was struggling with SuSe 10.1 and btsco (btsco 4.2,  2.6.16 kernel).  I had bought a Motorola H500 BT headset and Cambridge Silicon USB dongle which did not work.  So I replaced the USB dongle and the headset with a Logitech Mobile Freedom.  They still would not work.  I finally found this link.  Depending upon the settings in hcid.config different failure mechanisms can occur like "Error: Failed to connect to SDP server".  I could not find any information on the hcid.config file format.  After I read this howto I dumped the bluepincat script and used the simple /tmo/bluepin.sh script and the following hcid.config script and both headsets work fine with skype and xmms ( although the sound quality with xmms is poor ).   For xmms i used alsa sound ( not oss which did not work ).  Here is my hcid.conifg file
#
# HCI daemon configuration file.
#
# $Id: hcid.conf,v 1.4 2004/04/29 20:14:21 holtmann Exp $
#

# HCId options
options {
                                                                # Automatically initialize new devices
        autoinit yes;

        # Security Manager mode
        #   none - Security manager disabled
        #   auto - Use local PIN for incoming connections
        #   user - Always ask user for a PIN
        #
        security auto;

        # Pairing mode
        #   none  - Pairing disabled
        #   multi - Allow pairing with already paired devices
        #   once  - Pair once and deny successive attempts
        pairing multi;

        # PIN helper
        # if you want a interactiv query of your pin use /usr/bin/bluepin
        # /bin/bluepincat is using the pin in the /etc/bluetooth/pin file
        # pin_helper /usr/bin/bluepin;
        pin_helper /tmp/bluepin.sh;

        # D-Bus PIN helper
        # dbus_pin_helper;
}

# Default settings for HCI devices
device {
                                                                # Local device name
        #   %d - device id
        #   %h - host name
        name "BlueZ %h (%d)";

        # Local device class
        # e.g.
        #  0xsss100 = Computer
        #  0xsss104 = Computer Desktop
        #  0xsss108 = Computer Server
        #  0xsss10c = Computer Laptop
        # The 'sss' above define the service-class
        # see [https://www.bluetooth.org/foundry/assignnumb/document/baseband](https://www.bluetooth.org/foundry/assignnumb/document/baseband)
        # for more information.
        # 0x100bbb stands for "Object Transfer  (v-Inbox, v-Folder, ...)"
        # 0x040bbb stands for "Networking (LAN, Ad hoc, ...)"
        class 0x100;

        # Default packet type
        # pkt_type DH1,DM1,HV1;

        # Inquiry and Page scan
        # valid parameters: enable | disable
        iscan enable;
        pscan enable;

        # Default link mode
        #   none   - no specific policy
        #   accept - always accept incoming connections
        #   master - become master on incoming connections,
        #            deny role switch on outgoing connections
        #
        #lm accept,master;
        #
        lm accept;

        # Default link policy
        #   none    - no specific policy
        #   rswitch - allow role switch
        #   hold    - allow hold mode
        #   sniff   - allow sniff mode
        #   park    - allow park mode
        #
        # lp none;
        #
        lp rswitch,hold,sniff,park;

        # Authentication and Encryption
        # auth disable;
        # encrypt disable;

the /tmp/bluepin.sh script was created following the excellent howto and the script content was

#!/bin/sh
echo "PIN:0000"

NOTE: Both of my BT headsets use the same PIN which is 0000.   I have looked and several other BT headsets and they use the same PIN.  If you dont know the PIN for your BT headset 0000 is a good guess.

---

### Post by jryer on 2007-01-27
Hello Tolomir,

I have been looking all over for solutions to get my Jabra 250v BT headset working with my Kensington dongle. You give one bit of information that is more helpful than other messages I have read. You ask to enter this line
> sudo hciconfig hci0 revision

I get the following message:
> hci0:   Type: USB
        BD Address: 00:16:38:BE:F7:36 ACL MTU: 1017:8 SCO MTU: 64:8
        Firmware 0.65 / 39

I assume this is why I cannot get my headset working. As you state, if I do not see
> a rowentry like &#8220;SCO mapping: HCI&#8221;
and, therefore, I need a different dongle.

If this is true, how do I know what dongle to buy? Or, is there any work-around solution?

Thanks for your help!

---

### Post by Boolean263 on 2007-03-07
Hi folks!  I apologize in advance if thread necromancy is frowned upon, but this seemed most logical.

I found a cheap Motorola H300 headset, and then a Kensington dongle 33348 Bluetooth dongle.  I'm VERY close to getting them working on my Edgy install, but I'm stuck on an odd-seeming point.

I made it through Tolomir's very helpful howto at [the top of this thread]("http://ubuntuforums.org/showpost.php?p=304573&postcount=4") (with one minor oversight, which I'll explain in a moment).  I can l2ping the headset, figure out its MAC address, everything, but I can't get it to pair.

```

bash$ **uname -a**
Linux master 2.6.17-11-386 #2 Thu Feb 1 19:50:13 UTC 2007 i686 GNU/Linux
bash$ **sudo btsco -v 00:DE:AD:BE:EF:00**
btsco v0.42
Device is 2:0
Voice setting: 0x0060
Can't connect RFCOMM channel: Connection refused
bash$ **sudo cat /var/log/syslog | grep hcid**
Mar  7 17:26:51 localhost hcid[5506]: Bluetooth HCI daemon
[COLOR="Red"]Mar  7 17:26:51 localhost hcid[5506]: Unknown option 'pin_helper' line 27[/COLOR]
Mar  7 17:26:51 localhost hcid[5506]: syntax error line 27
Mar  7 17:26:51 localhost hcid[5506]: Register path:/org/bluez fallback:1
Mar  7 17:28:53 localhost hcid[5506]: HCI dev 0 registered
Mar  7 17:28:53 localhost hcid[5506]: Register path:/org/bluez/hci0 fallback:0
Mar  7 17:28:53 localhost hcid[5506]: HCI dev 0 up
Mar  7 17:28:53 localhost hcid[5506]: Device hci0 has been added
Mar  7 17:28:53 localhost hcid[5506]: Starting security manager 0
Mar  7 17:28:53 localhost hcid[5506]: Device hci0 has been activated
[COLOR="Red"]Mar  7 17:31:48 localhost hcid[5506]: pin_code_request (sba=00:FE:ED:FA:CE:00, dba=00:DE:AD:BE:EF:00)
Mar  7 17:31:48 localhost hcid[5506]: call_passkey_agent(): no agent registered[/COLOR]

```
(I've put dummy MACs in this listing, but I'm using the real ones on my system.)

I never get any sort of prompt for a PIN no matter what I do.  There was no "pin_helper" line in my /etc/bluetooth/hcid.conf, so I added it in the options { } section, and pointed it at a shell script identical to Tolomir's.  There was an entry for "passkey" which I've set to my headset's passkey.  I've used it with "security" set to "auto" and to "user", neither one makes a difference.

Here are the relevant packages I have installed:
[LIST]
[*]bluez-btsco 1:0.42-0ubuntu1
[*]bluez-cups 3.7-1ubuntu4
[*]bluez-hcidump 1.32-1
[*]bluez-passkey-gnome 0.5-2ubuntu2
[*]bluez-pcmcia-support 3.7-1ubuntu4
[*]bluez-pin 0.30-2.1ubuntu2
[*]bluez-utils 3.7-1ubuntu4
[*]linux-386 2.6.17.11
[*]gnome-bluetooth 0.8.0-0ubuntu1
[/LIST]
They're all stock Ubuntu packages through synaptic.  I'm not running a custom kernel.

Remember how I said I overlooked one detail of Tolomir's post?  It turns out I have the same problem (and it would seem, the same dongle) that jryer has:
```

bash$ **sudo hciconfig hci0 revision**
hci0:   Type: USB
        BD Address: 00:FE:ED:FA:CE:00 ACL MTU: 1017:8 SCO MTU: 64:8
        Firmware 0.65 / 39

```
No mention of "SCO mapping: HCI" anywhere, which is a dealbreaker according to Tolomir's howto.  It seems like a stretch to claim that that's the cause of my PIN problems, particularly when I'm so close (yet so far!) to having things work.  Am I really out of luck here with my dongle?  Or have I overlooked anything important when setting up my PIN helper?

Many thanks in advance!

---

### Post by Boolean263 on 2007-03-09
I got it working!  It turns out I needed to explicitly run
```
passkey-agent /etc/bluetooth/feed-pin.sh 00:DE:AD:BE:EF:00
```
and then, with that running in the background, pair my headset using btsco.  Now it seems to work wonderfully.

Thanks for your eyeballs.  And have faith Tolomir, if your dongle is the same of mine, then it wasn't such a bad buy after all!

---

### Post by rvernica on 2007-11-12
Did anyone managed to get a Motorola H300 working?

I got mine set up and paired up but I cannot hear any sound, just a "sssssssssssssss".

Any suggestions are welcome.

Thanks.

---

