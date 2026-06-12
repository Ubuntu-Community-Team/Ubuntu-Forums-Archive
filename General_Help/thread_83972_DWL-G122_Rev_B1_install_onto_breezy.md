---
title: "DWL-G122 Rev B1 install onto breezy"
date: 2005-10-30
forum: General Help
---

### Post by Whatthehello on 2005-10-30
I cant do it. somehow, none of the tutorials i used works. I even searched on the forums. I could not find an answer. :( i really hope i can get it to work.

DWL-G122 Rev B1

---

### Post by Whatthehello on 2005-10-30
:(

---

### Post by ultra.nj on 2005-10-30
i have the dwl-122 on breezy and used the tutorial here

[http://ubuntuforums.org/showthread.php?t=25676&highlight=dwl-122](http://ubuntuforums.org/showthread.php?t=25676&highlight=dwl-122)

you never know, it could work :)

if that fails, just try these and go through all of them :o

[http://ubuntuforums.org/search.php?searchid=2305949&highlight=dwl-g122](http://ubuntuforums.org/search.php?searchid=2305949&highlight=dwl-g122)

---

### Post by Whatthehello on 2005-10-30
thank you. i will try that

---

### Post by Whatthehello on 2005-10-30
bleh. it doesnt work.

> 
wlanctl-ng: No such device
wlanctl-ng: No such device
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
sit0: unknown hardware address type 776
Bind socket to interface: No such device
dennis@ubuntu:~$ sudo nano /etc/network/if-pre-up.d/linux-wlan-ng-pre-up
dennis@ubuntu:~$ cd /etc/hotplug/usb
dennis@ubuntu:/etc/hotplug/usb$ sudo nano prism2_usb dennis@ubuntu:/etc/hotplug/usb$ sudo sh /etc/hotplug/usb/prism2_usb wlanctl-ng: No such device
wlanctl-ng: No such device
There is already a pid file /var/run/dhclient.pid with pid 0
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
sit0: unknown hardware address type 776


whats wrong with it? i did everything

---

### Post by lupine_nickt on 2005-10-30
Don't worry -- it is possible :). I'm using the DWL-G122 Rev. B1 as well. It's an RT2500 chip, rather than a prism, which is why the wlan-ng drivers don't work (I think). (Well, it's actually RT2500USB or RT2570, for the technical terms). 

I used the rt2x00 driver - which you can find at:-http://rt2x00.serialmonkey.com; the download I used was at:- [http://prdownloads.sourceforge.net/rt2400/rt2570-1.1.0-b1.tar.gz?download](http://prdownloads.sourceforge.net/rt2400/rt2570-1.1.0-b1.tar.gz?download)

You need to compile it (come back to me if you need help with that - I'll see if I can remember how I did it :) ), and eventually you'll get the rt2500usb.ko module, which need to copy to your /lib/modules/[kernel-version]/kernel/drivers/usb/net directory. Then it's a simple matter of 'modprobe rt2570', and it should then show up for config. (including WEP) in System->Administtration->Networking

In 32-bit mode, you can get it working using ndiswrapper and the drivers that come on the CD - just install ndiswrapper using Synaptic, then use it with the XP drivers provided on your CD.

xF,

...Nick

---

### Post by Whatthehello on 2005-10-30
lol. can you direct me on how to compile it and install it?

---

### Post by lupine_nickt on 2005-10-30
Will do :).

First, you'll need to make sure that you've got all the tools you need - so make sure that you've got gcc installed, at the least. When you run 'make' (see later), it'll fail if there's something it needs which you don't have... in which case, it'll tell you what it's missing - so install it :). Download 'rt2570-1.1.0-b1.tar.gz' from the link I gave you earlier, and make sure it's on your desktop. Then you want to open up a terminal (I use a root terminal; if you don't want to, just remember to type 'sudo' before all the commands below)... wherever I type [ENTER], hit the enter/return key :)

type:
cd Desktop [ENTER]
tar -xzvf rt2570-1.1.0-b1.tar.gz [ENTER] 
cd rt2570-1.1.0-b1/Module [ENTER]
make [ENTER]
make install [ENTER]

Then that's your module installed. Now try:-

modprobe rt2570 [ENTER]

If it says something like 'can't find module: rt2570', then you want to do:-
cp rt2570.ko /lib/modules/[kernel-version]/kernel/drivers/usb/net [ENTER]

and then: modprobe rt2570 [ENTER] again

note: [kernel-version] is, for me, 2.6.12-9-amd64-k8... could be different for you, though.

Once that module's loaded, you should have a network interface 'rausb0', which you can configure in the normal way... using System->Administration->Networking

Hope that helps :)

xF,

...Nick

---

### Post by Whatthehello on 2005-10-30
hold on. i need to boot into linux XP

which version of gcc do i need? in synaptic theres gcc, gcc-.3.-base, and gcc-4.0

how can i check my kernel version?

---

### Post by lupine_nickt on 2005-10-30
gcc4 will be fine. 

xF,

...Nick

---

### Post by Whatthehello on 2005-10-30
i installed it and it still says make command not found

---

### Post by lupine_nickt on 2005-10-30
in your terminal, type:-
ls /lib/modules [RETURN]

You should get some output like:-
2.6.12  2.6.12-9-amd64-k8

You want the bit corresponding to:- 2.6.12-9-amd64-k8


Oh, and you need to install make as well (in synaptic, or in terminal, apt-get install make)

---

### Post by Whatthehello on 2005-10-30
now im getting this 

> 
root@ubuntu:~/Desktop/rt2570-1.1.0-b1/Module# make
make: *** /lib/modules/2.6.12-9-386/build: No such file or directory.  Stop.
rt2570.ko failed to build!
make: *** [module] Error 1


---

### Post by lupine_nickt on 2005-10-30
Try installing the kernel sources -- package name linux-source-2.6.12; it might take a while though

---

### Post by Whatthehello on 2005-10-30
how can i do that? 
sorry if im asking too many questions, but im really new to linux

---

### Post by lupine_nickt on 2005-10-30
In synaptic - just search for linux-source & install the package :)

xF,

...Nick

---

### Post by Whatthehello on 2005-10-30
its not in synaptic

---

### Post by lupine_nickt on 2005-10-30
Strange -- it's in mine. Try shutting down synaptic, opening a terminal & typing:

sudo apt-get install linux-source [return]

---

### Post by Whatthehello on 2005-10-30
nope. still not working.

---

### Post by Whatthehello on 2005-10-30
i think it might be linux-headers

---

### Post by Whatthehello on 2005-10-30
now im getting this

> 
root@ubuntu:~/Desktop/rt2570-1.1.0-b1/Module# make
/usr/src/linux-headers-2.6.12-9-386/scripts/gcc-version.sh: line 11: gcc-3.4: command not found
/usr/src/linux-headers-2.6.12-9-386/scripts/gcc-version.sh: line 12: gcc-3.4: command not found
make[1]: gcc-3.4: Command not found
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-9-386'
  CC [M]  /home/dennis/Desktop/rt2570-1.1.0-b1/Module/rtusb_main.o
/bin/sh: gcc-3.4: command not found
make[2]: *** [/home/dennis/Desktop/rt2570-1.1.0-b1/Module/rtusb_main.o] Error 127
make[1]: *** [_module_/home/dennis/Desktop/rt2570-1.1.0-b1/Module] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-9-386'
rt2570.ko failed to build!
make: *** [module] Error 1


---

### Post by lupine_nickt on 2005-10-30
How about linux-headers? (normally be linux-headers-2.6.12-9 - ignore all the -k8, -smp, etc ones)

If you can't find that, post the contents of your /etc/apt/sources.list file... if you can't find it, you'll be missing a repository somewhere.

Eh. beat me to it :)

xF,

...Nick

---

### Post by lupine_nickt on 2005-10-30
You should be able to install gcc-3.4 (in synaptic) as well (the output seems to say it wants it)

---

### Post by Whatthehello on 2005-10-30
when i type in apt-get install gcc-3.4, this is what it spits out:

> root@ubuntu:~# apt-get install gcc-3.4
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?


---

### Post by lupine_nickt on 2005-10-30
you need to close synaptic. only one package-installing program can be used at a time.

---

### Post by Whatthehello on 2005-10-30
kk.

> 
root@ubuntu:~# apt-get install gcc-3.4
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package gcc-3.4


---

### Post by lupine_nickt on 2005-10-30
eh. we'll get there in the end, lol. You saw a version 3 in Synaptic - can you install it from there?

---

### Post by Whatthehello on 2005-10-30
ok. i just followd this guide.

[http://ubuntuforums.org/showthread.php?t=79896&highlight=find+gcc-3.4+breezy](http://ubuntuforums.org/showthread.php?t=79896&highlight=find+gcc-3.4+breezy)

and i got 3.4 installed. now im making the package

---

### Post by lupine_nickt on 2005-10-30
ah :). I'm on amd64, so didn't have that problem. Did it compile?

xF,

...Nick

---

### Post by Whatthehello on 2005-10-30
is this correct?

> 
root@ubuntu:~/Desktop/rt2570-1.1.0-b1/Module# make install
echo "2.6 module install"
2.6 module install
make -C /lib/modules/2.6.12-9-386/build SUBDIRS=/home/dennis/Desktop/rt2570-1.1.0-b1/Module modules_install
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-9-386'
  INSTALL /home/dennis/Desktop/rt2570-1.1.0-b1/Module/rt2570.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-9-386'


---

### Post by lupine_nickt on 2005-10-30
doesn't look like an error. does modprobe work? If not, try the cp command earlier. All 'make install' does is copy the module over.

xF,

...Nick

---

### Post by Whatthehello on 2005-10-30
im getting with modprobe 

FATAL: Module rt2570 not found.rt2570

i tried 

cp rt2570.ko /lib/modules/2.6.12-9-386/kernel/drivers/usb/net

and it still not working

---

### Post by lupine_nickt on 2005-10-30
I've got a copy of it in: /lib/modules/2.6.12/extra as well. Try copying it into there.

Also, once you've done that & run modprobe again, can you post the output for the commands:
ls /lib/modules/2.6.12/extra [RETURN] and
ls /lib/modules/2.6.12-9-386/kernel/drivers/usb/net

Oh, and try 'insmod rt2570.ko' - it might work.

xF,

...Nick

---

### Post by Whatthehello on 2005-10-30
root@ubuntu:~/Desktop/rt2570-1.1.0-b1/Module# ls /lib/modules/2.6.12/extra
rt2570.ko

root@ubuntu:~/Desktop/rt2570-1.1.0-b1/Module# ls /lib/modules/2.6.12-9-386/kernel/drivers/usb/net
atmel    kaweth.ko   rt2570.ko   usbnet.ko  zd1211
catc.ko  pegasus.ko  rtl8150.ko  zd1201.ko



i think it wokrs now. im going to restart my computer

---

### Post by lupine_nickt on 2005-10-30
w00t! :)

/me crosses fingers...

xF,

...Nick

---

### Post by Whatthehello on 2005-10-31
yay! it works!

thank you so much. I owe you one

---

### Post by KidStardust on 2005-11-24
I have a similar problem... I have followed this discussion and could build the module which was much more of a hassle than I could have imagined.
Now the only thing left to do seems to be "modprobe rt2570" - but the machine keeps telling me "module not found". The .ko-file has been copied to /extras and to both kernel trees but it just does not work. I have no clue what to do...
Any help is highly appreciated. (Right now I have spent about 3 hours on getting my DWL-G122 to work).
Thanks in advance!

---

### Post by KidStardust on 2005-11-24
my outputs:

stardust@pantheon:~/Desktop/rt2570-1.1.0-b1/Module$ ls /lib/modules/2.6.12/extra
rt2570.ko

stardust@pantheon:~/Desktop/rt2570-1.1.0-b1/Module$ ls /lib/modules/2.6.12-9-386/kernel/drivers/usb/net
atmel    kaweth.ko   rt2570.ko   usbnet.ko  zd1211
catc.ko  pegasus.ko  rtl8150.ko  zd1201.ko

stardust@pantheon:~/Desktop/rt2570-1.1.0-b1/Module$ ls /lib/modules/2.6.12-10-386/kernel/drivers/usb/net
atmel    kaweth.ko   rt2570.ko   usbnet.ko  zd1211
catc.ko  pegasus.ko  rtl8150.ko  zd1201.ko

The module is in its place but modprobe keeps telling me:
stardust@pantheon:~/Desktop/rt2570-1.1.0-b1/Module$ modprobe rt2570
FATAL: Module rt2570 not found.

Please help!
(I have already tried the insmod command, but modprobe still fails)

---

### Post by Whatthehello on 2005-11-24
[QUOTE=KidStardust]my outputs:

stardust@pantheon:~/Desktop/rt2570-1.1.0-b1/Module$ ls /lib/modules/2.6.12/extra
rt2570.ko

stardust@pantheon:~/Desktop/rt2570-1.1.0-b1/Module$ ls /lib/modules/2.6.12-9-386/kernel/drivers/usb/net
atmel    kaweth.ko   rt2570.ko   usbnet.ko  zd1211
catc.ko  pegasus.ko  rtl8150.ko  zd1201.ko

stardust@pantheon:~/Desktop/rt2570-1.1.0-b1/Module$ ls /lib/modules/2.6.12-10-386/kernel/drivers/usb/net
atmel    kaweth.ko   rt2570.ko   usbnet.ko  zd1211
catc.ko  pegasus.ko  rtl8150.ko  zd1201.ko

The module is in its place but modprobe keeps telling me:
stardust@pantheon:~/Desktop/rt2570-1.1.0-b1/Module$ modprobe rt2570
FATAL: Module rt2570 not found.

Please help!
(I have already tried the insmod command, but modprobe still fails)[/QUOTE]
try copying rt2570.ko into /lib/modules/2.6.12/extra 
after that, try modprobe again.
tell me what happens.

---

### Post by KidStardust on 2005-11-24
I did this before but it does not help.
Actally words cannot express how fed up I am with this situation. I have wasted nearly 4 hours with this issue. My solution is to go back to WinXP after one and half a year (as much as I hate it, it just does its job, even though not too well in some areas) until wlan works out of the box in linux - whenever this might be.
Fiddling around in an extent like this is unacceptable for a distribution that has been tailored to the home user. I'd rather shell out a bucket full of money for an Apple Powerbook before going through this #§@" again, my time is just too precious.

Who cares for free beer if it tastes awful?
Just my 2 cents.

I'll probably be back next week and will bother you with some dual boot questions :-)

---

### Post by danish_demon on 2006-01-13
i'm in the same boat as the last person.  i have rt2570.ko in the appropriate usb/net dirs and in /extra.

any help out there?

edit:  i eventually was able to get the insmod command to work and the interface to active, but i still don't have a connection to the internet.

edit again:  I GOT IT, YES!!!!!!!!!!!!!!!!!!!!!!!

---

### Post by danish_demon on 2006-01-14
alright, i have it working, but it doesn't load automatically when i reboot.  from the other installation guide, it said to type ```
 sudo echo rt2570 >> /etc/modules 
```, but i get a "permission denied" error when i try that.  is there another way to get it to load at boot? (or a way for this method to work for me?)

thanks

edit:  i manually added rt2570 to /etc/modules (via "sudo gedit /etc/modules"), but it still didn't load.

edit again:  i got it to work.  i had to copy rt2570.ko to lib/modules/[kernel version]/kernel/net/wireless

---

### Post by kevyn72 on 2006-03-03
Hi,

I am trying to build this on Breezy and getting an odd error.

I have done the following:

sudo apt-get install build-essential
sudo apt-get install build-essential linux-headers-2.6.12-9-386
sudo apt-get install linux-source

Download rt2570-1.1.0-b1.tar.gz to Desktop
cd Desktop
tar -xzvf rt2570-1.1.0-b1.tar.gz
cd rt2570-1.1.0-b1/Module
make

and I get:

ubuntu@ubuntu:~/Desktop/rt2570-1.1.0-b1/Module$ make install
echo "2.6 module install"
2.6 module install
make -C /lib/modules/2.6.12-9-386/build SUBDIRS=/home/ubuntu/Desktop/rt2570-1.1.0-b1/Module modules_install
make[1]: Entering directory `/lib/modules/2.6.12-9-386/build'
make[1]: *** No rule to make target `modules_install'.  Stop.
make[1]: Leaving directory `/lib/modules/2.6.12-9-386/build'
make: *** [modules_install] Error 2

Here's what is in /lib/modules/2.6.12-9-386

ubuntu@ubuntu:~/Desktop/rt2570-1.1.0-b1/Module$ ls /lib/modules/2.6.12-9-386/
build   madwifi         modules.dep          modules.isapnpmap  modules.symbols
initrd  modules.alias   modules.ieee1394map  modules.pcimap     modules.usbmap
kernel  modules.ccwmap  modules.inputmap     modules.seriomap   volatile

The directory /lib/modules/2.6.12-9-386/build is empty (hence no make rule found).

Any idea why this is going wrong?

Many thanks,

Kevyn

PS I am running Ubuntu in the free VMWare player, in case that is relevant.

---

### Post by Neo4 on 2007-02-19
I i'm having serious problems with my edgy and g122 B1, 

with Iwconfig rausb0 is dettected! and if I put it in mode ad-hoc it works!

but on managed mode or monitor it doesnt!

I've tried to install but when I do make it occurs this error:

ake[2]: ** [/home/neo4/Desktop/rt2570-1.1.0-b1/Module/rtusb_main.o] Erro 1
make[1]: ** [_module_/home/neo4/Desktop/rt2570-1.1.0-b1/Module] Erro 2
make[1]: Saindo do diretório `/usr/src/linux-headers-2.6.17-11-generic'
rt2570.ko failed to build!
make: ** [module] Erro 1


I'm on this since yesterday morning ! i'm getting tired of linux =(

---

### Post by Neo4 on 2007-02-19
ok i'v downloaded the 2500 drivers and it worked :)

but still the same problem!

I only can connect to net with my intel 2200bg! 

it is detected on iwconfig and on my gnome network manager but doen't search for wireless lan!

my 2200bg shows my lan but the g122 not! arghhh!

---

