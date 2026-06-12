---
title: "Audio and video stutter unless input is received (Ubuntu 14.04/Gnome 3)"
date: 2015-04-11
forum: General Help
---

### Post by user_of_gnomes on 2015-04-11
Audio and video stutters unless I move the mouse. Sometimes it'll run fine for hours, sometimes it'll freeze the audio and/or image unless the computer receives input from mouse or keyboard. Watching a video in full-screen sceems to make it happen more often. Loading an album in VLC also makes it happen rather often. Streaming music is a lot more bearable (Banshee) but might make it happen as well. 

Flash player videos can cause it to freeze as well but once again, full screen mode makes it seem more frequent. 

I believe I've had this issue ever since I installed Ubuntu on my computer and I've never found a solution for it. Have to admit, haven't tried looking very hard. Partially because I don't really know what to do.

I've tried the following:[LIST=1]
[*]Installing Ubuntu Updates;
[*]Making sure the latest ati-catalyst driver is installed;
[*]changing the clock source;
[*]Not yelling at my computer.
[/LIST]

Nothing seems to work.

Some details that might be interesting:
[LIST]
[*]3.13.0-46-generic;
[*]Ubuntu 14.04.2 LTS 64-bit;
[*]AMD Phenom(tm) II X4 925 Processor × 4 ;
[*]ATI Radeon 6870;
[*]Gnome 3;
[*] HDA-Intel - HDA ATI SB / Xonar DGC-Media Oxygen HD Audio (Asus Sonar soundcard);
[*]No S.M.A.R.T trips
[/LIST]

Any idea where to go from here?

---

### Post by QDR06VV9 on 2015-04-11
> **user_of_gnomes said:**
> Audio and video stutters unless I move the mouse. Sometimes it'll run fine for hours, sometimes it'll freeze the audio and/or image unless the computer receives input from mouse or keyboard. Watching a video in full-screen sceems to make it happen more often. Loading an album in VLC also makes it happen rather often. Streaming music is a lot more bearable (Banshee) but might make it happen as well. 

Flash player videos can cause it to freeze as well but once again, full screen mode makes it seem more frequent. 

I believe I've had this issue ever since I installed Ubuntu on my computer and I've never found a solution for it. Have to admit, haven't tried looking very hard. Partially because I don't really know what to do.

I've tried the following:
[LIST=1]
[*]Installing Ubuntu Updates; 
[*]Making sure the latest ati-catalyst driver is installed; 
[*]changing the clock source; 
[*]Not yelling at my computer. 
[/LIST]

Nothing seems to work.

Some details that might be interesting:
[LIST]
[*]3.13.0-46-generic; 
[*]Ubuntu 14.04.2 LTS 64-bit; 
[*]AMD Phenom(tm) II X4 925 Processor × 4 ; 
[*]ATI Radeon 6870; 
[*]Gnome 3; 
[*] HDA-Intel - HDA ATI SB / Xonar DGC-Media Oxygen HD Audio (Asus Sonar soundcard); 
[*]No S.M.A.R.T trips 
[/LIST]

Any idea where to go from here?
Your Rig is very close to my Specs also.
Mine was due to video drivers.
Would you do this so we can get some more info 
run in terminal
```
sudo apt-get install inxi
```
and then run in terminal
```
inxi -b
``` 

And post the output here.
I think you **should** yell at your computer..(Joke here)
Also this link below is finally what I ended up doing..
[http://askubuntu.com/questions/68306/how-do-i-remove-the-proprietary-ati-drivers](http://askubuntu.com/questions/68306/how-do-i-remove-the-proprietary-ati-drivers)
Regards

---

### Post by user_of_gnomes on 2015-04-11
> **runrickus said:**
> Your Rig is very close to my Specs also.
Mine was due to video drivers.
Would you do this so we can get some more info 
run in terminal
```
sudo apt-get install inxi
```
and then run in terminal
```
inxi -b
``` 

And post the output here.
I think you **should** yell at your computer..(Joke here)
Also this link below is finally what I ended up doing..
[http://askubuntu.com/questions/68306/how-do-i-remove-the-proprietary-ati-drivers](http://askubuntu.com/questions/68306/how-do-i-remove-the-proprietary-ati-drivers)
Regards

Thanks for suggesting Inxi, I was looking for something like that! Here's the output:

```
System:    Host: Zeus Kernel: 3.13.0-46-generic x86_64 (64 bit) Desktop: Gnome 3.10.4 Distro: Ubuntu 14.04 trusty
Machine:   Mobo: Gigabyte model: GA-790XTA-UD4 version: x.x Bios: Award version: F3 date: 05/13/2010
CPU:       Quad core AMD Phenom II X4 925 (-MCP-) clocked at 800.00 MHz 
Graphics:  Card: Advanced Micro Devices [AMD/ATI] Barts XT [Radeon HD 6870] 
           X.Org: 1.15.1 drivers: ati,radeon (unloaded: fbdev,vesa) Resolution: 1920x1080@60.0hz 
           GLX Renderer: Gallium 0.4 on AMD BARTS GLX Version: 3.0 Mesa 10.1.3
Network:   Card: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller driver: r8169 
Drives:    HDD Total Size: 1394.6GB (19.6% used)
Info:      Processes: 210 Uptime: 19 min Memory: 1357.4/7982.7MB Client: Shell (bash) inxi: 1.9.17 
```

I am hoping I can do without removing the propietary drivers because they are much more efficient at throttling the GPU and I get better performance out of 'm! Got tired of manually switching energy saving profiles. 
If there are no other suggestions I'll remove 'm and see if the skipping comes back.

I forgot to mention that at some point [I removed PulseAudio]("http://www.hecticgeek.com/2012/01/how-to-remove-pulseaudio-use-alsa-ubuntu-linux/") and installed ALSA instead. That worked quite well for an entire day until I turned the computer off and on and I had no more sound at all. 
I didn't get to test it any further than just one day but I witnessed no skipping then.

---

### Post by QDR06VV9 on 2015-04-12
> **user_of_gnomes said:**
> Thanks for suggesting Inxi, I was looking for something like that! Here's the output:

```
System:    Host: Zeus Kernel: 3.13.0-46-generic x86_64 (64 bit) Desktop: Gnome 3.10.4 Distro: Ubuntu 14.04 trusty
Machine:   Mobo: Gigabyte model: GA-790XTA-UD4 version: x.x Bios: Award version: F3 date: 05/13/2010
[CODE]CPU:       Quad core AMD Phenom II X4 925 (-MCP-) clocked at 800.00 MHz 
```
Graphics:  Card: Advanced Micro Devices [AMD/ATI] Barts XT [Radeon HD 6870] 
           X.Org: 1.15.1 drivers: ati,radeon (unloaded: fbdev,vesa) Resolution: 1920x1080@60.0hz 
           GLX Renderer: Gallium 0.4 on AMD BARTS GLX Version: 3.0 Mesa 10.1.3
Network:   Card: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller driver: r8169 
Drives:    HDD Total Size: 1394.6GB (19.6% used)
Info:      Processes: 210 Uptime: 19 min Memory: 1357.4/7982.7MB Client: Shell (bash) inxi: 1.9.17 [/CODE]

I am hoping I can do without removing the propietary drivers because they are much more efficient at throttling the GPU and I get better performance out of 'm! Got tired of manually switching energy saving profiles. 
If there are no other suggestions I'll remove 'm and see if the skipping comes back.

I forgot to mention that at some point [I removed PulseAudio]("http://www.hecticgeek.com/2012/01/how-to-remove-pulseaudio-use-alsa-ubuntu-linux/") and installed ALSA instead. That worked quite well for an entire day until I turned the computer off and on and I had no more sound at all. 
I didn't get to test it any further than just one day but I witnessed no skipping then.

```
CPU:       Quad core AMD Phenom II X4 925 (-MCP-) clocked at 800.00 MHz
```
That is what I suspected!
With the drivers(proprietary) I also had glitches while over clocking try stepping down your cpu and gpu to see if there is any improvement.
I am not trying to be negative here but I got so frustrated that I ended up disabling my ATI card (via Bios)
and installed a middle of the road Nvidia card Things are much better not perfect but better.;)
My Specs now look like this.
```
inxi -b
System:    Host: me-Aspire-M3300 Kernel: 3.19.0-13-lowlatency x86_64 (64 bit)
           Desktop: N/A Distro: Ubuntu 15.04 vivid
Machine:   System: Acer product: Aspire M3300
           Mobo: Acer model: FRS780M
           Bios: American Megatrends v: P03-B0 date: 11/16/2009
CPU:       Quad core AMD Phenom II X4 810 (-MCP-) speed/max: 800/2600 MHz
Graphics:  Card: NVIDIA GF119 [GeForce GT 520]
           Display Server: X.Org 1.17.1 drivers: nvidia (unloaded: fbdev,vesa,nouveau)
           Resolution: 1920x1080@60.0hz
           GLX Renderer: GeForce GT 520/PCIe/SSE2
           GLX Version: 4.5.0 NVIDIA 349.12
Network:   Card: Marvell 88E8071 PCI-E Gigabit Ethernet Controller
           driver: sky2
Drives:    HDD Total Size: 2500.5GB (2.1% used)
Info:      Processes: 222 Uptime: 51 min Memory: 939.7/5967.4MB
           Client: Shell (bash) inxi: 2.2.16 

```
So sorry I did not have better news for you!:(
Maybe someone else will have a better solution.
But stepping down my cpu helped alot and I really did not notice any performance lags to be honest.
One more thought what mixer are you using not not that it matters but see if the tone box is checked, if it is uncheck it(disable)
that also cleaned up a lot of noise for me.
Regards
Just saw this.(Early for me need more coffe)
```
I forgot to mention that at some point [I removed PulseAudio]("http://www.hecticgeek.com/2012/01/how-to-remove-pulseaudio-use-alsa-ubuntu-linux/")  and installed ALSA instead. That worked quite well for an entire day  until I turned the computer off and on and I had no more sound at all. 
I didn't get to test it any further than just one day but I witnessed no skipping then.
```
When you boot-up and have no sound open terminal and
```
sudo alsamixer
``` 
make sure your card is  the default.

---

### Post by user_of_gnomes on 2015-04-12
I uninstalled PulseAudio once again and rebooted. Seems to work now. I'll see if the stuttering persists and if not, move on to your next suggestions.

> With the drivers(proprietary) I also had glitches while over clocking try stepping down your cpu and gpu to see if there is any improvement.

I run everything at stock-speeds, though.

>  and installed a middle of the road Nvidia card Things are much better not perfect but better.
How are the Nvidia drivers? Are you using the propietary or open source ones? I am particularly concerned about the power-saving features not working all that well.ATI seems to have it covered.

> One more thought what mixer are you using not not that it matters but see if the tone box is checked, if it is uncheck it(disable)

Where would I find that in gnome-alsamixer? Or alsamixer.

---

### Post by QDR06VV9 on 2015-04-13
> **user_of_gnomes said:**
> I uninstalled PulseAudio once again and rebooted. Seems to work now. I'll see if the stuttering persists and if not, move on to your next suggestions.



I run everything at stock-speeds, though.


How are the Nvidia drivers? Are you using the propietary or open source ones? I am particularly concerned about the power-saving features not working all that well.ATI seems to have it covered.



Where would I find that in gnome-alsamixer? Or alsamixer.
Stock Speed is good.
 Yes running Yes I am using Nvidia driver
```
Graphics:  Card: NVIDIA GF119 [GeForce GT 520]
           Display Server: X.Org 1.17.1 drivers: nvidia (unloaded: fbdev,vesa,nouveau)
           Resolution: 1920x1080@60.0hz
           GLX Renderer: GeForce GT 520/PCIe/SSE2
           GLX Version: 4.5.0[COLOR=#ff0000] NVIDIA 349.12[/COLOR]
```
Alsamixer you can invoke in terminal
```
sudo alsamixer
```
See thumb
As you can see from that shot mine defaults to ATI but by using <F6> at the top of your keyboard you will get option to change to the right card.
also shown in second thumb.
Test how that works for you.
Best of luck;)

---

### Post by user_of_gnomes on 2015-04-13
I uninstalled PulseAudio and installed Gnome-Alsa again. After one reboot, the sound gave up the ghost once more (despite having the soundcard set properly in alsamixer) but I then followed [step 6 of this troubleshooting page]("https://help.ubuntu.com/community/SoundTroubleshooting") and it seems to work quite well now, even after a few reboots.

I haven't had any stuttering yet either but I'm no doubt jinxing it by saying s!

---

### Post by user_of_gnomes on 2015-04-14
So far so good. I'm marking this as solved for now, thanks for the help Runrickus.

---

### Post by QDR06VV9 on 2015-04-15
Not sure what I did to help?
Did not even think to have you check your bios..
Good Job Bud, Glad you got it sorted out;)
Regards

---

