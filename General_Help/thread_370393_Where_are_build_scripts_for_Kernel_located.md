---
title: "Where are build scripts for Kernel located?"
date: 2007-02-25
forum: General Help
---

### Post by aka_bigred on 2007-02-25
I am trying to install wish ( wish.sf.net ) for x10 control on my ubuntu box, but the install script fails.  It seems to be looking for the kernel build scripts, but doesn't find them.  

I'm newer to linux, so I'm not very good when it comes to  in-depth compiling issues.

The folder it seems to be looking for is /lib/modules/2.6.17-10-server/build

Can anyone help me out?

```

[FONT="Fixedsys"]
root@owfs:/usr/src# cd x10dev-2.1.5
root@owfs:/usr/src/x10dev-2.1.5# ls
CREDITS  dev              html     kernel-patches  Makefile  scripts
daemons  example_scripts  INSTALL  License.txt     RCS       utils
root@owfs:/usr/src/x10dev-2.1.5# make
(cd daemons; make)
make[1]: Entering directory `/usr/src/x10dev-2.1.5/daemons'
gcc -D_REENTRANT -static -I/usr/src/linux/include -I../dev   -c -o main.o main.c
gcc -D_REENTRANT -static -I/usr/src/linux/include -I../dev   -c -o pl_xcvr.o pl_xcvr.c
gcc -lpthread -Wall -o pld main.o pl_xcvr.o
gcc -D_REENTRANT -static -I/usr/src/linux/include -I../dev   -c -o cm11a_xcvr.o cm11a_xcvr.c
gcc -lpthread -Wall -o cm11ad main.o cm11a_xcvr.o
gcc -D_REENTRANT -static -I/usr/src/linux/include -I../dev   -c -o plusb_xcvr.o plusb_xcvr.c
gcc -lpthread -Wall -o plusbd main.o plusb_xcvr.o
make[1]: Leaving directory `/usr/src/x10dev-2.1.5/daemons'
(cd utils; make)
make[1]: Entering directory `/usr/src/x10dev-2.1.5/utils'
gcc -I/usr/src/linux/include -I.. nbread.c -Wall -o nbread
gcc -I/usr/src/linux/include -I.. x10watch.c -Wall -o x10watch
x10watch.c: In function âmainâ:
x10watch.c:136: warning: format â%dâ expects type âintâ, but argument 4 has type âchar *â
gcc -I/usr/src/linux/include -I.. x10logd.c -Wall -o x10logd
x10logd.c: In function âstartâ:
x10logd.c:208: warning: suggest parentheses around assignment used as truth value
gcc -I/usr/src/linux/include -I.. nbecho.c -Wall -o nbecho
make[1]: Leaving directory `/usr/src/x10dev-2.1.5/utils'
(cd dev; ./make.sh)
make[1]: Entering directory `/usr/src/x10dev-2.1.5/dev'
make -C /lib/modules/2.6.17-10-server/build SUBDIRS=/usr/src/x10dev-2.1.5/dev modules
make: Entering an unknown directory
make: *** /lib/modules/2.6.17-10-server/build: No such file or directory.  Stop.
make: Leaving an unknown directory
make[1]: *** [default] Error 2
make[1]: Leaving directory `/usr/src/x10dev-2.1.5/dev'
root@owfs:/usr/src/x10dev-2.1.5# make install
sh ./scripts/install.sh
cp -f daemons/*d /usr/sbin/
cp -f utils/x10logd /usr/sbin/
cp -f utils/x10watch /usr/bin/
cp -f utils/nbread /usr/bin/
cp -f utils/nbecho /usr/bin/
sh ./scripts/makedev.sh
Creating X10 devices in /dev/x10 with data_major=120 and control_major=121
(cd dev; ./make.sh install)
make[1]: Entering directory `/usr/src/x10dev-2.1.5/dev'
mkdir -p /lib/modules/2.6.17-10-server/kernel/drivers/char/x10
cp -f x10.ko /lib/modules/2.6.17-10-server/kernel/drivers/char/x10
cp: cannot stat `x10.ko': No such file or directory
make[1]: *** [install] Error 1
make[1]: Leaving directory `/usr/src/x10dev-2.1.5/dev'
depmod
root@owfs:/usr/src/x10dev-2.1.5# lsmod | grep x
snd_intel8x0           34844  0
snd_ac97_codec         97440  1 snd_intel8x0
snd_mixer_oss          19328  1 snd_pcm_oss
snd_pcm                84356  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd                    58116  6 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
snd_page_alloc         11528  2 snd_intel8x0,snd_pcm
ext3                  142344  1
jbd                    62100  1 ext3
piix                   11780  1
root@owfs:/usr/src/x10dev-2.1.5# modprobe x10
FATAL: Module x10 not found.
root@owfs:/usr/src/x10dev-2.1.5# uname -r
2.6.17-10-server
root@owfs:/usr/src/x10dev-2.1.5# cd /usr/sbin
root@owfs:/usr/sbin# ls | grep cm
cm11ad
root@owfs:/usr/sbin#[/FONT]

```

---

### Post by dcstar on 2007-02-25
> **aka_bigred said:**
> I am trying to install wish ( wish.sf.net ) for x10 control on my ubuntu box, but the install script fails.  It seems to be looking for the kernel build scripts, but doesn't find them.  

I'm newer to linux, so I'm not very good when it comes to  in-depth compiling issues.
.........

If you are compiling software then you need the relevant dev packages, there are kernel HOWTO's in the forum specifying what you need to compile kernels, so I would search them out and install what they need (for a start).

If the package you are compiling has specific dependencies, then you will have to find what those are and install them.

---

### Post by aka_bigred on 2007-02-26
I was able to find some more info last night.

I needed to run the following to get the needed headers, or whatever:

[PHP]apt-get install linux-headers-`uname -r`[/PHP]

Once I did that, x10dev installed fine.

---

### Post by JeremyLaurenson on 2007-02-28
I have compiled and run the installer but dont see my usb powerlink on /dev/usb... Which controller are you using?

---

### Post by aka_bigred on 2007-02-28
I have the serial Powerlinc II connected to a Serial to USB converter. 

I think I have some issues with the driver for my serial-USB adapter.  I haven't gotten it working, but got past the compile/install hurdle.  I have a Prolific Technology PL2303X USB - Serial adapter.  I haven't looked at it too much, been busy at work & such.

I also don't seem to find the PL executable in the /usr/sbin/ folder like I am expecting from the wish install instructions.

---

### Post by aka_bigred on 2007-02-28
I got it working.


turns out the USB-serial converter was fine. The documentation is wrong on the wish v2 page for starting the Powerlinc II daemon.  It shows:

[PHP] 	
modprobe x10
/usr/sbin/pl -device /dev/ttyS0
/usr/sbin/x10logd
[/PHP]

The daemon for the Powerlinc II is be pl**d** not pl so to start it's:

[PHP] 	
modprobe x10
/usr/sbin/pld -device /dev/ttyS0
/usr/sbin/x10logd
[/PHP]

of course for me using the USB-serial converter I feed it /dev/ttyUSB0 for the device name.

---

