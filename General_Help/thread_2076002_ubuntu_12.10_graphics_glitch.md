---
title: "ubuntu 12.10 graphics glitch"
date: 2012-10-25
forum: General Help
---

### Post by Twilk73 on 2012-10-25
First time linux user so if you can help please be detailed. Also I reviewed the 12.10 bugs thread but it wasnt very helpful to me. 

Anyway, I installed the 12.10, 64 bit version of ubuntu and everything seems to be working great except the video card? When I go into the ubuntu store images and text become distorted and unreadable. Over time they either fix them selves or stay distorted untill I reload the program. Sometimes reloading takes several tries to get it fixed. I dont know what is causing this but I did notice that the system is not recognizing my nvidia 670m video card. 

My machine is an ASUS G75V, with 12g's of ram 500mb hard drive and nvidia 670m graphics card. The original OS was windows 7 64 bit and thus that is the reason I choose 64 bit unbuntu 12.10. 

Thanks, Twilk

---

### Post by Twilk73 on 2012-10-25
Further details:

The details program shows graphics unknown, experience standard,

The software source/additional drivers says, Nvidia corporation; unknown 
(then gives me the options for)

-Using nvidia binary xorg driver, kernel module and VDPAU library from nvidia-current (proprietary, tested)

-Using X.org X server - Nouveau display driver from xserver-xorg-video-nouveau (open soruce)

-Using nvidia binary xorg driver, kernel module and VDPAU library from nvidia-current-updates (proprietary)

-Using Experimental nvidia binary xorg driver, kernel module and VDPAU library from nvidia-experimental-304 (proprietary)

The default option that was choosen was the x.org open source option.

Thanks again, Thomas

---

### Post by danielbauwens on 2012-10-25
You might want to update your kernel?

---

### Post by Twilk73 on 2012-10-25
Kernel? The linux kernel or is there a kernel for the nvidia driver?

---

### Post by garginis on 2012-10-25
Did you install graphic driver?If no, type this in terminal:
```
sudo apt-get install nvidia-current
```

---

### Post by Twilk73 on 2012-10-25
Ok I ran the sudo entry above and that switched me to this option

-Using nvidia binary xorg driver, kernel module and VDPAU library from nvidia-current (proprietary, tested)

Before it was using this option.

-Using X.org X server - Nouveau display driver from xserver-xorg-video-nouveau (open soruce)

The problem is also solved now because I am not getting the screen tweaking so thats awesome. However in details its still showing unknown driver and standard experience. Yesterday I experimented with switching to the drivers manually by just clicking the options and that also switched me, but everytime I restarted the computer the screen was blown up and none navigational. 

Moving on I have a few questions. How did you know to use this sudo line. Was it in fix it thread, was it something thats just standard knowledge?

---

### Post by vandorjw on 2012-10-26
that specific command is fairly standar knowledge.

I'll explain in detail what it did.

sudo --  allows users to run programs with the security privileges of another user, usually root. 

apt-get -- the program we wanted to run. apt-get is a tool to automatically update your Debian machine and get and install debian packages/programs! 
(Ubuntu is a Debian Derivative)

install -- an option givin to 'apt-get' 
--other options include, remove, re-install, purge...

nvidia-current -- the nvidia driver. 

I hope that made sense.


If you are looking for a program, and cannot find it in the Software center, please try

sudo apt-cache search "name of what you looking for"

apt-get does not have a search function.

Cheers

---

### Post by Twilk73 on 2012-10-26
> **vandorjw said:**
> that specific command is fairly standar knowledge.

I'll explain in detail what it did.

sudo --  allows users to run programs with the security privileges of another user, usually root. 

apt-get -- the program we wanted to run. apt-get is a tool to automatically update your Debian machine and get and install debian packages/programs! 
(Ubuntu is a Debian Derivative)

install -- an option givin to 'apt-get' 
--other options include, remove, re-install, purge...

nvidia-current -- the nvidia driver. 

I hope that made sense.


If you are looking for a program, and cannot find it in the Software center, please try

sudo apt-cache search "name of what you looking for"

apt-get does not have a search function.

Cheers

Thanks man that makes a lot of sense.

---

### Post by Geezanansa on 2012-10-26
Hello Twilk73 and hope you are enjoying ubuntu.

I have been (trying to ) using ubuntu for a couple of years and still regularly search for this [http://https://help.ubuntu.com/community/UsingTheTerminal](http://https://help.ubuntu.com/community/UsingTheTerminal)

To enjoy ubuntu even more; as mentioned,  you could update your kernel.  What kernel you use ultimately shapes what goes into apt package by default.

Ubuntu default settings for updates do not have proposed updates activated.  If you want you could search for proposed ubuntu.  
[https://help.ubuntu.com/community/UbuntuUpdates](https://help.ubuntu.com/community/UbuntuUpdates)

so to update your kernel just activate proposed updates
[https://wiki.ubuntu.com/Testing/EnableProposed](https://wiki.ubuntu.com/Testing/EnableProposed)
 then use software updater to update everything and reboot.  Select a driver using additional drivers and reboot. Once logged in again open a terminal window and do a ```
sudo nvidia-xconfig
``` and reboot and enjoy.

I have not upgraded to 12.10 yet but am looking forward to it and will be very soon.
The 310 driver in 12.04 is jaw droppingly awesome.

Trying different drivers will make different things happen at boot time. The troubleshooter at the beginning of this thread   [http://ubuntuforums.org/showthread.php?t=1743535&highlight=blank+screen](http://ubuntuforums.org/showthread.php?t=1743535&highlight=blank+screen) has proven to be very useful.
64bit should be a quicker working system for most tasks however if you intend using any windows applications/games  running through wine then in general a 32bit  will behave more predictably.   How is 64bit doing for you?   It is while since i tried 64bit so 12.10 would be a good place to try:)  No harm in trying both on 64bit mobo/cpu.

kind regards and ttfn

---

### Post by Twilk73 on 2012-10-26
12.10 pretty much came working out of the box. I removed a few programs I had no need for I only tried 12.04 for a short time but so far the only thing iv really noticed to be different is the lock screen lacks the option to change the OS layout. 64bit thus far the only thing not working out of the box is the sound, the video card didnt show up and the back lit keyboard seems to come on automatically at start up regardless of what I set it to before shut down. All things I am sure will be fixed. I cant really give you a good description of how well 12.10 64 bit is I havent really dug in yet and my experience here is minimal lol. 

Thanks though for the tips and yes I will enjoy linux. Any programs you recommend to check out. Tools, or just useful programs?

---

### Post by Twilk73 on 2012-10-29
> **Geezanansa said:**
> Hello Twilk73 and hope you are enjoying ubuntu.

I have been (trying to ) using ubuntu for a couple of years and still regularly search for this [http://https://help.ubuntu.com/community/UsingTheTerminal](http://https://help.ubuntu.com/community/UsingTheTerminal)

To enjoy ubuntu even more; as mentioned,  you could update your kernel.  What kernel you use ultimately shapes what goes into apt package by default.

Ubuntu default settings for updates do not have proposed updates activated.  If you want you could search for proposed ubuntu.  
[https://help.ubuntu.com/community/UbuntuUpdates](https://help.ubuntu.com/community/UbuntuUpdates)

so to update your kernel just activate proposed updates
[https://wiki.ubuntu.com/Testing/EnableProposed](https://wiki.ubuntu.com/Testing/EnableProposed)
 then use software updater to update everything and reboot.  Select a driver using additional drivers and reboot. Once logged in again open a terminal window and do a ```
sudo nvidia-xconfig
``` and reboot and enjoy.

I have not upgraded to 12.10 yet but am looking forward to it and will be very soon.
The 310 driver in 12.04 is jaw droppingly awesome.

Trying different drivers will make different things happen at boot time. The troubleshooter at the beginning of this thread   [http://ubuntuforums.org/showthread.php?t=1743535&highlight=blank+screen](http://ubuntuforums.org/showthread.php?t=1743535&highlight=blank+screen) has proven to be very useful.
64bit should be a quicker working system for most tasks however if you intend using any windows applications/games  running through wine then in general a 32bit  will behave more predictably.   How is 64bit doing for you?   It is while since i tried 64bit so 12.10 would be a good place to try:)  No harm in trying both on 64bit mobo/cpu.

kind regards and ttfn

I got itchy and did this

the 310 driver is freaking sweet. Thanks, man!

---

### Post by ARooster on 2012-11-15
> **Twilk73 said:**
> Any programs you recommend to check out. Tools, or just useful programs?

Synaptic Package Manager is great for easing the navigation through the repositories. It's essentially a graphic front end for Advanced Packaging Tool (remember the apt-get command in terminal?)

---

### Post by tamccullough on 2012-11-15
Ok, I'm a little confused.

So maybe I could get some help from others here in this thread.

I too installed 12.10 64 bit on a multiboot machine.

AMD Phenom(tm) II X6 1090T Processor × 6 
16 GiB
GTX 460

and still I am having problems with the nvidia drivers.  I first tried the drivers that are default with a new install and then I tried the drivers found in the X Updates ppa and still with no success.

My resolution gets fudged and compiz doesn't appear to work.  Panels aren't displayed.

So I have had to use the default Nouveau driver just to fool with 12.10.

I also have 12.04 and Win 7 installed on the same system. No problems.

I have been using ubuntu for a while now, since 9.04 and I have never encountered any issues with nvidia drivers.

Could I get some help, or maybe someone could direct me to an appropriate thread?

Cheers

---

