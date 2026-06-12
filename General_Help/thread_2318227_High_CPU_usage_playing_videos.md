---
title: "High CPU usage playing videos"
date: 2016-03-24
forum: General Help
---

### Post by fall2 on 2016-03-24
"KERNAL ERRORS"


While in firefox I streamed a html5 video, let the video load completely and I looked at top in a terminal.
firefox hit up to 75% cpu
Xorg hit up to 41% cpu
pulseaudio hit 3%

Those are the high spikes, the low spikes would be half those numbers 35, 20 and 1 durring the video.


Videos look like they are in slow motion and skip every few seconds in all browsers. I tried ff, chrome and opera. It plays slow+skips in all flash and html5. Audio doesn't skip.
In youtube html5 i had a video in 480p, it was playing slow and skipping so i turned it to 144p and it got much worse.

Video does seem to play good if I reset my laptop and go directly to a video in any web browser but it will get really bad after playing a video or restarting the browser.

To put it into perspective in youtube i used to drop about 100 frames per minute in 480p and now i drop about 1500 frames per minute.

I did test it on puppy linux and it was much better, there was no slow motion video and a lot less frames dropped but videos still skipped a little every few seconds.


Both flash and htlm5 are so broken. I almost think there is a driver error? 
unlike puppy a usb boot of xubuntu didn't play any where near as well.

---

### Post by sudodus on 2016-03-24
You can try Lubuntu. It has the lightest desktop environment, LXDE, of the Ubuntu flavours, lighter than Xubuntu's XFCE.

But if you have problems with Puppy, maybe your hardware is not powerful enough. A good graphics card can do a lot of the work and and CPU will be almost idle also with 1920x1080-50p video (unless the CPU and motherboard are just too old). But many good graphics cards need proprietary drivers to release the full capability.

In order to give good and relevant advice, we must know your computer, so please specify at least

- Brand name and model
- CPU
- RAM (size)
- graphics chip/card, name and model (this is very important)

---

### Post by fall2 on 2016-03-24
Gateway 400vtx
2400 pentium 4
2GB 
Intel Corporation 82852/855GM Integrated Graphics Device (rev 01)


I'm digging through my kernal.log and found these errors, I don't know if they are any use but here they are.

Mar 24 05:37:15 fall-Gateway-400VTX kernel: [   23.059448] [drm:intel_set_cpu_fifo_underrun_reporting [i915]] *ERROR* pipe A underrun
Mar 24 05:37:15 fall-Gateway-400VTX kernel: [   23.069273] [drm:intel_set_cpu_fifo_underrun_reporting [i915]] *ERROR* pipe B underrun
Mar 24 05:37:15 fall-Gateway-400VTX kernel: [   23.069325] [drm:intel_cpu_fifo_underrun_irq_handler [i915]] *ERROR* CPU pipe B FIFO underrun
Mar 24 05:37:15 fall-Gateway-400VTX kernel: [   23.083283] [drm] initialized overlay support



Lubuntu 14.04 was my first linux distro. It is definitely a little less cpu intensive than xubuntu. I just found xubuntu to be a little more mature or complete OS and user friendly as to options it has.

---

### Post by Nuno_Abreu on 2016-03-24
It shouldn't be that slow, as I have a Pentium IV machine and it barely even reaches 30% of CPU usage when watching a 480p video - and we're talking about a computer with 1GB of DDR2 RAM.

Does this only happen with web browsers? What about VLC? You can also try to use xorg-edgers to see if that solves the problem - here's the PPA:
[http://bit.ly/1TgcvVp](http://bit.ly/1TgcvVp)

---

### Post by fall2 on 2016-03-24
> **Nuno_Abreu said:**
> It shouldn't be that slow, as I have a Pentium IV machine and it barely even reaches 30% of CPU usage when watching a 480p video - and we're talking about a computer with 1GB of DDR2 RAM.

Does this only happen with web browsers? What about VLC? You can also try to use xorg-edgers to see if that solves the problem - here's the PPA:
[http://bit.ly/1TgcvVp](http://bit.ly/1TgcvVp)

That did seem to help, I only tested in one browser "ff" a few times but I did have a dramatic reduction in frame loss using html5.
Using flash the frame loss was about the same.
In both flash and html5, the choppyness, slow motion video and freezes "seem" to be mostly reduced so far.
I'll test later on Opera.

Overall thank you Nuno_Abreu.
It still doesn't look to me like its as good as it should be. Well, it was a train wreck and now its more like bumper cars.

---

### Post by sudodus on 2016-03-24
I enjoy mixing Xubuntu and Lubuntu. My current system was installed as Xubuntu with the meta-packaged lubuntu-desktop added afterwards. It gives me a system that is better for me than either of the pure systems. Most of the time I'm using the Lubuntu desktop. My hardware is getting old and I want the fast response and the good video playing of the LXDE desktop environment that comes with Lubuntu. And I have many good tools and system configurations of Xubuntu.

Maybe you can do the something similar - log into Lubuntu and its lighter and faster desktop environment to play video - log into Xubuntu for other tasks and enjoy the more polished desktop environment.

1. If you want it lighter, you can install only lubuntu-core, not the whole lubuntu-desktop

2. If you want it even lighter, you can install only LXDE, not the whole lubuntu-core

3. If you want it even lighter, you can install only openbox, not the whole LXDE. Openbox in only a window-manager not a full desktop environment, but you can use it as a light-weight environment to play video (with less issues due to lacking horsepower).

4. There are also other ultra-light window-managers, for example fluxbox and jwm, that you can try.

---

### Post by fall2 on 2016-03-25
Yeah I have internal 14.04 error messages popping up. for some reason when I try to open light locker settings, it just closes right away. On top of that videos in Opera are twice as choppy than videos in FF, it shouldn't be that way.

My software is broken.

---

### Post by sudodus on 2016-03-25
Sometimes it is easier to make a fresh installation than to try to fix a system after a lot of tweaking.

It can be possible but difficult to get good performance with old hardware. Maybe you can start with a very light system and carefully add packages.

- One alternative is to start with the Ubuntu ***mini.iso***.

- Another alternative is according to this link: [OBI/Trusty-mini-txt](https://help.ubuntu.com/community/OBI/Trusty-mini-txt)

---

### Post by fall2 on 2016-03-25
I am thinking I should reinstall bios and then try xubuntu again.

When I boot xubuntu from a usb 7 or 8 errors pop up. PIPE and CPU errors. I think some of the code for my drivers got messed up in bios and thats why all the linux os I tried are not working like they used to.

---

### Post by sudodus on 2016-03-25
It is worth trying :-)

I think it is also a good idea to try a light desktop environment or window manager.

---

### Post by fall2 on 2016-03-27
Hey I just thought I would report back and tell you I flashed/fixed my bios but that was not the problem.

I did find a article that said "Rolling back to the originally installed kernel fixed this issue."
"[drm:intel_cpu_fifo_underrun_irq_handler [i915]] *ERROR* CPU pipe A FIFO underrun"

I don't have "PIPE A FIFO" error, its "PIPE B FIFO" but I think the errors must be similar.


So, I don't think I can roll back? or can I? or can I fix the kernel?

---

### Post by matthew82 on 2016-03-28
Hey Fall2! I have tried some flavors of Ubuntu 14.04 LTS on my HP mini 311 with dedicated nVidia graphics. The ones I experimented with are lubuntu, xubuntu, Ubuntu, and then Kali Linux. I mainly use Ubuntu with GNOME desktop environment since it uses less graphics and also made sure that the graphics drivers were chosen and up to date rather than the default graphic driver which places the load on CPU than using the GPU to my understanding.  Sometimes, I do hop on Kali and update the software and drivers. It's the flavor I use when out and about since that mostly pure Debian. Just some food for thought.

---

### Post by fall2 on 2016-03-28
Errors come up when trying to boot Ubuntu 14.04 from a USB and it fails to load.

---

### Post by mikewhatever on 2016-03-28
> **fall2 said:**
> Gateway 400vtx
2400 pentium 4
2GB 
Intel Corporation 82852/855GM Integrated Graphics Device (rev 01)

This hardware is about 13 yeas old. It was, and still is, a good desktop PC for editing documents, checking emails, light browsing, but not for videos. I honestly don't think anything other then a decent dedicated graphics card is going to help, and even then, do not expect too much, it's not going to get any newer.

---

### Post by fall2 on 2016-03-29
Hmm, looks like I made a bad choice for a title of this forum. The title should of been "Kernel Errors"

---

### Post by sudodus on 2016-03-29
Please try a lighter flavour of Ubuntu! I suggest Lubuntu.

An alternative is something like I suggested in post #6. If there are still problems to play video, and you really want to do that, try more with Puppy linux (there are several flavours of Puppy) or Tiny Core.

Otherwise, I think mikewhatever is right in post #14.

---

### Post by fall2 on 2016-03-29
I had this pc for 2 years and never had these kernal errors come up. The errors started march 24th.

I tried Ubuntu, Lubuntu, Puppy, Xubuntu, Damn small linux. Its no better in any.
I also noticed I am getting Operating System freezes as well were I can't click on anything for two or three seconds.

The Linux bug keeps comming up and it tells me to report it so it can be fixed.



some of my var/log/kern.log.1


kernel: [   14.393665] [drm] Memory usable by graphics device = 128M
kernel: [   14.393676] checking generic (e8000000 1e0000) vs hw (e8000000 8000000)
kernel: [   14.393681] fb: switching to inteldrmfb from VESA VGA
kernel: [   14.393746] Console: switching to colour dummy device 80x25
kernel: [   14.394105] [drm] Replacing VGA console driver
kernel: [   14.411865] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
kernel: [   14.411874] [drm] Driver supports precise vblank timestamp query.
kernel: [   14.412007] [drm:intel_parse_bios [i915]] *ERROR* Child device config size 27 is too small.
kernel: [   14.412217] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem[IMG]https://lqo-thequestionsnetw.netdna-ssl.com/questions/images/smilies/redface.gif[/IMG]wns=io+mem
kernel: [   14.472087] [drm] GMBUS [i915 gmbus panel] timed out, falling back to bit banging on pin 3
kernel: [   14.614325] [drm:intel_set_cpu_fifo_underrun_reporting [i915]] *ERROR* pipe A underrun
kernel: [   14.627250] [drm:intel_set_cpu_fifo_underrun_reporting [i915]] *ERROR* pipe B underrun
kernel: [   14.627304] [drm:intel_cpu_fifo_underrun_irq_handler [i915]] *ERROR* CPU pipe B FIFO underrun
kernel: [   14.656777] [drm] initialized overlay support
kernel: [   14.659290] [drm] Initialized i915 1.6.0 20150522 for 0000:00:02.0 on minor 0
kernel: [   14.751833] fbcon: inteldrmfb (fb0) is primary device
kernel: [   14.752084] Console: switching to colour frame buffer device 128x48
kernel: [   14.752122] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
kernel: [   14.752126] i915 0000:00:02.0: registered panic notifier



and some more...



[   22.812443] [drm] GMBUS [i915 gmbus panel] timed out, falling back to bit banging on pin 3
[   22.846745] [drm:intel_set_cpu_fifo_underrun_reporting [i915]] *ERROR* pipe A underrun
[   22.847046] [drm:intel_cpu_fifo_underrun_irq_handler [i915]] *ERROR* CPU pipe B FIFO underrun
[   22.855890] [drm] initialized overlay support
[   22.855989] [drm] Initialized i915 1.6.0 20150522 for 0000:00:02.0 on minor 0



Some more...




usbcore: registered new interface driver snd-usb-audio
[  361.000150] [drm] stuck on render ring
[  361.003143] [drm] GPU HANG: ecode 2:0:0x7c63ffca, in Xorg [1187], reason: Ring hung, action: reset
[  361.003151] [drm] GPU hangs can indicate a bug anywhere in the entire gfx stack, including userspace.
[  361.003155] [drm] Please file a _new_ bug report on bugs.freedesktop.org against DRI -> DRM/Intel
[  361.003159] [drm] drm/i915 developers can then reassign to the right component if it's not a kernel issue.
[  361.003163] [drm] The gpu crash dump is required to analyze gpu hangs, so please always attach it.
[  361.003168] [drm] GPU crash dump saved to /sys/class/drm/card0/error
[  361.008378] drm/i915: Resetting chip after gpu hang
[  361.008448] [drm:i915_reset [i915]] *ERROR* Failed to reset chip: -19



 [drm:i9xx_check_fifo_underruns [i915]] *ERROR* pipe B underrun
[ 6238.095366] [drm:intel_cpu_fifo_underrun_irq_handler [i915]] *ERROR* CPU pipe B FIFO underrun
[ 6238.178488] [drm:intel_cpu_fifo_underrun_irq_handler [i915]] *ERROR* CPU pipe A FIFO underrun
[ 6478.955755] [drm:intel_cpu_fifo_underrun_irq_handler [i915]] *ERROR* CPU pipe A FIFO underrun
[ 6479.106324] [drm:intel_cpu_fifo_underrun_irq_handler [i915]] *ERROR* CPU pipe B FIFO underrun
[10826.977994] [drm:intel_cpu_fifo_underrun_irq_handler [i915]] *ERROR* CPU pipe B FIFO underrun
[10829.110759] [drm:intel_cpu_fifo_underrun_irq_handler [i915]] *ERROR* CPU pipe A FIFO underrun
[11516.335599] [drm:intel_cpu_fifo_underrun_irq_handler [i915]] *ERROR* CPU pipe A FIFO underrun
[11516.402117] [drm:intel_cpu_fifo_underrun_irq_handler [i915]] *ERROR* CPU pipe B FIFO underrun
[11516.501867] [drm:intel_cpu_fifo_underrun_irq_handler [i915]] *ERROR* CPU pipe B FIFO underrun
[11516.565194] [drm:intel_cpu_fifo_underrun_irq_handler [i915]] *ERROR* CPU pipe A FIFO underrun
[11516.801150] [drm:intel_cpu_fifo_underrun_irq_handler [i915]] *ERROR* CPU pipe B FIFO underrun
[11518.994834] [drm:intel_cpu_fifo_underrun_irq_handler [i915]] *ERROR* CPU pipe A FIFO underrun
[11526.743669] [drm:intel_cpu_fifo_underrun_irq_handler [i915]] *ERROR* CPU pipe B FIFO underrun
[11526.943174] [drm:intel_cpu_fifo_underrun_irq_handler [i915]] *ERROR* CPU pipe B FIFO underrun
[11529.385355] [drm:intel_cpu_fifo_underrun_irq_handler [i915]] *ERROR* CPU pipe A FIFO underrun
[11537.401099] [drm:intel_cpu_fifo_underrun_irq_handler [i915]] *ERROR* CPU pipe B FIFO underrun
[11537.433434] [drm:intel_cpu_fifo_underrun_irq_handler [i915]] *ERROR* CPU pipe A FIFO underrun
[14042.976962] [drm:intel_cpu_fifo_underrun_irq_handler [i915]] *ERROR* CPU pipe B FIFO underrun
[14044.995527] [drm:intel_cpu_fifo_underrun_irq_handler [i915]] *ERROR* CPU pipe A FIFO underrun
[14114.372307] [drm:intel_cpu_fifo_underrun_irq_handler [i915]] *ERROR* CPU pipe A FIFO underrun
[14114.423848] [drm:intel_cpu_fifo_underrun_irq_handler [i915]] *ERROR* CPU pipe B FIFO underrun
[15027.000095] [drm] stuck on render ring
[15027.003109] [drm] GPU HANG: ecode 2:0:0x4167ffc1, in Xorg [1188], reason: Ring hung, action: reset
[15027.003116] [drm] GPU hangs can indicate a bug anywhere in the entire gfx stack, including userspace.
[15027.003121] [drm] Please file a _new_ bug report on bugs.freedesktop.org against DRI -> DRM/Intel
[15027.003125] [drm] drm/i915 developers can then reassign to the right component if it's not a kernel issue.
[15027.003129] [drm] The gpu crash dump is required to analyze gpu hangs, so please always attach it.
[15027.003134] [drm] GPU crash dump saved to /sys/class/drm/card0/error
[15027.008394] drm/i915: Resetting chip after gpu hang
[15027.008462] [drm:i915_reset [i915]] *ERROR* Failed to reset chip: -19

---

### Post by fall2 on 2016-03-29
Well I think a answered my own problem. I need to report it to bugs.freedesktop.org.

---

### Post by sudodus on 2016-03-29
I know almost nothing about kernel errors. But the fact that you get them with several and very different kernels makes me think that you have some failing hardware rather than bugs in the kernels. Since the graphics is mentioned several times in your output, I can suspect problems with the graphics chip or some hardware around it.

Sometimes a failing power supply unit can trigger failures too - for example when the circuits are getting too low voltage.

---

### Post by fall2 on 2016-03-29
Nah, the problem started when I tried to install arch linux. That installation failed, I think I had the wrong .iso image maybe. When I restarted xubuntu I was missing a lot of desktop features so I had to reinstall xubuntu. Thats when the errors started. Maybe it broke some hardware during that, I think its software. I seen a post of another person with a similar issue and he managed to fix it by rolling back his kernels. 

I don't really know, it could be either one hardware or software. The only way to find out is to check the software.

---

### Post by sudodus on 2016-03-29
If you boot Puppy from a CD or USB drive, it works without using the content in the internal drive. It will not care if there is a good or bad installed system, or no system at all in the internal drive.

---

### Post by fall2 on 2016-03-29
Is there a version of puppy that uses a full FireFox browser, with all the add-ons. That could be helpful.

---

### Post by sudodus on 2016-03-29
I don't know the details about Puppy, I only test it occasionally. There is a [Puppy Linux Forum](http://murga-linux.com/puppy/), where you should get good replies to that question and also other questions about Puppy.

---

