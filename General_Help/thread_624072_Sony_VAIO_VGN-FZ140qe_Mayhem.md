---
title: "Sony VAIO VGN-FZ140qe Mayhem"
date: 2007-11-26
forum: General Help
---

### Post by Neonjack on 2007-11-26
Hi!  

First of all, I'd like to say Ubuntu saved my life!  Why?  Because this summer, I bought this machine: 

Computer Type: Notebook
Type of Use: Portable
Action Buttons: S1, (programmable), Volume, AV Mode, Play/Pause and Stop
Pointing Device: Electro-Static touch pad
Keyboard: QWERTY, 82 keys with 2mm stroke and 19.05mm pitch
Camera: Built-in camera and microphone

**Processor**
Type: Intel® Core™2 Duo Processor T7100
Speed: 1.80GHz1
Front Side Bus Speed: 800MHz
L2 Cache: 2MB Advanced Smart Cache
Technology: Intel® Centrino® Duo processor Technology

**Memory**
Type: DDR2
Installed: 2GB (1GBx2) PC2-5300
Maximum: 4GB
Speed: 667MHz

**Hard Drive**
Capacity: 200GB2
Speed: 4200rpm
Interface: Serial ATA

**Expansion Slots**
Multimedia Card Reader: One Memory Stick Duo™ media with MagicGate® functionality, One ExpressCard™ /34 Slot, One Secure Digital Media (SD) slot

**Audio**
Sound System: Sony® Sound Reality™ - Audio Enhancer

**Display**
Screen or Display Technology: WXGA LCD
Screen Size: 15.4”11
Resolution: 1280 x 800
XBRITE™ Technology: Yes

**Graphics**
Processor: Mobile Intel® Graphics Media Accelerator X3100
Video RAM: 358MB Total Available Graphics Memory13
Chipset: Intel® 965GM
Interface: VGA and S-Video Out with Smart Display Sensor

**Inputs and Outputs**
Ethernet Port: 1
Headphone Jack: 1
Memory Stick® Media Slot: 1
Modem Jack: 1
Secure Digital Slot: 1
Microphone Input: 1
S-Video Output: 1
USB Ports: 3 (2.0 compliant)
VGA Output: 1
DC-In: 1
Express Card™ Slot: /34 x 1
i.LINK® Connection: 1(4-pin) interface6

**Networking/Modem**
Ethernet Protocol: Fast Ethernet (RJ-45)
Ethernet Speed: 10Base-T/100Base-TX
Modem Type: Integrated V.92/V.90 Modem (RJ-11)
Wireless LAN: Intel® PRO/Wireless 4965AGN Network Connection (802.11a/b/g/n)3

**Powe**r
Battery Type: Standard Lithium-ion Battery (VGPBPS8)
Estimated Battery Life: 2.0-4.0 hours7
Power Requirements: 86W+10%

**Software**
Operating System: Windows Vista™ Home French Premium

**Dimensions**
Weight: 5.75 lbs with standard battery (weight is approximate and may vary)
Measurements: 14” (W) x 0.98” -1.4” (H) x 10.02” (D)

The seller didn't have a clue as to why there was no recovery disk with this laptop and did not find any reasons why I couldn't install XP when I got home. 

Well!  I had 2 big surprises, when I did got home: there was a hidden partition on my laptop (7GO) with Vista on it AND I could never install XP on it because SONY would not provide any drivers for it.  I was in trouble!  It took me a while to realise all that, but as a web designer, I need to check my sites on different platforms (IE6, IE7, FF, Opera and so on), but it was impossible now, because my super laptop was Vista only, IE7 only.

Everything went to hell when my OS crashed on me and I had to reformat everything.

This is where Ubuntu comes in!  It's light, beautiful and efficient, much more than I could've imagine.

Now, the only troubles are...

- My headphones jack doesn't work, only my laptop speakers do and in my sound options, I only have MASTER and PCM available;
- My video card is not recognized even though I updated it through the Linux Graphics Drivers from Intel page ([http://intellinuxgraphics.org/download.html]("http://intellinuxgraphics.org/download.html"))
- My S VIDEO OUT doesn't work at all...  when I plug it on my TV, nothing happens and it's certainly related to my video card not being recognized;
- My LCD Display is not recognized.

HELLP!

I do not want to go back to Vista, I love Ubuntu.

Can anyone help me out?  

Thanks a lot in advance!!!

Mehdi

---

### Post by inportb on 2007-11-26
Hey, your audio problem looks like a driver issue. It looks like you have more channels than your current driver can manage. I had a similar issue and fixed it by building myself the latest version of ALSA.

try this:

sudo apt-get install build-essential ncurses-dev gettext && wget ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.15.tar.bz2 && tar xf alsa-driver-1.0.15.tar.bz2 && cd alsa-driver-1.0.15 && ./configure --with-cards=hda-intel && make && sudo install -v -m644 pci/hda/snd-hda-intel.ko  /lib/modules/$(uname -r)/ubuntu/media/snd-hda-intel/ && cd ../ && sudo rm -rf alsa-driver-1.0.15 && sudo depmod -ae && sudo modprobe snd-hda-intel ; modprobe snd-pcm-oss ; modprobe snd-mixer-oss ; modprobe snd-seq-oss

(that's one long-*** line. it installs the build environment, downloads the ALSA source, build the drivers, and installs the driver)

---

### Post by Neonjack on 2007-11-26
Hum, I tried and here's what I got at some point during dl/config: 

Setting up build-essential (11.3ubuntu1) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
--18:51:53--  [ftp://ftp.alsa-project.org/pub/drive...1.0.15.tar.bz2](ftp://ftp.alsa-project.org/pub/drive...1.0.15.tar.bz2)
           => `drive...1.0.15.tar.bz2'
Resolving ftp.alsa-project.org... 160.217.9.25
Connecting to ftp.alsa-project.org|160.217.9.25|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub ... done.
==> PASV ... done.    ==> RETR drive...1.0.15.tar.bz2 ... 
No such file `drive...1.0.15.tar.bz2'.

Any ideas?

---

### Post by Neonjack on 2007-12-02
Please people...  I'm desperate...

---

### Post by marco_polo99 on 2007-12-02
I've got a VGN-fz240e and I solved the headphone issues by doing the following, however I still don't have a working mic in.


Solved the headphone issue by reinstalling alsa according to instructions provided by LordRaiden [http://ubuntuforums.org/showthread.p...ht=sound+mixer](http://ubuntuforums.org/showthread.p...ht=sound+mixer) then downloading alsa mixer gui "sudo apt-get install alsamixergui" and adding line "options snd-hda-intel model=vaio position_fix=0" into /etc/modprobe.d/alsa-base


You may also want to check out this thread which is an ongoing regarding vaio issues with the VGN series 
[http://ubuntuforums.org/showthread.php?t=486861&highlight=vgn-fz+headphone](http://ubuntuforums.org/showthread.php?t=486861&highlight=vgn-fz+headphone)
__________________

---

### Post by Neonjack on 2007-12-02
Thanks  **marco_polo99** but I'm still stucked.

I've followed **LordRaiden**'s instruction, but I still only have **Master** and **PCM** in my sound options.

Here's a couple of screenshots, any ideas?: 

[IMG]http://www.mehdi.ca/temp/mixer.png[/IMG]

[IMG]http://www.mehdi.ca/temp/terminal.png[/IMG]

[IMG]http://www.mehdi.ca/temp/volume.png[/IMG]

---

### Post by marco_polo99 on 2007-12-02
Were you able to edit alsa-base?  From your screenshot it looks like you were trying to do so, but typed in the wrong command.  You need to type "sudo gedit /etc/modprobe.d/alsa-base"  to open the gedit  text editor so that you can add the line "options snd-hda-intel model=vaio position_fix=0" at the bottom, save, and reboot.

---

### Post by Neonjack on 2007-12-02
Hah!  It worked! Awesome, thank you so much....

Now, I only need to find out how to make my S VIDEO cable work (and do you have any idea why I can't enable any kind of Visual Effects in my Appearance Preferences?).

I'm learning more and more everday; Linux is SO much moe interesting, even though SONY is one company I'll never buy laptop from, ever again...

 :^P

---

### Post by Neonjack on 2007-12-02
Hum, now my laptop speakers and headphone jack are playing at the same time...

---

### Post by syberdave on 2007-12-03
> **Neonjack said:**
> Hum, now my laptop speakers and headphone jack are playing at the same time...

Try the latest dev version of the ALSA drivers:
[ftp://ftp.suse.com/pub/projects/alsa/snapshot/driver](ftp://ftp.suse.com/pub/projects/alsa/snapshot/driver)

I tried the ALSA in kernel 2.6.23.9 (latest as of right now), and sound goes through the speakers and the headphone jack. But with the latest dev version as of yesterday, the speakers do cut off properly when you plug in headphones.

Also, about the SVIDEO cable, play with the xrandr utility. I don't have a TV to play with, but I was able to mess with a VGA monitor with it.

---

### Post by Neonjack on 2007-12-03
Hey syberdave, I tried what you said and it went OK but didn't work: sound still plays in both output (laptop speakers and external speakers) at the same time, plus xrandr just added an applet to instant-switch my resolution, ie from 1280X800 to 800X600, let's say, but nothing related to outputting from my SVIDEO to my TV...

Still hoping!

---

### Post by Neonjack on 2007-12-15
Hi everyone, still no luck with my card...

 :^(

No vids on TV for me and mydaughter during the vacations!

Seems like there's nothing to do with Intel965 x3100 cards, what a shame!

---

### Post by syberdave on 2007-12-15
Are you sure you're using xrandr? It's a command-line application. You probably used "krandrtray" which is some KDE app.

Here's the output that shows that I have a VGA monitor connected:
> tangent:~# xrandr
Screen 0: minimum 320 x 200, current 1280 x 1024, maximum 1280 x 1280
VGA connected 1280x1024+0+0 (normal left inverted right) 376mm x 301mm
   1280x1024      60.0*+   59.9  
   1024x768       75.1     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        75.0     72.8     66.7     60.0  
   720x400        70.1  
LVDS connected 1280x800+0+0 (normal left inverted right) 0mm x 0mm
   1280x800       57.7*+   60.0  
   1280x768       60.0  
   1152x768       54.8  
   1024x768       85.0     75.0     70.1     60.0  
   832x624        74.6  
   800x600        85.1     72.2     75.0     60.3     56.2  
   640x480        85.0     72.8     75.0     59.9  
   720x400        85.0  
   640x400        85.1  
   640x350        85.1  
TV disconnected (normal left inverted right)

I was able to enable "VGA" by using: xrandr --output VGA --auto
And judging from the output there, you might be able to enable "TV" using: xrandr --output TV --auto
I don't have a TV to try it on.

If that doesn't work, make sure that in xorg.conf, you're using the intel driver.
To change what driver you're using, use: sudo dpkg-reconfigure xserver-xorg

---

### Post by Neonjack on 2007-12-17
Ok, making progress.  I was able to connect it to my TV but my laptop LCD went dark, which made sense.  But when I disconnected the SVIDEO cable, it didn't came back, had to log-out/log in.

Also, once on TV, it's extremely brilliant, all washed out, and I haven't found out a way to tone it all down a bit... 

Is there some application available to let me configure once and for all a second screen that I can just switch on and off, between laptop and TV?

Surely there is...

All my problems are almost solved!

 :^D

Ah!  my WLAN now!!!!

eh heh....

---

