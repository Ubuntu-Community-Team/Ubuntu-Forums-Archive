---
title: "Unable to install V4L-DVB Device Drivers (Realtek 1f4d:c803)"
date: 2015-11-10
forum: General Help
---

### Post by fkervin on 2015-11-10
Hi all,

I have recently move from ubuntu 14.04 to ubuntu 15.10 (new fresh install). I was using a USB DVB-T tuner before but now I'm unable to use it.

The lsusb output of the device is this one:

Bus 001 Device 004: ID 1f4d:c803 G-Tek Electronics Group

Ive try to install V4L-DVB as explained here: 

[http://www.linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers](http://www.linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers)

Following the "Basic" Approach:

git clone [git://linuxtv.org/media_build.git](git://linuxtv.org/media_build.git)
cd media_build 
./build
 I've this error:

```
  CC [M]  /home/user/media_build/v4l/v4l2-compat-ioctl32.o
  CC [M]  /home/user/media_build/v4l/vb2-trace.o
/home/user/media_build/v4l/vb2-trace.c:4:30: fatal error: trace/events/vb2.h: No such file or directory
compilation terminated.
scripts/Makefile.build:258: recipe for target '/home/user/media_build/v4l/vb2-trace.o' failed
make[3]: *** [/home/user/media_build/v4l/vb2-trace.o] Error 1
Makefile:1398: recipe for target '_module_/home/user/media_build/v4l' failed
make[2]: *** [_module_/home/user/media_build/v4l] Error 2
make[2]: Leaving directory '/usr/src/linux-headers-4.2.0-16-generic'
Makefile:51: recipe for target 'default' failed
make[1]: *** [default] Error 2
make[1]: Leaving directory '/home/user/media_build/v4l'
Makefile:26: recipe for target 'all' failed
make: *** [all] Error 2
build failed at ./build line 491.
user@user:~/media_build$ 

```

I've also try the other two methods but I also have errors....


I've been looking for some information and it seems to be a problem that happend on latest kernel versions of Linux (I use 4.2.0-16), but I've found no solution :(

Is there any way to install those drivers or other ones that makes my tuner work ok? 

Regards and thanks in advance

---

### Post by QDR06VV9 on 2015-11-10
[Ubuntu 14.10 (Utopic Unicorn) reaches End of Life on July 23, 2015]("http://fridge.ubuntu.com/2015/07/03/ubuntu-14-10-utopic-unicorn-reaches-end-of-life-on-july-23-2015/")
Maybe upgrade to 15.10 or stay with 14.04 with support til 2019

---

### Post by fkervin on 2015-11-10
Thanks for your answer, runrickus.

I've actually using 15.10, not 14.10 (it was a typing error), so it's not a problem of being outdated, perhaps "too-updated", but not outdated.

The output of dmesg (I forgot in the first post) is this:

```
[  108.436664] usb 1-4: dvb_usb_v2: 'Trekstor DVB-T Stick Terres 2.0' successfully initialized and connected
[  108.436746] usbcore: registered new interface driver dvb_usb_rtl28xxu
```

As far as I'm concerned is ok, so there a driver/firmware problem on the usb stick.

Just like a told, the "Basic" Approach of the method returns the error I explained. I've try also with Developer's Approach:

```
git clone [git://linuxtv.org/media_build.git](git://linuxtv.org/media_build.git)
cd media_build 
./build --main-git
```

In this point, if I follow next instructions I don't know what am I supposed to add inside **~/media_build/media/drivers/media/video/foo.c** file, there is nothing specified :(, so using next make -C commands perhaps are not ok.

Instead of this, after **./build --main-git** I run sudo make install as the system suggest, and everything seems to install ok. The problem is that I have only 6 tv channels instead of the 70 I should have (in my last 14.04 install I had 70).

So, it is clear that the driver of the dongle is not ok.

I would really thank any help.

Regards

---

### Post by QDR06VV9 on 2015-11-10
Huumm? What method are you using to scan channels?

---

### Post by fkervin on 2015-11-10
Many thanks for your interest, runnickus,

I'm using TVheadend, in the installation of 14.04 gets more than 60 channels.

Regards

---

### Post by deadflowr on 2015-11-10
What kind of service is it scanning (over the air, cable, sat?)

---

### Post by fkervin on 2015-11-11
> **deadflowr said:**
> What kind of service is it scanning (over the air, cable, sat?)

Hi deadflowr,

Many thanks for your interest, I hope to be able to solve this with the help of all of you, perhaps it will be also usefull for anyone wanting yo watch TV on Ubuntu 15.10.

I want to watch DVB-T (free TV over the air). In my last 14.04 installation I used (and still can try and works perfectly) tvheadend as backend for this task. With 15.10 I've experience some problems making work this program (Tvheadend) but finally I installed it and works, it's explained in this thread:

[http://ubuntuforums.org/showthread.php?t=2301481](http://ubuntuforums.org/showthread.php?t=2301481)

If I don't install V4L-DVB I get some services in the program, but no channels, I can't see any TV channel. Installing V4L in Developer's Approach mode (just like I told on last post) I access to 6 TV channels, but on 14.04 I had almost 70 channels. By some reason the tuner works but only gets a very little number of channels.

At this moment I'm trying another USB stick (different model) and I've another 2 ones (I'll test with all of them). All those sticks worked great on 14.04, I'll see if anyone of them do its job in 15.10.

I'm also trying to scan using me-tv, I'll post results when done.

Meanwhile, if anyone can help me I'd thank a lot.

Regards

---

### Post by fkervin on 2015-11-11
Hi all,

After take several hours testing the problem seems to be many usb tuners have uncorrect drivers or for some reason doesn't work ok.

I've try four different DVB-T tuners and three of them find no channel or very few that later can't be played, only one of them works ok:

```
Bus 001 Device 003: ID 048d:9006 Integrated Technology Express, Inc. IT9135 BDA Afatech DVB-T HDTV Dongle
```

This is the only one that search for channels correctly, all the others fails.

Any idea? I'd really like to make work the tuner I wanted to use :(

Regards and thanks

---

### Post by fkervin on 2015-11-12
Hi all,

I'm back to tell I've try ME-TV and the result is very similar to TVheanend. With Me-TV channels are found but when I try use them (once scanned) they don't work and I've the message "Unknow program".

So, since I've found a USB tuner that works, but not other ones, problem seems to me related to firmware/drivers, please correct me if I'm wrong.

I have to make those tuners work since the one that does is not mine :(

Regards

---

### Post by deadflowr on 2015-11-12
Hmm, Have you tried any of the various command line scanners:
Scan: [http://www.linuxtv.org/wiki/index.php/Scan](http://www.linuxtv.org/wiki/index.php/Scan)
Dvbscan: [http://www.linuxtv.org/wiki/index.php/Dvbscan](http://www.linuxtv.org/wiki/index.php/Dvbscan)
W_scan: [http://linuxtv.org/wiki/index.php/W_sca]("http://linuxtv.org/wiki/index.php/W_scan")
You might need to turnoff tvheadend for these to run.

(Full-disclosure, I don't use tvheadend, but most tv app programs have similar functions and ways of working
I use mythtv, and have used tvtime, me-tv and kaffiene)

Also, anytime I've ever gotten "unknown program" is because my grabber has gone belly-up in someway.
So you might look at your grabber configuration.

---

