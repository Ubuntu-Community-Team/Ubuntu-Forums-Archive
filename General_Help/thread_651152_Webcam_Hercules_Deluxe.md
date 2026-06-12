---
title: "Webcam Hercules Deluxe?"
date: 2007-12-27
forum: General Help
---

### Post by Reeva on 2007-12-27
Hello,

I have a problem installing my Hercules Webcam Deluxe on 7.10

I used this guide

> 
It toook me quite a while to figure this one out, so I post how I did it: I also do not seem to be able to open up a new thread for this (partially new) HowTo, so I post here. The info I collected stems from this thread and from [http://blog.thedarkmere.net/index.ph...peg-guide.html](http://blog.thedarkmere.net/index.ph...peg-guide.html). I had to modify the latter end steps though to make it work properly.

The preliminaries: My machine is an IBM Netvista PC (PIII 1Gig), Ubuntu 6.06 Dapper, server installation with additional XUbuntu interface addon.

The Hercules Classic Webcam is an el-chepo webcam incorporating 4LEDs for low lighting usage. "lsusb" sees the camera as "Omnivision Technologies, Inc". The drivers needed to make it work are the ov51x and ov519_decomp modules.

I assume in this description that your camera is seen on the USB bus, otherwise yuo have to activate and make sure that USB works properly by activating the bus. You can find in this site enough descriptions on how to do that..

Once the cam is seen on the USB bus, the following procedure gives you a fuly functional cam on your Ubuntu 6.06 dapper machine:

1. Get the linux headers for your system, so that you can compile the drivers once you downloaded them. To do this, open a terminal window (Applications -> Terminal on XUbuntu) and type

sudo apt-get install build-essential linux-headers-`uname -r`

2. Get the modules for your webcam:

wget [http://www.rastageeks.org/downloads/...g-0.5.4.tar.gz](http://www.rastageeks.org/downloads/...g-0.5.4.tar.gz)

Ensure the drivers landed into a directory you know

3. Move to the directory where your downloaded drivers are, and extract the source files from the tar files.

tar -xvf ov51x-jpeg-0.5.4.tar.gz

4. Change directory to where your sources are:

cd ov51x-jpeg-0.5.4

5. Compile and install the modules:

sudo make install

This will compile the drivers and install them into the subdirectory of /lib/modules/your-linux-version called extra

6. If all went well, we can install the modules by hand now:

sudo modprobe videodev
sudo modprobe i2c_core
sudo insmod /lib/modules/`uname -r`/extra/ov51x.ko
sudo insmod /lib/modules/`uname -r`/extra/ov519_decomp.ko

7. test your installation by using a camera viewing application, such as xawtv.

If all goes well, you will be able to see the output of your webcam in xawtv.

Now comes the tricky part: making such modules permanent, so that your machine recognizes the Hercules webcam both at bootup as well when you plug it in. The problem here with respect to other module installations is that for some obscure reason, the ov519_decomp module insists in loading the ov511 module when loading through modprobe, and ov511 knows nothing of some of the functions in ov519_decomp and therefore complains.

We will thus load ov51x normally through modprobe, but we will load ov519_decomp through insmod. Let us look at the steps to do this:

1. Make sure you load the vidoedev and i2c_core modules at bootup: to do this, in the terminal type:

sudo vi /etc/modules

We use here vi, but you can actually substitute vi with any other text editor of your preference (I know, I am old and I used vi for decades ;-P). At the end of the files, add the following two lines:

videodev
i2c_core

Now save the file and quit the editor. This will guarantee that from now on at bootup the videodev and the i2c_core modules are loaded.

2. Tell Ubuntu what to do whenever it notices the camera is plugged in:

sudo touch /etc/modprobe.d/ov51x
sudo vi /etc/modprobe.d/ov51x

add to the file the following line:

install ov51x /sbin/modprobe --ignore-install ov51x; insmod /lib/modules/`uname -r`/extra/ov519_decomp.ko

This has to be ONLY on one line.
Save the file and quit the editor.

And voila, at next rebbot your Hercules Classic webcam is there, ready to use.... Have fun!


But when I execute the last commands, I got this error:

```

alexander@alexander-laptop:~/ov51x-jpeg-1.5.4$ sudo insmod /lib/modules/`uname -r`/extra/ov51x.ko
[sudo] password for alexander:
insmod: can't read '/lib/modules/2.6.22-14-generic/extra/ov51x.ko': No such file or directory

```

What could be the problem of that? The only file in the extra folder is ov51x-jpeg.ko

When I look to the syslog when I insert the webcam, I got this:

```

[ 4073.000000] usb 5-3.4: new full speed USB device using ehci_hcd and address 7
[ 4073.092000] usb 5-3.4: configuration #1 chosen from 1 choice
[ 4073.092000] /home/alexander/ov51x-jpeg-1.5.4/ov51x-jpeg-core.c: USB OV519 video device found

```

Thank you at advance,

---

### Post by Reeva on 2007-12-27
Nobody has the solution? :$

---

### Post by jazzgossen on 2008-01-04
This is just a guess, but you could try to run "./configure" before you do the "make install". 

You can also do "locate ov51x.ko" to see if the file was created somewhere else when you did the last make.

---

### Post by jazzgossen on 2008-01-05
I just bought a Hercules Deluxe myself, but it seems that the version I got doens't work with Linux. 

When I do "lsusb", the camera is identified as "06f8:3008 Guillemot Corp.", and according to the OV driver installation instructions [over here]("https://help.ubuntu.com/community/Ov51x"), the camera should be identified as "Omnivision Technologies". So I guess that Hercules changed the chip in the camera, and I haven't found a Linux driver for this Guillemot chip. 

Bummer.

By the way, I also found [this list]("http://alpha.dyndns.org/ov511/cameras.html") of cameras that work with the OV driver.

---

### Post by jazzgossen on 2008-01-10
I exchanged the Hercule for a Logitech Quickcam Pro. Works great.

---

### Post by _sluimers_ on 2008-01-11
instead of  
sudo modprobe videodev
sudo modprobe i2c_core
sudo insmod /lib/modules/`uname -r`/extra/ov51x.ko
sudo insmod /lib/modules/`uname -r`/extra/ov519_decomp.ko

it's:
sudo modprobe ov51x-jpeg

So all you have to type is sudo modprobe ov51x-jpeg and your camera is ready to go.
Reason is the version you're using and the one in the guide.. look REAL closely :D.

Thanks by the way, I had to re-install it myself :).

---

### Post by eljaumet on 2008-03-18
Hello, I've tried this module, and works for me in this Hercules Deluxe camera if I test it with Java Media Framework. But if try to use it in skype 2.0 for linux, or aMSN a don't get the image, however sound recording is available in skype.

Any ideas?

Thanks, it is a good job

---

