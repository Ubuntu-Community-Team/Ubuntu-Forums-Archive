---
title: "Video Tearing 13.10 with Nvidia 331.49 drivers"
date: 2014-02-26
forum: General Help
---

### Post by i0ls on 2014-02-26
I recently threw together another rig using some new and some parts from my htpc. The video card GTX 650 TI, i3 3.4, and ram 8gb ddr3 1333 g.skill ripsaw's. 
Everything in the htpc ran nice and smooth, in xbmcbuntu 13.10. I keep getting video tearing while gaming, youtube etc. 
I did some google searching and a few guys said to make sure the v sync is on, Nvidia X Server Settings says it is. I also changed Power Mizer to performance. I swapped the dvi for an hdmi cable and played with the response time in the monitors settings. A few people said to put some extra stuff in /ect/environments which seems to have done nothing as well..
Has anyone else had this happen? What have I overlooked?

I am Editing this to make things easier to find: Here is how I went about solving this issue (or making things tolerable).

~Tearing in Google Chrome with Youtube, and various online videos.

      Navigate to chrome://chrome-urls/

      Enable Override software rendering list Mac, Windows, Linux, Chrome OS:

      Restart Chrome and my videos play flawlessly!!.

~my xorg.conf file was blank (I am guessing from purging and re installing drivers a few times) and things from nvidia config were not getting saved or applied.
 
      I made a new one simply in nvidia config app, although there was an error at first I was able to save the to the xorg.conf file and all is running good.

~The powermizer would keep reseting itself whenever i rebooted, I kept putting it on max performance and seemed to smooth things out without getting very hot.

      Following the instructions in this thread it seems that now when I reboot my powermizer is set to max performance
          [http://forums.opensuse.org/showthread.php/410089-nvidia-powermizer-how-tweak](http://forums.opensuse.org/showthread.php/410089-nvidia-powermizer-how-tweak)


Hopefully this helps someone out!

---

### Post by papibe on 2014-02-26
Hi i0ls.

Is XBMCbuntu runs compiz underneath as Ubuntu does?

If so, you may need also set a few options in ccsm (Compiz Config Settings Manager). Take a look at this 2 threads:  [HOWTO: Get rid of video TEARING in Compiz with NVIDIA]("http://ubuntuforums.org/showthread.php?t=1390284&highlight=tearing") (first post), and [NVIDIA, VDPAU, tearing and an XBMC solution]("http://ubuntuforums.org/showthread.php?t=1683875&highlight=nvidia+tearing") (post 4).

Hope it helps. Let us know how it goes.
Regards.

---

### Post by i0ls on 2014-02-26
> **papibe said:**
> Hi i0ls.

Is XBMCbuntu runs compiz underneath as Ubuntu does?

If so, you may need also set a few options in ccsm (Compiz Config Settings Manager). Take a look at this 2 threads:  [HOWTO: Get rid of video TEARING in Compiz with NVIDIA]("http://ubuntuforums.org/showthread.php?t=1390284&highlight=tearing") (first post), and [NVIDIA, VDPAU, tearing and an XBMC solution]("http://ubuntuforums.org/showthread.php?t=1683875&highlight=nvidia+tearing") (post 4).

Hope it helps. Let us know how it goes.
Regards.

Thanks for the reply! You have helped me out before I appreciate it.
I had everything except compiz config installed and manually entering the refresh rate done or checked off already.
I rebooted after completing and fired up big buck bunny and i am still tearing like a sob. Though that's not the only place that happens its the easiest and one of the most apparent. I don't really get it.. I got the same results regardless of which Nvidia drivers I had selected.
Ideas?

Edit: As far as I know xbmcbuntu is stripped down and runs XBMC as its main display session. There is a desktop environment though, and I think its XFCE but I am not 100% on that.

---

### Post by papibe on 2014-02-26
Do yo have multiple monitors?

Regards.

---

### Post by i0ls on 2014-02-27
Just one monitor, a samsung syncmaster p2770fh.
I read a thread about someone having luck by manually entering the horizontal and vertical rates in xorg.conf, but that someone was not me. I am beginning to loose my sanity on this one.
Thanks

EDIT:
I just purged and reinstalled the drivers. When I install the 331.49 drivers and reboot I end up in low graphics mode. ctrl+alt+f1 and sudo apt-get remove --purge bumblebee and then reboot and I have an x server running again.
Would this bumblebee business have anything to do with why my screen is tearing its own @$$ off?
thanks
ps. pardon my insanity with this, its been several hours of no results.

---

### Post by papibe on 2014-02-27
Could you install this:
```
sudo apt-get install wmctrl
```

Then run this command and post the results?
```
wmctrl -m

```
Regards.

EDIT: regarding bumblebee, just make sure the that the Nvidia card is active and the drivers is loaded. You may be using the Intel graphics.

---

### Post by i0ls on 2014-02-27
i tried to install the drivers from the website. big mistake
after booting into the recovery console and purging nvidia-* i now get a login screen and a black with a curser ctrl+alt+f1 i get an error
[4.518183] system-udevd[433]: Failed to apply ACL on /dev/dri/card1: no such directory

now i am really in over my head. i hope i am not out this whole weeks work of setting up this install :(

---

### Post by papibe on 2014-02-27
Check if [this]("http://ubuntuforums.org/showthread.php?t=2169638&p=12765972#post12765972") helps to get your desktop back.

Regards.

---

### Post by i0ls on 2014-02-27
no dice :( :(

EDIT:!!
So glad that I made that clone of my hard drive right before i screwed around with this. I had forgot about it last night.
I am sure restoring a clone of my drive isnt the best for the ssd. 

Edit #2
re installed the drivers from the ppa: I am back to where the post started. Here is the updated info.

:~$ wmctrl -m
Name: Compiz
Class: N/A
PID: N/A
Window manager's "showing the desktop" mode: OFF

---

### Post by i0ls on 2014-02-28
I have googled this again and again and here is what I know/have in common.
On more than one occasion the op's and myself all have gtx 550 it/ gtx 550 (is this common with only this card? or is it like when you buy a certain car and then notice them everywhere and that never happened before.)
The asrock h77 chipset. Which I have tore through the bios and looked for a way to determine without a doubt that the igpu is disabled without luck.
And pretty much any flavor of ubuntu/xbuntu etc etc..

So 2 days of going in circles, where should I logically begin again? anyone plz??

---

### Post by i0ls on 2014-02-28
I have also noticed that my xorg.conf file is completely blank. should this be like this?

---

### Post by papibe on 2014-02-28
Let's check some basics.

Could you post the output of these commands?
```
lspci -nnk | grep -iA2 vga

dpkg -l | grep nvidia

lsmod | grep -E 'nvidia|nouv'

apt-cache policy libvdpau1

apt-cache policy vdpau-va-driver

```
Are videos showing tearing too?

Regards.

---

### Post by i0ls on 2014-02-28
hi again, thank you for your help. i am giving this my best shot here and really trying to do every solution on google that i find and crossing my fingers.
i have tearing on videos, and open gl games, sorry to spam this. not sure how else to post it...


:~$ lspci -nnk | grep -iA2 vga
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GK106 [GeForce GTX 650 Ti] [10de:11c6] (rev a1)
	Subsystem: ZOTAC International (MCO) Ltd. Device [19da:5263]
	Kernel driver in use: nvidia


:~$ dpkg -l | grep nvidia
rc  nvidia-304                                    304.119-0ubuntu1~xedgers13.10.1               amd64        NVIDIA legacy binary driver - version 304.119
rc  nvidia-319                                    331.49-0ubuntu1~xedgers13.10.3                amd64        Transitional package for nvidia-319
ii  nvidia-331                                    331.49-0ubuntu1~xedgers13.10.3                amd64        NVIDIA binary driver - version 331.49
ii  nvidia-common                                 1:0.2.83                                      amd64        transitional package for ubuntu-drivers-common
rc  nvidia-libopencl1-304                         304.119-0ubuntu1~xedgers13.10.1               amd64        NVIDIA OpenCL Driver and ICD Loader library
ii  nvidia-libopencl1-331                         331.49-0ubuntu1~xedgers13.10.3                amd64        NVIDIA OpenCL Driver and ICD Loader library
rc  nvidia-opencl-icd-304                         304.119-0ubuntu1~xedgers13.10.1               amd64        NVIDIA OpenCL ICD
ii  nvidia-opencl-icd-331                         331.49-0ubuntu1~xedgers13.10.3                amd64        NVIDIA OpenCL ICD
ii  nvidia-settings                               331.38-0ubuntu1~xedgers~saucy1                amd64        Tool for configuring the NVIDIA graphics driver
ii  nvidia-settings-319                           331.38-0ubuntu1~xedgers~saucy1                amd64        Transitional package for nvidia-settings


:~$ lsmod | grep -E 'nvidia|nouv'
nvidia              10688804  40 
drm                   297056  2 nvidia


:~$ apt-cache policy libvdpau1
libvdpau1:
  Installed: 0.7-1
  Candidate: 0.7-1
  Version table:
 *** 0.7-1 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) saucy/main amd64 Packages
        100 /var/lib/dpkg/status


:~$ apt-cache policy vdpau-va-driver
vdpau-va-driver:
  Installed: (none)
  Candidate: 0.7.3-2ubuntu1
  Version table:
     0.7.3-2ubuntu1 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) saucy/universe amd64 Packages

---

### Post by i0ls on 2014-02-28
Do you think that installing the nvidia drivers again might help? I am using the open source drivers from the ppa. Though I am a bit apprehensive about installing them as last time the broke my os.
I did a dist-upgrade and it worked on some stuff from the video drivers ppa, but nothing seems to have changed including the driver version.
Is anyone out there solving this issue? i am about to start bashing my face into the keyboard...

---

### Post by i0ls on 2014-02-28
Her is an update:
I messed around with a bunch of settings in csm and tf2 and i have resolved this issue in open gl, for the most part. I mainly enabled any kind of filtering I could find, and tf2 has a separate v sync setting. 

I wish it were that easy to fix everywhere else. I feel like I am ticking the box for v sync and it never apply's it....

---

### Post by i0ls on 2014-03-01
Is there any way to force v sync? Every where that I read talks about ccsm or nvidia config. Is there something that I can add to say /etc/environments or something like that?

---

### Post by i0ls on 2014-03-01
now i have really screwed up my open gl settings.. theres no tearing but it skips and lags and the desktop had tearing say with you-tube etc. 
hate hate hate this bs...

---

### Post by i0ls on 2014-03-02
I am at a loss here....
nobody has an answer or even a suggestion? nothing to be said at all? :(
 feel like buying a windows key almost, and I hate the @#$# out of windows...

---

### Post by i0ls on 2014-03-03
Had another breakthrough today, this time battling nasty tearing in chrome playing hd video in full screen..

*Navigate to chrome://chrome-urls/

*Enable Override software rendering list Mac, Windows, Linux, Chrome OS:

*Restart Chrome and my videos play flawlessly!!.

Now on to everything else.....

---

### Post by i0ls on 2014-03-03
One thing i have noticed.
If I leave the nvidia settings open and play games etc, my card performs like a 180 dollar card and not a 40 dollar card with the power mizer set up high.
If I quit nvidia settings it resets. I found a thread with a post that mentions editing xorg.conf. Issue is mine is blank! nothing there, nobody home...
if i ctrl alt f1 and stop lightdm and run X -configure I end up an error about number of created screens does not match the number of detected devices.
How do I not have an empty xorg.conf?
would that have anything to do with my vsync issues and screen tearing if xorg.conf has an issue with the number of screens??
help a rookie plzzz...

---

### Post by i0ls on 2014-03-03
Here is another update:
it seems that because my xorg.conf file was empty, most of my selections in nvidia settings app were not getting applied. I made another xorg.conf file after finding my original was empty, probably from purging and upgrading nvidia drivers.
Since then things are saved from my settings in the nvidia app.

---

### Post by papibe on 2014-03-03
To save the what you have on nvidia-settings to the X config file do this:
```
gksudo nvidia-settings
```
Make all the adjustments you need, and then press 'Save to X configuration file. Make sure you save to this location:
```
/etc/X11/xorg.conf
```
If gksudo is not installed, use this to isntall it:
```
sudo apt-get install gksu
```
Hope it helps. Let us know how it goes.
Regards.

---

### Post by Bobby Infinity on 2014-04-12
This post solved the video tearing for me.[ https://bbs.archlinux.org/viewtopic.php?pid=1375173#p1375173]("https://bbs.archlinux.org/viewtopic.php?pid=1375173#p1375173")

Just edit your /etc/X11/xorg.conf adding:

```
Section "Extensions"
   Option         "Composite" "Disable"
EndSection
```

---

