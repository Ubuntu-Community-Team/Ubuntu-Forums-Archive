---
title: "Ubuntu 12.04 slow to boot after recent updates"
date: 2014-07-15
forum: General Help
---

### Post by hockeybum27 on 2014-07-15
Specs:
Dell Latitude 256 GB SSD, 8GB RAM
Processor: Intel® Core&#8482; i7-2620M CPU @ 2.70GHz × 4
dual boot (Grub 1.99-21Ubuntu3.15) - Ubuntu is on a 52GB EXT4, I also have a 151 GB NTFS partition that mounts at boot
Release 12.04 (precise) 64-bit
Kernel Linux 3.2.0-67-generic
GNOME 3.4.2

Normally booting this system to Ubuntu is fast, as you might imagine - I'd say somewhere in the neighborhood of 20 seconds or maybe less.  I noticed after a recent (past 2 weeks or so) update, my boot time has gone way up - typically 45 seconds or so.  I don't know how to keep track of a timeline of updates, but I believe that one of the recent updates that occurred around the same time was a GRUB update; I'm not sure.

I'm not sure how to troubleshoot this, but I've seen references to dmesg, and it shows some interesting stuff in there (though I'm not sure I know exactly how to interpret it).  One thing I see is an apparently big delay in the vmnet (I have vmware player v4.0.2, but have not updated that since installation a couple of years ago, since it was quite problematic to do so).  Then the last line is something about DRM.

UPDATE - I still have the issue after the most recent kernel update (0.67).  I am only including the last few lines from the kernel.log below, as it shows the large gap in time (between the last 2 messages about DRM).  My question - what is happening in between?


```

Jul 17 09:18:12 my-ubu-box kernel: [    7.889513] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Jul 17 09:18:12 my-ubu-box kernel: [    8.070098] HDMI status: Codec=0 Pin=5 Presence_Detect=0 ELD_Valid=0
Jul 17 09:18:12 my-ubu-box kernel: [    8.078194] HDMI status: Codec=0 Pin=6 Presence_Detect=0 ELD_Valid=0
Jul 17 09:18:12 my-ubu-box kernel: [    8.086206] HDMI status: Codec=0 Pin=7 Presence_Detect=0 ELD_Valid=0
Jul 17 09:18:12 my-ubu-box kernel: [    8.086323] input: HDA NVidia HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input17
Jul 17 09:18:12 my-ubu-box kernel: [    8.086424] input: HDA NVidia HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input18
Jul 17 09:18:12 my-ubu-box kernel: [    8.086519] input: HDA NVidia HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input19
Jul 17 09:18:12 my-ubu-box kernel: [    8.434873] [drm] Changing LVDS panel from (-hsync, -vsync) to (-hsync, +vsync)
Jul 17 09:18:13 my-ubu-box kernel: [    9.829966] [drm:gen6_sanitize_pm] *ERROR* Power management discrepancy: GEN6_RP_INTERRUPT_LIMITS expected 1a000000, was 12000000
Jul 17 09:18:43 my-ubu-box kernel: [   38.954593] [drm] Changing LVDS panel from (-hsync, +vsync) to (-hsync, -vsync)
```

Any help or direction would be much appreciated; I look at this as a learning experience since I've not spent nearly as much time learning this wonderful OS as I should have, given I've had it for a couple of years.  I always am eager to learn more about how to troubleshoot for myself, and of course that means learning more about the inner workings.

---

### Post by bluelightav on 2014-07-19
You're not alone. We've got several SSD machines running 12.04 and ALL of them are now very slow to boot, went up from ~5 seconds to nearly half a minute. This is ridiculous. I think that the bug got "backported" to all existing 3.x kernels since we're seeing it on 3.11 and 3.13 as well. However, this doesn't happen under 14.04 with the same kernels. **This really needs more attention.** In my experience, the general responsiveness of these machines also went down considerably. They no longer feel like recent hardware (Ivy Bridge i3s and Pentiums with 4-8 GB RAM) with SSDs but like sluggish old HDDs. This is unacceptable.

---

### Post by hockeybum27 on 2014-07-21
bluelightav,

Thanks for the reply - I normally see responses to my posts same day, so I was beginning to wonder if I was the only one with this issue.  I see now that is not the case (though I've not found other posts on the matter).  I'd not thought it was the SSD at all, so thanks for shedding some light on that as well.

Though it sounds as though you're in the same boat (i.e., still dealing with the issue), if you can provide answers/comments/info on the below, I'd be grateful:

- should I report this as an issue more proactively (e.g., launchpad, 'Report a bug', etc.)?  I know I'd likely need more specifics ( see below) to be able to post effectively on this.

- is there any specfic log/logs I can look at that would show me it is the SSD that is the issue?

- do you have an idea of what update might have caused this?

- would it make sense to revert back to a previous kernel (assuming it's the kernel)?  If so, which one?

Thanks again for taking the time to answer!

---

### Post by oldfred on 2014-07-21
This is the 30 sec delay:

>  Jul 17 09:18:13 my-ubu-box kernel: [    9.829966] [drm:gen6_sanitize_pm] *ERROR* Power management discrepancy: GEN6_RP_INTERRUPT_LIMITS expected 1a000000, was 12000000
Jul 17 09:18:43 my-ubu-box kernel: [   38.954593] [drm] Changing LVDS panel from (-hsync, +vsync) to (-hsync, -vsync)



But I do not know if the timestamp is beginning or end or if your issue is Power management or LVDS panel.
Did you also change any video settings? What video driver?

Are you booting with UEFI or BIOS. Your hardware should be either?

This was more for the newer Haswell Intel chips, but discusses UEFI/BIOS settings.
 Ubuntu on the Precision M3800 or XPS15 Nov 2013
[http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx](http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx)
[URL="https://wiki.ubuntu.com/HardwareSupport/Machines/Laptops/Dell/XPS/15z"]
https://wiki.ubuntu.com/HardwareSupport/Machines/Laptops/Dell/XPS/15z[/URL]

---

### Post by hockeybum27 on 2014-07-21
oldfred,

re: interpreting the time in the log file, I concur - I will say that 
1) the log shows drm (not sure what that stands for?) switching a few times (though only 2x in the excerpt I sent you), and only the last one shows a gap between it and the previous entry; and 
2) based on the wording of the entries, the first entry you reference looks like a report *after* something was done (a resulting ERROR) - implying an 'end time', whereas the 2nd entry wording is as if it's ABOUT to do something ('Changing'...).  

On to answers (sort of) to your questions:

I'm not sure how to tell which video driver I'm using, if you can tell me a good way to check I'd love to know - I can tell you have the cursed Nvidia with Optimus (but I have that disabled in BIOS, if I recall - I've not played with that in years)...
I am using BIOS (not UEFI).
I've not changed any video settings in forever (I do alternate between using dual monitors, with my laptop being one of them, and an Asus being the other, but this has no effect).

Once I know how to check the video driver I will post that as well.

Thanks for your help on this!

---

### Post by oldfred on 2014-07-21
#To see video:
sudo lshw -c display
sudo lshw | grep -A 11 display
lspci | grep VGA
#Resolution:
xwininfo -root
#What is installed
dkms status

I do not know much about Optimus. Supposedly the newest nVidia supports that but not with switching. If you want to save power you turn off nVidia, if you can and just use Intel drivers. 

Some very new systems may need next version of Intel drivers to work well.
      
 Intel Corporation Haswell-ULT Integrated Graphics Controller (rev 09)  Dell 17R
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1300349](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1300349)


 HP 1000-1220LA worked with   i915.i915_enable_rc6=1
Broadwell (future) fix for use with 14.04's 3.13 kernel. Fixes really in 3.15 kernel
[http://www.phoronix.com/scan.php?page=news_item&px=MTY0ODY](http://www.phoronix.com/scan.php?page=news_item&px=MTY0ODY)
Haswell improvements thru 2013
[http://www.phoronix.com/scan.php?page=article&item=intel_2013haswell_end&num=1](http://www.phoronix.com/scan.php?page=article&item=intel_2013haswell_end&num=1)

---

### Post by hockeybum27 on 2014-07-21
I have not changed anything with display drivers (other than any updates that are automatic of course).  Since I have Optimus disabled (presumably - I will confirm at next reboot as this is a BIOS setting), I'm thinking Optimus would not come in to play here?

output from lshw - c display:
```

 *-display               
       description: VGA compatible controller
       product: GF119M [NVS 4200M]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
        resources: irq:16 memory:e4000000-e4ffffff memory:d0000000-dfffffff  memory:e0000000-e1ffffff ioport:4000(size=128) memory:e5000000-e507ffff
  *-display
       description: VGA compatible controller
       product: 2nd Generation Core Processor Family Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:46 memory:e5400000-e57fffff memory:c0000000-cfffffff ioport:5000(size=64)

```

Output from lspci | grep VGA:
```
00:02.0  VGA compatible controller: Intel Corporation 2nd Generation Core  Processor Family Integrated Graphics Controller (rev 09)
01:00.0 VGA compatible controller: NVIDIA Corporation GF119M [NVS 4200M] (rev a1)

```

Output from dkms:

```
nvidia-304, 304.116, 3.2.0-61-generic, x86_64: installed
nvidia-304, 304.116, 3.2.0-63-generic, x86_64: installed
nvidia-304, 304.116, 3.2.0-64-generic, x86_64: installed
nvidia-304, 304.116, 3.2.0-65-generic, x86_64: installed
nvidia-304, 304.116, 3.2.0-67-generic, x86_64: installed
nvidia-304-updates, 304.116, 3.2.0-61-generic, x86_64: installed
nvidia-304-updates, 304.116, 3.2.0-63-generic, x86_64: installed
nvidia-304-updates, 304.116, 3.2.0-64-generic, x86_64: installed
nvidia-304-updates, 304.116, 3.2.0-65-generic, x86_64: installed
nvidia-304-updates, 304.116, 3.2.0-67-generic, x86_64: installed
vboxhost, 4.3.14, 3.2.0-65-generic, x86_64: installed
vboxhost, 4.3.14, 3.2.0-67-generic, x86_64: installed

```

---

### Post by oldfred on 2014-07-21
It looks like you have nVidia installed but it is a legacy version?

I have an old 9600GT and run this which I installed from repository:
nvidia-331-updates, 331.38, 3.2.0-67-generic, x86_64: installed

       nVidia driver versions:
[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)
Legacy drivers by GPU model 
[http://www.nvidia.com/object/IO_32667.html](http://www.nvidia.com/object/IO_32667.html)

---

### Post by hockeybum27 on 2014-07-23
Oldfred,

Thanks for the info - are you suggesting that I try the same one?  if it hoses my display, is it easy to revert?

Also 0 I don't understand WHY this just started happening, however - something changed to make this start happening.

---

### Post by oldfred on 2014-07-23
If you want to install the newer nVidia, you must be careful to purge the old one or else you will have issues.

 Shows any file with nvidia in name, lots of files.
sudo find / -name "nvidia*"
Shows versions in repository:
sudo apt-cache search nvidia-sett*
Lists installed version, in/with your kernel:
dkms status
# Houseclean out all old versions to avoid issues
sudo apt-get remove --purge < nvidiadriverpackagename>
# [ using the correct names] for each driver, before running:
sudo apt-get purge nvidia*
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

     I do not have dual video. The newer nVidia will work with it, but I think it only uses the nVidia chip in high power mode. Not sure if then you may still want bumblebee or not, so you can switch to the Intel chip for low power use.

       Testing NVIDIA Optimus / DRI PRIME On Ubuntu 14.04
[http://www.phoronix.com/scan.php?page=article&item=nvidia_prime_ubuntu1404&num=1](http://www.phoronix.com/scan.php?page=article&item=nvidia_prime_ubuntu1404&num=1)
Bumblebee:
[https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)
[http://www.webupd8.org/2013/04/set-up-bumblebee-with-bumblebee.html](http://www.webupd8.org/2013/04/set-up-bumblebee-with-bumblebee.html)
[http://askubuntu.com/questions/348614/bumblebee-on-ubuntu-13-04-with-geforce-750m-and-driver-319](http://askubuntu.com/questions/348614/bumblebee-on-ubuntu-13-04-with-geforce-750m-and-driver-319)

---

### Post by hockeybum27 on 2014-07-23
Oldfred,

Thanks for the info - are you suggesting that I try the same one?  if it hoses my display, is it easy to revert?

Also 0 I don't understand WHY this just started happening, however - something changed to make this start happening.

---

### Post by oldfred on 2014-07-23
Yes, but I do not know what Optimus issues may be, so it really is up to you.

Generally you need the correct nVidia driver for your version of card/chip.
Sometimes kernel changes or other support software change to work "better" with video drivers.

Can you turn off nVidia chip in UEFI/BIOS? Then you know if you can boot without nVidia driver.
But on my older system, when I do not have nVidia I have to use nomodeset.
And I have seen a lot of users with just Intel and those need other boot parameters to boot.
       Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)

---

### Post by hockeybum27 on 2014-07-23
OF,
Thanks - I will look in to this - based on what I am getting from you, you are leaning towards the possibility or likeliness that a recent update messed up something with the video drivers?  I wonder if the other person who posted here is using Nvidia?  I will check.

---

### Post by hockeybum27 on 2014-07-23
Bluelight, are you using Nvidia?  Do you think this is related to video (see stream below)?

---

### Post by hockeybum27 on 2014-07-25
OF,

Update - starting yesterday (7/24) my boot time was back to normal (or more so).  The only thing that had changed were some automated updates the previous day; they were all CUPS updates, which makes no sense to me.
FYI here is what I'm seeing in my kernel log (I found it appears to have better info than dmesg - it includes dmesg + more):

```

Jul 25 10:00:14 my-ubu-box kernel: [    8.430085] input: HDA NVidia HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input17
Jul 25 10:00:14 my-ubu-box kernel: [    8.430215] input: HDA NVidia HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input18
Jul 25 10:00:14 my-ubu-box kernel: [    8.430326] input: HDA NVidia HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input19
Jul 25 10:00:15 my-ubu-box kernel: [    8.995105] userif-2: sent link down event.
Jul 25 10:00:15 my-ubu-box kernel: [    8.995107] userif-2: sent link up event.
Jul 25 10:00:15 my-ubu-box kernel: [    9.198511] [drm] Changing LVDS panel from (-hsync, -vsync) to (-hsync, +vsync)
Jul 25 10:00:16 my-ubu-box kernel: [   10.373940] [drm:gen6_sanitize_pm] *ERROR* Power management discrepancy: GEN6_RP_INTERRUPT_LIMITS expected 1a000000, was 12000000
Jul 25 10:00:23 my-ubu-box kernel: [   17.671105] vmnet8: no IPv6 routers present
Jul 25 10:00:23 my-ubu-box kernel: [   17.703094] vmnet1: no IPv6 routers present
Jul 25 10:00:24 my-ubu-box kernel: [   19.199371] [drm] Changing LVDS panel from (-hsync, +vsync) to (-hsync, -vsync)

```

I don't have any idea what has changed (I'd not yet gotten brave enough - or had enough downtime - to start working the Nvidia driver route yet).

I still see that gap after the power management error (~10 secs).  I'd love to get that resolved as well - any thoughts on where to go with that?

---

### Post by bluelightav on 2014-07-29
Hi, sorry for delay, I myself left for a vacation and haven't been keeping up with my posts on the net. The rest of our team is busy with other issues, so unfortunately I can't tell you yet whether the recent updates fixed the booting times. I'll ping them and see if something changed, but I'm not expecting a proper evaluation until Aug 18 when I return and have a look at the PCs in question myself - only then will I be able to tell if the issue is really gone.

> **hockeybum27 said:**
> Bluelight, are you using Nvidia?  Do you think this is related to video (see stream below)?

To answer your question: no, none of these PCs have nVIDIA cards and nVIDIA drivers. They are all Intel based - Sandy and Ivy Bridge Pentiums and Core i3s with integrated graphics only.

(By the way, I wouldn't be surprised if cups really was the culprit :))

---

