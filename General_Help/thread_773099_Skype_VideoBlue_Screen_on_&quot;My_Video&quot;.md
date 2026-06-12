---
title: "Skype Video/Blue Screen on &quot;My Video&quot;"
date: 2008-04-28
forum: General Help
---

### Post by X Driver on 2008-04-28
I just loaded Hardy Heron and all was well with Skype. I went to use it today and now I have a blue screen where my video should be. Other party can see my video, I can see it for a split second when it first starts, then it turns blue. In the test mode, same thing. I see my video, then it gets covered with a blue screen. And that's what it's doing, covering my video. 

In the test video mode in Skype, you can click on your video image and enlarge it. When I do this, I can see the top left corner of my video, the rest is blue.

I have started messing with Compiz since I've installed Skype. I hope this isn't what's doing it because it's way to cool to get rid of, and I don't look that great anyway. :)

I'm new to Ubuntu, so I'm kind of stuck.


Does anyone have any workarounds so that I can still use Compiz and get these problems fixed?

Any help would be appreciated.

Thanks,
Sam


NOTE: If I turn off Compiz, the video in Skype works fine.

---

### Post by X Driver on 2008-04-29
Any helP?

---

### Post by ironwolfe on 2008-04-29
What is your webcam?  Also do you know what driver you are using? V4L?

also try the following program to test:

```
sudo apt-get install camorama

```

It is likely skype, but I want to know if the camera is set up properly first.  Skype can only take a certain feed from the camera - it IS beta after all.

If camorama works then we know the webcam and Xorg (video) are fine and it is skype.  depending on which camera (driver) there may be a way to trick skype - but lets start with camorama.

I run compiz and this would be a first for me if compiz was the problem.  I am betting you have a logitech camera ;)

---

### Post by X Driver on 2008-04-29
Ironwolfe,

It's a Chicony on a Toshiba Satellite U305-S5077.


I tried a bunch of things including loading a bad video driver that I finally was able to get rid of and get back to my original driver.

So then I completely uninstalled Compiz, ran sudo dexconf, and then Skype worked fine. So, why not try it again. Reinstall Compiz, setup the same way, and Skype does it again.

Out of frustration, I quit for a while, decide to load a couple of programs, Amarok and KPDF. Now I don't have any idea what this has to do with my problem, but my video is now working in Skype. Now if I turn it off and it quits agian I'll be pissed.

Update: It quit again.

---

### Post by ironwolfe on 2008-04-30
Trust me run camorama - see if it also works.

If it doesn't work then we have to narrow down further.

What driver are you using?  post the results of:

```
sudo lsmod
```

found this thread that seems to suggest your webcam is problematic...
[HTML]http://ubuntuforums.org/showthread.php?t=498571[/HTML]

> Google for and compile the uvcvideo driver, and grab the luvcviewer program. I got it to display video by running this:

./luvcview -f yuv -w

I would try the command - but don't get your hopes up - it worked with a logitech 5000 pro - but I could never get skype to work.

Here is another possible solution - worked for some...

>  Re: Toshiba A205---Chicony USB 2.0 webcam doesn't work
I had the same problem on laptop Toshiba A200 and was searching for a long time for driver and finally resolved! Everything is working!

Visit site [http://mxhaard.free.fr/spca5xx.html](http://mxhaard.free.fr/spca5xx.html)
In list you can find that chicony microchip is based on sn9c1xx chips driver.
You can download driver for sn9c1xx directly from here: [http://www.linux-projects.org/downlo...untu1_i386.deb](http://www.linux-projects.org/downlo...untu1_i386.deb)
This driver is written recently and actually it is new.
relative site is: [http://www.linux-projects.org/module....php?op=&cid=7](http://www.linux-projects.org/module....php?op=&cid=7)

I hope it works for you!

V.F.

it sounds like you will need the spca5xx driver to get this camera to work.  run this command to make sure you have the right USB ID - post the results of this command

```
sudo lsusb
```

---

### Post by X Driver on 2008-04-30
Thanks Ironwolfe.

I've tried some of this stuff already. Camorama didn't work.
I did get get luvcview to work the other day, but same thing. I could see the top left corner of the video, the rest was cover with blue.

I'm thinking about starting over and reloading Hardy. I've messed up the Compiz and can't get it right even with multiple complete removals and reinstalls.

Thanks

---

### Post by ironwolfe on 2008-05-01
Did you try the spca5xx driver?

Let me know how the reinstall works - hopefully it will get the webcam working.  I have a feeling the driver (perhaps a module in the kernel) is messing things up.  I have a feeling you may need to stop the module (driver) that is default and install the spca driver.

BTW, I am sticking to gutsy for a while longer... ;)

Good luck.

---

### Post by X Driver on 2008-05-01
Ironwolfe,

I just got the driver in a tar.gz file. I'm new to Linux. Is there some easy instructions you could give me on how to load this new driver?

Thanks,
Sam

---

### Post by X Driver on 2008-05-05
I'm still looking for an answer to this problem.

Has anybody else experienced this problem?

Thanks,
Sam

---

### Post by ironwolfe on 2008-05-10
> **X Driver said:**
> Ironwolfe,

I just got the driver in a tar.gz file. I'm new to Linux. Is there some easy instructions you could give me on how to load this new driver?

Thanks,
Sam

Thanks for letting me know you are new to Linux - It seems that spca5xx is already in the kernel so this is not the problem.  I think I know what is wrong but first I need to know the exact usb ID for the webcam and some other info.  

Paste the following into your terminal window by holding down SHIFT-CONTROL-V type :
```
lsusb
```

highlight all the text and post it here.

Do the same with the output from this command
```
lsmod
```

And once again 

```
uname -a
```

Last time:

```
cat /etc/lsb-release
```

The first command will tell us what exact camera you are using.  The second command will tell us what drivers (modules) you have already installed. ;) the third will tell me what kernel you are running so we know which driver you need.  Last one is the release of ubuntu you are running.

Here is the latest from the skype dev team:

> Known Issues with Workarounds/Solutions
* Many 64-bit OS users have reported their device not being detected in Skype. - Read more
* ov511/ov51x_jpeg users can find patches to these drivers in our Webcam driver survey thread which add support for Skype and also 64-bit support. [ov511, ov51x_jpeg]
* Syntek Driver (stk11x) has been updated to provide YUV support in 1.2.0. And an additional fix for red/blue shifting will be in 1.2.1. Read more
* Cameras that only capture in RGB may miraculously begin working if run through mrk.its' excellent Skype video hijacker program. This program can also apply effects to video for other users. Read more

Recommended Minimum Driver Version
* ATi fglrx 8.43.x or Catylyst 8.01 or later. Note: Newer drivers may require Option "TexturedVideo" "on" in your /etc/X11/xorg.conf
* uvc webcam driver r166 or later. r166 is recommended currently.
* gspca webcam driver 01.00.16 or later (also known as 20070426). Later is better.

Please also start a log for skype:

```
mkdir ~/.Skype/Logs
```
post any files that appear there when you restart skype and try video....

---

### Post by X Driver on 2008-05-10
Thanks for the help Ironwolfe. 

Again, this problem only occurs when I run the cube in Compiz.
I've loaded the Compiz Fuzion Icon and just turn off Compiz and run Metacity when I need the camera, and then it works fine.
I would still like to fix this problem if I can.

Thanks again.  

Here's the information.



Bus 005 Device 003: ID 04f2:b008 Chicony Electronics Co., Ltd 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 046d:c521 Logitech, Inc. MX620 Laser Cordless Mouse
Bus 001 Device 001: ID 0000:0000 


 lsmod
Module                  Size  Used by
ipv6                  267780  10 
af_packet              23812  4 
binfmt_misc            12808  1 
i915                   32512  2 
drm                    82580  3 i915
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
bluetooth              61156  4 rfcomm,l2cap
ppdev                  10372  0 
acpi_cpufreq           10796  2 
cpufreq_powersave       2688  0 
cpufreq_ondemand        9740  1 
cpufreq_stats           7104  0 
freq_table              5536  3 acpi_cpufreq,cpufreq_ondemand,cpufreq_stats
cpufreq_conservative     8712  0 
cpufreq_userspace       5284  0 
container               5632  0 
dock                   11280  0 
sbs                    15112  0 
sbshc                   7680  1 sbs
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
ndiswrapper           193500  0 
sbp2                   24072  0 
parport_pc             36260  0 
lp                     12324  0 
parport                37832  3 ppdev,parport_pc,lp
joydev                 13120  0 
uvcvideo               58116  0 
compat_ioctl32          2304  1 uvcvideo
videodev               29440  1 uvcvideo
v4l1_compat            15492  2 uvcvideo,videodev
v4l2_common            18304  2 uvcvideo,videodev
evdev                  13056  7 
psmouse                40336  0 
serio_raw               7940  0 
iTCO_wdt               13092  0 
sdhci                  19076  0 
iTCO_vendor_support     4868  1 iTCO_wdt
ricoh_mmc               4352  0 
mmc_core               51460  1 sdhci
pcspkr                  4224  0 
snd_hda_intel         344728  3 
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78596  2 snd_hda_intel,snd_pcm_oss
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_hwdep              10500  1 snd_hda_intel
snd_seq_dummy           4868  0 
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
snd_rawmidi            25760  1 snd_seq_midi
video                  19856  0 
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
output                  4736  1 video
wmi_acer                9644  0 
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
battery                14212  0 
ac                      6916  0 
button                  9232  0 
snd                    56996  17 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
soundcore               8800  1 snd
intel_agp              25492  1 
agpgart                34760  3 drm,intel_agp
ext3                  136712  1 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
usbhid                 31872  0 
hid                    38784  1 usbhid
sg                     36880  0 
sr_mod                 17956  0 
cdrom                  37408  1 sr_mod
sd_mod                 30720  3 
pata_acpi               8320  0 
ata_generic             8324  0 
ata_piix               19588  2 
libata                159344  3 pata_acpi,ata_generic,ata_piix
scsi_mod              151436  5 sbp2,sg,sr_mod,sd_mod,libata
ohci1394               33584  0 
ieee1394               93752  2 sbp2,ohci1394
ehci_hcd               37900  0 
uhci_hcd               27024  0 
usbcore               146028  6 ndiswrapper,uvcvideo,usbhid,ehci_hcd,uhci_hcd
r8169                  32900  0 
thermal                16796  0 
processor              36872  4 acpi_cpufreq,thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50580  3 

 uname -a
Linux sam-laptop 2.6.24-16-generic #1 SMP Thu Apr 10 13:23:42 UTC 2008 i686 GNU/Linux



 cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.04
DISTRIB_CODENAME=hardy
DISTRIB_DESCRIPTION="Ubuntu 8.04"

---

### Post by ironwolfe on 2008-05-10
Based on what you posted:

```
uvcvideo 58116 0
compat_ioctl32 2304 1 uvcvideo
videodev 29440 1 uvcvideo
v4l1_compat 15492 2 uvcvideo,videodev
v4l2_common 18304 2 uvcvideo,videodev
```

it looks like you are running an uptodate driver.  You may want to try a subversion or svn driver - these are the latest from the developers... not yet in the kernel, which is where yours is.  Based on discussions with others, you are getting better than most - simply by shutting off compiz.

If you are feeling adventurous and want to try the latest driver...:

```
cd ~
```

```
sudo apt-get install subversion
```

```
sudo svn checkout svn://svn.berlios.de/linux-uvc/linux-uvc/trunk
```

```
sudo apt-get install linux-headers-`uname -r`
```

```
cd trunk
```

```
make
```

```
sudo install
``` or checkinstall - if you wish

Open the the makefile in a text editor 

```
gedit Makefile
```

and change :

INSTALL_MOD_DIR := usb/media

to

INSTALL_MOD_DIR := ubuntu/media/usbvideo

then run

```
sudo make install
```

Insert Modules
```
sudo modprobe -r uvcvideo
```
```
sudo modprobe uvcvideo
```

if you want you can clean up the "trunk folder"

```
rm -r ~/trunk/*
```


let us know how it goes... make a backup of you system if you can.

---

### Post by X Driver on 2008-05-10
Thanks Ironwolfe.

I think I may give it a try, I need to think about it. So far everything is working pretty good with my Ubuntu installation except this Skype problem. I only use it occasionally so I need to decide if I want to take the chance of messing up my system or settling for the way it is.

Another reason to settle is that it seems that Compiz slows my system a little bit. Should that be happening?

If I try it and it doesn't work, is it difficult to revert back to the old driver?

Thanks,
Sam

---

### Post by ironwolfe on 2008-05-11
> **X Driver said:**
> Thanks Ironwolfe.

I think I may give it a try, I need to think about it. So far everything is working pretty good with my Ubuntu installation except this Skype problem. I only use it occasionally so I need to decide if I want to take the chance of messing up my system or settling for the way it is.

Another reason to settle is that it seems that Compiz slows my system a little bit. Should that be happening?

If I try it and it doesn't work, is it difficult to revert back to the old driver?

Thanks,
Sam

I am not familiar with Hardy yet, compiz is rock solid on Gutsy for me - it is mostly GPU driven.  

The modules are in /lib/modules/2.6.24-16-generic/kernel/drivers/media/video/ so you need to do:

```
gksudo nautilus
``` to do a backup with a GUI. or from the command line:

```
mkdir ~/backupmodules
sudo cp -dpRxv /lib/modules/2.6.24-16-generic/kernel/drivers/media/video ~/backupmodules
```

I installed the uvcvideo drivers from svn on my test system and it works well.  I don't have your webcam though.  skype is saying that as long as you are above version 166 you are ok - you are running Hardy so you are above revision 166.  To find out:
```
modinfo uvcvideo
``` and scroll up to the version info.

I hope this all helps.

good luck

---

### Post by ntlam on 2008-05-13
> **X Driver said:**
> Ironwolfe,

It's a Chicony on a Toshiba Satellite U305-S5077.


I tried a bunch of things including loading a bad video driver that I finally was able to get rid of and get back to my original driver.

So then I completely uninstalled Compiz, ran sudo dexconf, and then Skype worked fine. So, why not try it again. Reinstall Compiz, setup the same way, and Skype does it again.

Out of frustration, I quit for a while, decide to load a couple of programs, Amarok and KPDF. Now I don't have any idea what this has to do with my problem, but my video is now working in Skype. Now if I turn it off and it quits agian I'll be pissed.

Update: It quit again.

I have the same laptop but haven't used the camera for a while. Hope that you keeping updating the issue solution.

---

### Post by X Driver on 2008-05-15
> **ntlam said:**
> I have the same laptop but haven't used the camera for a while. Hope that you keeping updating the issue solution.

This problem only occurs when I run the cube in Compiz.
I've loaded the Compiz Fuzion Icon and just turn off Compiz and run Metacity when I need the camera, and then it works fine. Actually lately, I don't even run the cube at all.


I haven't tried Ironwolfe's last suggestion to load the newest subversion driver, only because I haven't had the time, and I'm also not sure if I want to risk it.

Overall my machine runs great and I don't want to mess it up. While the cube is neat and fun to get it to work, I really didn't use it except for the wow factor.

I've read a lot of your previous post trying to get my wireless to work on Gusty.I never could figure it out. So I gave up until Hardy arrived. I then found some real good cut and paste instructions for ndsiwrapper. 

Just a few little bugs like my built in microphone doesn't work. Have you got yours to work?

---

### Post by ntlam on 2008-05-17
Nope, My microphone is not working either. That's sad because yesterday I had to switch to windows to talk.

---

### Post by ntlam on 2008-05-17
I got wireless work since I started with feisty by using ndiswrapper. I also posted the solution somewhere...don't remember exactly where...

---

### Post by X Driver on 2008-05-17
Hey ntlam,

Does your volume wheel on the left side control the system volume, or just headset volume when one is plugged in? Mine controls headset, not system, but I'd swear at one time it did control system volume.

Thanks

---

