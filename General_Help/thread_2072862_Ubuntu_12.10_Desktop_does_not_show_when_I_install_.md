---
title: "Ubuntu 12.10 Desktop does not show when I install nvidia drivers"
date: 2012-10-18
forum: General Help
---

### Post by Chelidze on 2012-10-18
Desktop does not shows after I installed nvidia [COLOR="Magenta"]experimental drivers[/COLOR]. I tried nvidia simple [COLOR="Red"]proprietary[/COLOR] drivers, and they did not work either.

Here is how it looks. This is not cropped or any thing. This is how it looks, after the installation of the drivers the desktop resolution decreased from 1440X900 to 1024X768

[http://i.imgur.com/0vi72.png](http://i.imgur.com/0vi72.png)

The desktop only shows desh and panels  when I use the [COLOR="DarkRed"]open source[/COLOR] drivers.

Is there any way to fix this so I can get better performance??

Thank you in advance.

---

### Post by lunchb0x91 on 2012-10-18
The exact same thing is happening with my installation even when using the recommended proprietary drivers. 

I currently am using a nvidia gts 450.

---

### Post by Lisiano on 2012-10-18
Same here (GT320). I can't find anything in dmesg that might be useful. I can still open a terminal with Ctrl+Alt+T and start other apps, but since unity doesn't start properly, windows have no borders.

Also, running nvidia-xconfig cause the resolution to go even lower.
Currently I tried nvidia-current and nvidia-experimental-304.

```
lisiano@Lisiano-Ubuntu:~$ lsmod
Module                  Size  Used by
nvidiafb               45561  0 
fb_ddc                 12525  1 nvidiafb
i2c_algo_bit           13413  1 nvidiafb
vgastate               21001  1 nvidiafb
bnep                   18140  2 
rfcomm                 46619  0 
bluetooth             209199  10 bnep,rfcomm
parport_pc             32688  0 
ppdev                  17073  0 
vesafb                 13797  1 
snd_hda_codec_hdmi     32007  4 
snd_hda_codec_realtek    77876  1 
kvm_amd                55604  0 
kvm                   414070  1 kvm_amd
psmouse                95552  0 
microcode              22803  0 
edac_core              52451  0 
snd_usb_audio         130279  1 
snd_usbmidi_lib        24953  1 snd_usb_audio
snd_seq_midi           13324  0 
edac_mce_amd           23303  0 
serio_raw              13215  0 
snd_seq_midi_event     14899  1 snd_seq_midi
k10temp                13126  0 
snd_seq                61521  2 snd_seq_midi,snd_seq_midi_event
snd_rawmidi            30512  2 snd_usbmidi_lib,snd_seq_midi
usblp                  18140  0 
snd_seq_device         14497  3 snd_seq_midi,snd_seq,snd_rawmidi
snd_hda_intel          33491  5 
snd_hda_codec         134212  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13602  2 snd_usb_audio,snd_hda_codec
snd_pcm                96580  4 snd_hda_codec_hdmi,snd_usb_audio,snd_hda_intel,snd_hda_codec
video                  19335  0 
gspca_sonixj           33232  0 
gspca_main             28322  1 gspca_sonixj
snd_timer              29425  2 snd_seq,snd_pcm
wmi                    19070  0 
videodev              120309  1 gspca_main
mac_hid                13205  0 
snd                    78734  24 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_usb_audio,snd_usbmidi_lib,snd_seq,snd_rawmidi,snd_seq_device,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_timer
soundcore              15047  1 snd
snd_page_alloc         18484  2 snd_hda_intel,snd_pcm
i2c_nforce2            13013  0 
lp                     17759  0 
parport                46345  3 parport_pc,ppdev,lp
hid_generic            12493  0 
uas                    17844  0 
usbhid                 46947  0 
hid                   100366  2 hid_generic,usbhid
usb_storage            48838  0 
firewire_ohci          40401  0 
firewire_core          64368  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
forcedeth              67156  0 
lisiano@Lisiano-Ubuntu:~$ 
```*Note: The nvidiafb module was modprobed by me, it made the VT bearable but X is still not using the driver (EDIT: Scratch that, did nothing)*
I'll go and try to probe the driver, if I find it.

EDIT: Okay... This is... Weird. I can't find the kernel module. Like it's not even present in the system. Guh. Poking around in packages, here I come.

---

### Post by Lisiano on 2012-10-18
Really? REALLY? Package maintainers. Why the heck did you forget to add [linux-headers-generic](apt://linux-headers-generic) as a dependency!? *(EDIT: Nvm, it is actually a dependency, why the heck didn't it get pulled during installation then...)*

Guh.

Anyway, to fix this "bug", you will need to install this [linux-headers-generic](apt://linux-headers-generic). After that, revert to nouveau (If you didn't already) and install whatever driver you wanted to use.

Or if you are too lazy to revert first, open a terminal (Ctrl+Alt+T) then type in the following:

This if you have nvidia-current (proprietary,tested)
```
sudo dpkg-reconfigure nvidia-current
```

This if you have nvidia-current-updates (proprietary)
```
sudo dpkg-reconfigure nvidia-current-updates
```

This if you have nvidia-experimental-304 (proprietary)
```
sudo dpkg-reconfigure nvidia-experimental-304
```

Then after a reboot, all will be dandy.

---

### Post by Chelidze on 2012-10-18
> **Lisiano said:**
> Really? REALLY? Package maintainers. Why the heck did you forget to add [linux-headers-generic](apt://linux-headers-generic) as a dependency!? *(EDIT: Nvm, it is actually a dependency, why the heck didn't it get pulled during installation then...)*

Guh.

Anyway, to fix this "bug", you will need to install this [linux-headers-generic](apt://linux-headers-generic). After that, revert to nouveau (If you didn't already) and install whatever driver you wanted to use.

Or if you are too lazy to revert first, open a terminal (Ctrl+Alt+T) then type in the following:

This if you have nvidia-current (proprietary,tested)
```
sudo dpkg-reconfigure nvidia-current
```

This if you have nvidia-current-updates (proprietary)
```
sudo dpkg-reconfigure nvidia-current-updates
```

This if you have nvidia-experimental-304 (proprietary)
```
sudo dpkg-reconfigure nvidia-experimental-304
```

Then after a reboot, all will be dandy.

wow thank you for the fix

---

### Post by Hideaki on 2012-10-19
> **Lisiano said:**
> Really? REALLY? Package maintainers. Why the heck did you forget to add [linux-headers-generic](apt://linux-headers-generic) as a dependency!? *(EDIT: Nvm, it is actually a dependency, why the heck didn't it get pulled during installation then...)*

Guh.

Anyway, to fix this "bug", you will need to install this [linux-headers-generic](apt://linux-headers-generic). After that, revert to nouveau (If you didn't already) and install whatever driver you wanted to use.

Or if you are too lazy to revert first, open a terminal (Ctrl+Alt+T) then type in the following:

This if you have nvidia-current (proprietary,tested)
```
sudo dpkg-reconfigure nvidia-current
```

This if you have nvidia-current-updates (proprietary)
```
sudo dpkg-reconfigure nvidia-current-updates
```

This if you have nvidia-experimental-304 (proprietary)
```
sudo dpkg-reconfigure nvidia-experimental-304
```

Then after a reboot, all will be dandy.

How the hell did that happen? *facepalm*
Working now, that's for pointing that out.

---

### Post by pjman on 2012-10-19
> **Lisiano said:**
> Really? REALLY? Package maintainers. Why the heck did you forget to add [linux-headers-generic]("apt://linux-headers-generic") as a dependency!? *(EDIT: Nvm, it is actually a dependency, why the heck didn't it get pulled during installation then...)*

Guh.

Anyway, to fix this "bug", you will need to install this [linux-headers-generic]("apt://linux-headers-generic"). After that, revert to nouveau (If you didn't already) and install whatever driver you wanted to use.

Or if you are too lazy to revert first, open a terminal (Ctrl+Alt+T) then type in the following:

This if you have nvidia-current (proprietary,tested)
```
sudo dpkg-reconfigure nvidia-current
```This if you have nvidia-current-updates (proprietary)
```
sudo dpkg-reconfigure nvidia-current-updates
```This if you have nvidia-experimental-304 (proprietary)
```
sudo dpkg-reconfigure nvidia-experimental-304
```Then after a reboot, all will be dandy.

Thank you!!

[s][Bug #1068942]("https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-updates/+bug/1068942") has been reported.[/s]

Duplicate of [Bug #1068341]("https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-updates/+bug/1068341")

---

### Post by paulelena on 2012-10-20
It didn't work for me to install nvidia-current... What could have happened?

---

### Post by polmak on 2012-10-20
> **Lisiano said:**
> Really? REALLY? Package maintainers. Why the heck did you forget to add [linux-headers-generic]("apt://linux-headers-generic") as a dependency!? *(EDIT: Nvm, it is actually a dependency, why the heck didn't it get pulled during installation then...)*

Guh.

Anyway, to fix this "bug", you will need to install this [linux-headers-generic]("apt://linux-headers-generic"). After that, revert to nouveau (If you didn't already) and install whatever driver you wanted to use.

Or if you are too lazy to revert first, open a terminal (Ctrl+Alt+T) then type in the following:

This if you have nvidia-current (proprietary,tested)
```
sudo dpkg-reconfigure nvidia-current
```This if you have nvidia-current-updates (proprietary)
```
sudo dpkg-reconfigure nvidia-current-updates
```This if you have nvidia-experimental-304 (proprietary)
```
sudo dpkg-reconfigure nvidia-experimental-304
```Then after a reboot, all will be dandy.

Thanks worked for me , can't believe this actually got through, never going to entice new users with show stoppers like thus

---

### Post by avidesh on 2012-10-20
I have on board intel graphics accelerator...
which driver is suitable in my case?
I tried installing nvidia-current and then running ```
sudo dpkg-reconfigure nvidia-current
```

I still get an error that says system is running in low graphics mode.

I still get the old desktop but no launcher or top bar

---

### Post by oldfred on 2012-10-20
Did you install the kernel headers first? For me that installed the current kernel's headers.

sudo apt-get install linux-headers
sudp apt-get purge nvidia*
sudo apt-get install nvidia-current
sudo dpkg-reconfigure nvidia-current

change nvidia-current to nvidia-current-updates or nvidia-experiment-304 if you want to be an the edge or really need the newer version for some reason.

---

### Post by Lisiano on 2012-10-20
Don't install nVidia drivers for Intel GPUs. Same goes for ATI. If you mean you have an onboard Intel GPU AND a separate (discrete) nVidia GPU, you will have to stick to nouveau since using proprietary drivers blocks off access to other GPU drivers.

@oldfred, 304 is not edgy. That's a blunt edge. 310 is edgy :3

---

### Post by avidesh on 2012-10-21
thanks I removed the nvidia drivers completely and now it works. I get unity launcher.

However the system has become dreadfully slow.

Any tweaks?

---

### Post by kyalpani on 2012-10-21
I have been fighting with this issue for two days now and I am quite frustrated. 

As soon as I install the properietray nVidia drivers (my viao runs with NVIDIA GeForce GT 640M LE GPU) reboot works fine and I get the Login menu, but when I log in there is no unity Launcher... when I remove the nvidia proprietary drivers and then reboot, sometimes the login window does not show (and I type in my password blind to login), my desktop is back but due to the compiz demon sometimes the performance lags (5-40% cpu hog) and there are frequent desktop crashes and black screens (of death ala windows blue screen of death). Usually cleaning up ~/.compiz* and ~/.config/compiz* directories + "setsid unity" + reboot restores my environment for a while...

Disabling/Enabling stuff over the compiz management interface (ccsm command) almost everytime crashes my desktop with no possibilty of recovery unless I go through the cycle of deleting the aforementioned directories + reboot etc...

I have done 30+ reboots since yesterday...

I am at a loss as to why 12.10 was released without any possibilty to stick with the 2D interface which is stable. I really don't care about these 3D bells and whistles. I wish there was a relatively painless way to revert to 12.04 that was a relatively good release. 

My message to ubuntu: I know that there is no implied warranty etc. etc. when we use this software but still, my (and others I am sure) work existentially depends on this platform nowadays so please be a bit more careful, take your time in releasing! By definition, a release is a stable thing...I learned my lesson and will not upgrade this fast again!

In any case, if anyone has an idea how resolve the sitiation, e.g. disable compiz (!&%?!) without compromising my whole installation I really would appreciate it if you shared it...

thank you very much

---

### Post by oldfred on 2012-10-21
When at screen with no Unity bar. Right click may give some info.

cntrl-alt f1 or f2 to get to terminal also works
sudo apt-get install linux-headers
sudp apt-get purge nvidia*
sudo apt-get install nvidia-current
sudo dpkg-reconfigure nvidia-current
(Same for fglrx also)


If headers are installed you can do this also at screen.

When you see you are in the desktop but no icon or bar, right click to change desktop background
When the window appear, click  on all settings, now you see the system settings window.
Next, click on Software source, go in the additional drivers tab.
Select the 3 rd option, using video driver for the nvidia or AMD... fglrx-upgrade

---

### Post by kyalpani on 2012-10-21
thanks alot for your reply... I went through all the steps as you described but in the last screen where I except to see addtional drivers, the list is empty and it says "No proprietary drivers are in use"

what should I do now?

My unity desktop still has no launcher

---

### Post by Lisiano on 2012-10-21
> **oldfred said:**
> cntrl-alt f1 or f2 to get to terminal also works
```
sudo apt-get install linux-headers
sudp apt-get purge nvidia*
sudo apt-get install nvidia-current
sudo dpkg-reconfigure nvidia-current
```
(Same for fglrx also)There is no need to purge and reinstall the driver. dpkg-reconfigure will make the driver compile. Else it's just going to compile the driver another time.

---

### Post by kyalpani on 2012-10-21
Thank you for your help again. Instead wasting more time trying to repair 12.10 I reinstalled 12.04 as I was quite happy with it. I think leaving out unity 2D in the new release was a big mistake. Compiz is quite buggy.

---

### Post by espenore on 2012-10-22
> **Lisiano said:**
> Really? REALLY? Package maintainers. Why the heck did you forget to add [linux-headers-generic](apt://linux-headers-generic) as a dependency!? *(EDIT: Nvm, it is actually a dependency, why the heck didn't it get pulled during installation then...)*

Guh.

Anyway, to fix this "bug", you will need to install this [linux-headers-generic](apt://linux-headers-generic). After that, revert to nouveau (If you didn't already) and install whatever driver you wanted to use.

Or if you are too lazy to revert first, open a terminal (Ctrl+Alt+T) then type in the following:

This if you have nvidia-current (proprietary,tested)
```
sudo dpkg-reconfigure nvidia-current
```

...

Then after a reboot, all will be dandy.

I fist got an error messsage saying that nvidia-current was not correctly installed. I then tried a

> sudo apt-get install nvidia-current

and now things work!

Thank you very much for pointing out the way to go and check!

Espen

---

### Post by flavouride on 2012-10-22
+1 encountered the same problem and fortunately noticed that "linux-headers-3.5.0-17" was removed at the end of the fresh installation

---

### Post by stankopp on 2012-10-24
None of this is helping me.  I can put a different card in my machine and have a launcher, but the system is extremely slow.

If I put my nvidia card in, the system is not sluggish but I have no launcher or panel.  This is the kind of stuff that keeps Ubuntu from becoming mainstream...

---

### Post by avidesh on 2012-10-25
I have added a new graphics card NVIDIA GT620.
I also added current nvidia-driver.. as per the instructions in this thread.

The unity bar is showing up and the performance in not sluggish as it was before.

However at the startup I continue to get a message that the system is running in low resolution the display card can't be detected etc.

it suggest an option to run in low resolution mode. I select that and everything works ok. I even get high resolution.

What could be the problem for initial message? That appears every time.

---

### Post by avidesh on 2012-10-27
Do I need to change the greeter?

my lightdm.conf file has following in it.


```
autologin-session=lightdm-autologin
greeter-session=lightdm-gtk-greeter
user-session=ubuntu
```

---

### Post by YokoZar on 2012-11-07
> **Lisiano said:**
> Really? REALLY? Package maintainers. Why the heck did you forget to add [linux-headers-generic](apt://linux-headers-generic) as a dependency!? *(EDIT: Nvm, it is actually a dependency, why the heck didn't it get pulled during installation then...)*

Guh.

This is not an oversight, it's a shortcoming of dpkg.  That's why the linked bug is against dpkg and not nvidia-drivers -- there's no way to properly specify this dependency.

To be clear about what's going on here:

The NVidia Proprietary drivers need to build a kernel module at install time, which in turn needs the kernel headers. The driver install will build the driver for every kernel it finds matching headers for on the system at install time.

If you did something like install the new driver individually and then update the system to install the kernel afterwards, it might not have been built.


This isn't a trivial problem to solve at the packaging layer, since the driver install needs to also support the situation where someone doesn't want the latest kernel and latest kernel headers (like a strict dependency on the -generic package would force)

---

### Post by BandC on 2012-11-08
Hi. I have the same problem as most of the posters here. I recently upgraded to Ubuntu 12.10 (64-bit) and I have an Nvidia GTX 460. I get low res. desktop with no panel / borders. When I switch to nouveau drivers the desktop is fine but the performance is horrible, everything is sluggish.

I tried what is suggested here several times but it doesn't work. I still get the low res. desktop with no panel with Nvidia drivers when I reboot.

Here's my terminal output. Are the drivers installing OK? Can you think of anything wrong?

Thanks.

b@b-desktop:~$ sudo apt-get -y install linux-source linux-headers-generic && sudo apt-get -y remove nvidia-current nvidia-current-updates nvidia-experimental-304 && sudo apt-get -y install nvidia-current-updates
[sudo] password for b: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-generic is already the newest version.
linux-source is already the newest version.
The following package was automatically installed and is no longer required:
  nvidia-settings-updates
Use 'apt-get autoremove' to remove it.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'nvidia-current' is not installed, so not removed
Package 'nvidia-current-updates' is not installed, so not removed
Package 'nvidia-experimental-304' is not installed, so not removed
The following package was automatically installed and is no longer required:
  nvidia-settings-updates
Use 'apt-get autoremove' to remove it.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  nvidia-current-updates
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/67.7 MB of archives.
After this operation, 204 MB of additional disk space will be used.
Selecting previously unselected package nvidia-current-updates.
(Reading database ... 360810 files and directories currently installed.)
Unpacking nvidia-current-updates (from .../nvidia-current-updates_304.51-0ubuntu1_amd64.deb) ...
Processing triggers for man-db ...
Setting up nvidia-current-updates (304.51-0ubuntu1) ...
update-alternatives: using /usr/lib/nvidia-current-updates/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode
update-alternatives: using /usr/lib/nvidia-current-updates/alt_ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode
update-initramfs: deferring update (trigger activated)
update-initramfs: Generating /boot/initrd.img-3.0.0-26-generic
INFO:Enable nvidia-current-updates
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/dell_latitude
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/put_your_quirks_here
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/lenovo_thinkpad
DEBUG:Processing quirk Latitude E6530
DEBUG:Failure to match System manufacturer with Dell Inc.
DEBUG:Quirk doesn't match
DEBUG:Processing quirk ThinkPad T420s
DEBUG:Failure to match System manufacturer with LENOVO
DEBUG:Quirk doesn't match
Loading new nvidia-current-updates-304.51 DKMS files...
Building for 3.0.0-26-generic and 3.5.0-18-generic
Building for architecture x86_64
Module build for the currently running kernel was skipped since the
kernel source for this kernel does not seem to be installed.
Building initial module for 3.5.0-18-generic
Done.

nvidia_current_updates:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.5.0-18-generic/updates/dkms/

depmod.......

DKMS: install completed.
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.5.0-18-generic
b@b-desktop:~$

---

### Post by BandC on 2012-11-09
Can anyone please at least tell me if they see anything wrong in my console output above? Anything out of norm or not installed correctly? Thanks.

I am especially worried about this:

Module build for the currently running kernel was skipped since the
kernel source for this kernel does not seem to be installed.

in my console output above. Is this normal? Can that be that I am still missing some source package and that's why NVidia drivers are not working?

---

### Post by bogan on 2012-11-10
Hi!,** B&C,**

You Posted> :xxx Loading new nvidia-current-updates-304.51 DKMS files...
Building for 3.0.0-26-generic and 3.5.0-18-generic
Building for architecture x86_64
Module build for the currently running kernel was skipped since the
kernel source for this kernel does not seem to be installed.
Building initial module for 3.5.0-18-generic
Done.

nvidia_current_updates:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.5.0-18-generic/updates/dkms/ xxxWhich implies that the running kernal was 3.0.0-26-generic, [not 12.10, 3.5.0-18-generic] and the 3.0.0-26 source or headers were missing.

What does 'uname -r' show ??

Chao!,** bogan.**

---

### Post by BandC on 2012-11-10
Thank you very much for your reply bogan!

uname -r shows: 3.0.0-26-generic

I actually upgraded from 11.04 to 11.10 to 12.04 to 12.10. So you think for some reason the newest Ubuntu kernel didn't get installed? How can I install 3.0.0-26 source or how can I upgrade to 3.5.0-18? What's the best course of action?

Again, thanks a lot!

---

### Post by BandC on 2012-11-10
Fixed! Here was the problem in case other people have the same issue: Apparently my grub menu.lst wasn't updated when I did upgrades so it was booting into 3.0.0-26 kernel. I regenerated menu.lst by doing:

sudo update-grub

When my PC booted into the new kernel Nvidia drivers worked fine.

Thanks!

---

### Post by gsilves30 on 2012-11-10
Hi all, 

I just wanted to check if there is something I am missing. I have:

- installed linux-source and linux-headers-3.5.0-18-generic for x86_64
- installed the NVIDIA blob both stable and also tried experimental via apt

No errors on the install, when I reboot I get a blank no unity desktop still and if I run nvidia-xconfig I get some 480p resolution instead. if I run nvidia-settings I actually am told my nvidia X driver is not in use.

Any pointers?

---

### Post by bogan on 2012-11-11
Hi!, [B]BandC,
[/B]
AFAIK: " grub menu.lst" is a relic of legacy grub and is not used by Grub 2, either v1.99 or v2.00.

Which suggests, now you are booting to 12.10, 3.5.0-18, if it still exists, you need to purge legacy grub and install grub-pc. [ I am not sure of the exact commands, but be carefull! ].

Does it show Grub v2.00 in the heading of the grub boot menu?

Edit:
If not, you probably need to run: 'sudo update-grub' again,  now you are booting to 12.10, and possibly :'sudo grub-install /dev/sda'; otherwise control will remain with the grub in 3.0.0-26

Chao!,** bogan.**

---

### Post by Tobeus on 2012-11-14
I have the Nvidia GTX 460 running with an E6750 Core2Duo proc on my desktop and have the same issues.  The nouveau driver doesn't work, purged all nvidia drivers and tried each one individually with purges in between (nvidia-current, nvidia-current-updates, nvidia-experimental...) without luck.  The only way I have been able to get into a somewhat working desktop with Unity is to download the 3.10 experimental drivers from the nvidia website.  I allowed the installer to apply the file into /etc/modprobe.d to stop the nouveau driver from loading and continued the install.  There were some complaints by the installer, but it seemed to work ok after a reboot.  There are still some major issues including bugs while gaming and whatnot, but at least it works.

I still think I'm going back to 12.04 for a while because it seems like 12.10 is only half-baked for some nvidia users.  Without some kind of decent site for hardware compatibility checks that are more user friendly than the ones in this forum, I'm not going to bother buying another video card without proof that it is well supported in linux by nvidia, unity, and ubuntu.  Good luck everyone!

-Tobeus

---

### Post by andersgb1 on 2012-11-14
> **Tobeus said:**
> I have the Nvidia GTX 460 running with an E6750 Core2Duo proc on my desktop and have the same issues.  The nouveau driver doesn't work, purged all nvidia drivers and tried each one individually with purges in between (nvidia-current, nvidia-current-updates, nvidia-experimental...) without luck.  The only way I have been able to get into a somewhat working desktop with Unity is to download the 3.10 experimental drivers from the nvidia website.  I allowed the installer to apply the file into /etc/modprobe.d to stop the nouveau driver from loading and continued the install.  There were some complaints by the installer, but it seemed to work ok after a reboot.  There are still some major issues including bugs while gaming and whatnot, but at least it works.

I still think I'm going back to 12.04 for a while because it seems like 12.10 is only half-baked for some nvidia users.  Without some kind of decent site for hardware compatibility checks that are more user friendly than the ones in this forum, I'm not going to bother buying another video card without proof that it is well supported in linux by nvidia, unity, and ubuntu.  Good luck everyone!

-Tobeus

Yeah, same thing goes for me. I've tried (re)installing all three versions of the driver, making sure both linux-headers and -source are installed, used dpkg-reconfigure as well as nvidia-xconfig a bunch of times and so on (yes, I also verified that running kernel version matched that of headers and source). Using nouveau is horrible - slow performance and excessive battery drain. I remember two things that caught my attention during this process:

1) When installing nvidia-* drivers, it generates a weird "DEBUG:" message about some "quirks", saying that it doesn't match my model with Lenovo T420.
2) After installation, dmesg at one point reported some conflict, saying that nvidia was unable to load because of nouveau being loaded first. I then just removed noveau.

I'm running a Lenovo W520 with Optimus, things worked like a charm in Precise. Now I had to complete disable discrete graphics in the BIOS, leaving me with the nice experience of an Intel GPU for Unity 3D :) Oh well, at least battery now lasts 6+ hours...

---

### Post by graingert on 2012-11-17
You might be experiencing one or both of:

[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/1076281](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/1076281)

[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/1078598](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/1078598)

---

### Post by andersgb1 on 2012-11-17
> **graingert said:**
> You might be experiencing one or both of:

[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/1076281](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/1076281)

[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/1078598](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/1078598)

Nope. Already installed all headers/source (first link) and I cannot even open nvidia-settings without getting a warning that the drivers aren't in use (second link).

---

### Post by jeffisabelle on 2012-11-19
I have the same issue. I tried many solutions step by step mentioned here, askubuntu etc. (including complete reinstall of unity, compiz, lightdm, nvidia drivers, nouveau) no luck at all. Still no top panel, no launcher or dash. 

The only solution was installing gnome-shell and log in  to it instead of unity, for me. I will keep using it unless there is a comprehensive tutorial which explains the problem and solutions gently.

---

### Post by BlastXng on 2012-11-30
> **jeffisabelle said:**
> I have the same issue. I tried many solutions step by step mentioned here, askubuntu etc. (including complete reinstall of unity, compiz, lightdm, nvidia drivers, nouveau) no luck at all. Still no top panel, no launcher or dash. 

The only solution was installing gnome-shell and log in  to it instead of unity, for me. I will keep using it unless there is a comprehensive tutorial which explains the problem and solutions gently.

After reading this entire thread and following the steps contained within it and reading through and using steps outlined here:

[http://askubuntu.com/questions/202677/nvidia-driver-doesnt-work-in-12-10]("http://askubuntu.com/questions/202677/nvidia-driver-doesnt-work-in-12-10")

I still have no joy with NVIDIA on my Dell ES4620 laptop.. :mad:

1. My BIOS has been set correctly, NVIDIA is enabled, Intel is not.
2. I have updated all of my packages.
3. Headers & Sources have been downloaded and installed.

I went from 11.04 to 12.10 and I am thinking of going back to all the way to 11.04. 

Any thoughts or suggestions?

Blast

---

### Post by kokoshmusun on 2012-12-01
I had horrible NVidia problems with 12.10, it was a completely unusable system.  I tried bunch of things without success. I went back to 12.04.  Things work very well.  In my experience, it's not worth your time to try to fix it.  Just stick with 12.04.  If things get fixed, you can jump on to 13.04 later.

---

### Post by faabiioo on 2012-12-03
Hi,
since last Wednesday I'm struggling to make my Nvidia gpu card with my freshly installed ubuntu 12.10 work toegther. I've tried every single possible solution I've encountered in forums and wikis and such. And I eventually got to a conclusion: there is no way, at the moment, to have it up and properly running. Hybrid graphics on an Intel laptop just drive you crazy.

I've experienced the whole system freezing repeatedly; audio disappearance  even when everything said that hardware and software was properly configured; I've seen no launch-bar, no menu-bar, gigantic icons and mouse pointer; unity with no 3d; weird psychedelic colours; even the touchpad once stopped functioning, apparently without a reason, since all drivers where ok. And I mean it: as soon as I reverted whichever last attempt to make the nvidia card work, everything was back and fine. 

I have tried drivers from "apt-get" - nvidia-current, bumblebee-nvidia and related - latest unix driver from NVIDIA web site (as of today, 310.19); I have tried those coming with the cuda toolkit (I actually need my GPU card just to let me work with cuda), I've written in forums, asked questions, read over and over again solutions and suggestions for a week almost, but still my laptop can be used only with its Intel graphic card. And it's actually good, except I'm supposed to use cuda for my work and I can't. And, of course, I'd never, ever, switch to windows.
I'm looking forward to find a solution - and i don't even want it to be easy! - and be one day able to use my new laptop.

Can somebody give me some hopes?

---

### Post by andersgb1 on 2012-12-03
> **faabiioo said:**
> Hi,
since last Wednesday I'm struggling to make my Nvidia gpu card with my freshly installed ubuntu 12.10 work toegther. I've tried every single possible solution I've encountered in forums and wikis and such. And I eventually got to a conclusion: there is no way, at the moment, to have it up and properly running. Hybrid graphics on an Intel laptop just drive you crazy.

I've experienced the whole system freezing repeatedly; audio disappearance  even when everything said that hardware and software was properly configured; I've seen no launch-bar, no menu-bar, gigantic icons and mouse pointer; unity with no 3d; weird psychedelic colours; even the touchpad once stopped functioning, apparently without a reason, since all drivers where ok. And I mean it: as soon as I reverted whichever last attempt to make the nvidia card work, everything was back and fine. 

I have tried drivers from "apt-get" - nvidia-current, bumblebee-nvidia and related - latest unix driver from NVIDIA web site (as of today, 310.19); I have tried those coming with the cuda toolkit (I actually need my GPU card just to let me work with cuda), I've written in forums, asked questions, read over and over again solutions and suggestions for a week almost, but still my laptop can be used only with its Intel graphic card. And it's actually good, except I'm supposed to use cuda for my work and I can't. And, of course, I'd never, ever, switch to windows.
I'm looking forward to find a solution - and i don't even want it to be easy! - and be one day able to use my new laptop.

Can somebody give me some hopes?

Thanks for this elaborate post, faabiioo! I think you summarized the situation for many of us quite well. As mentioned earlier, I went through the same ordeal as you, but to no avail. So I think, based on this, we can answer your final question by: no, not at this point.

We will probably have to wait until the Ubuntu developers find a solution to this. At this point, I can't stop wondering:

1) How many users are using Ubuntu 12.10?
2) How high a percentage of those in 1) have NVidia cards?
3) How high a percentage of those in 2) saw this as the last straw and turned away from Ubuntu?

---

### Post by mdshann on 2012-12-12
Installed 12.10 today. had this issue. I went to install the headers, which worked fine. I then ran dpkg-reconfigure nvidia-current and it said that the headers for the currently running kernel did not exist. OK, so we'll do an apt-get update && apt-get upgrade to make sure I am on the latest kernel. It held back the latest kernel and I had to manually ask it to install the new kernel with apt-get install linux-image-generic. After that install finished I rebooted and everything worked perfectly.


Looking through my unity panel start menu thingy, what happened to "additional drivers" that used to do all this crap for us?

---

### Post by andersgb1 on 2012-12-12
> **mdshann said:**
> Installed 12.10 today. had this issue. I went to install the headers, which worked fine. I then ran dpkg-reconfigure nvidia-current and it said that the headers for the currently running kernel did not exist. OK, so we'll do an apt-get update && apt-get upgrade to make sure I am on the latest kernel. It held back the latest kernel and I had to manually ask it to install the new kernel with apt-get install linux-image-generic. After that install finished I rebooted and everything worked perfectly.


Looking through my unity panel start menu thingy, what happened to "additional drivers" that used to do all this crap for us?

I also tried all of that, and I can execute dpkg-reconfigure without errors, but still doesn't work on my system...

---

### Post by Geezanansa on 2012-12-12
This is a frustrating situation to be in.  That is hundreds of people have collaborated in making ubuntu possible.  And hundreds more developing drivers.  Yet thousands are struggling to boot ubuntu.
 Is it possible the nvidia drivers have improved so much they just aint unity friendly because of unity, nouveau(vesa) and mesa(opengl) dependencies within ubuntu?  Is it possible grub2 is somehow influencing these graphics issues?

Regardless of which the solution probably means waiting on updates.

---

### Post by bogan on 2012-12-12
Hi!, **mdshann**,

You Posted:> Looking through my unity panel start menu thingy, what happened to "additional drivers" that used to do all this crap for us?      In 12.10, the 'Additional Drivers' program is accessed via a Tab in Software Sources.

From the top Right cog menu Icon, select: ' System Settings...' ; or Right-Click on the Desktop, select: 'Change Desktop Background', select the 'All Settings' Tab;

[Note; This second path can work even when a full unity GUI screen, with Panels & Icons, is not available.]

In the System Settings window scroll to 'System>Software Sources' and select it.

After a delay  from updating the Sources file, the window will open; the right-hand Tab is for:  'Additional Drivers'.

Simple, is it not??

Chao!, **bogan**.

---

### Post by RWayne on 2012-12-12
It seems ubuntu is going downhill.... I'm not a novice user but I can't trust my job to an unreliable system. I tried everything to make my nvidia card work on 12.10, but no deal. I'll keep some distance from it for sometime, will try another distro as I'm having to type this message on my nexus 7 although I have stuff to be done on my PC. Good luck for you, but I just don't have time to fight with my OS anymore.

For the time, I will be using W7 and android only for everyday use, and a minimal distribution for when I have to code something.

---

### Post by rasmus91 on 2012-12-19
> **mdshann said:**
> Installed 12.10 today. had this issue. I went to install the headers, which worked fine. I then ran dpkg-reconfigure nvidia-current and it said that the headers for the currently running kernel did not exist. OK, so we'll do an apt-get update && apt-get upgrade to make sure I am on the latest kernel. It held back the latest kernel and I had to manually ask it to install the new kernel with apt-get install linux-image-generic. After that install finished I rebooted and everything worked perfectly.


Looking through my unity panel start menu thingy, what happened to "additional drivers" that used to do all this crap for us?

this
```
apt-get install linux-image-generic
```
saved my desktop from getting windows again.

thank you mdshann

---

### Post by bruceforsberg on 2013-01-11
I had a similiar problem. Thanks for all the feedback here. I took an SSD out of an old HP NVIDIA graphics laptop with Ununtu 12.10 on it and installed it in a new Toshiba Portege R835 with Intel Sandy Bridge graphics. Ununtu desktop would not work. Only a basic Gnome desktop would work. I had to remove all NVIDIA stuff in order to get things to work.

sudo apt-get purge nvidia*

---

### Post by kokoshmusun on 2013-01-12
I found 12.10 to be completely unusable. Reverted to 12.04 but even that does not provide the awesome, glitchless experience I had in 10.x and 11.x.  On the other hand, Win7 seems to JUST WORK, unlike vista.  So I found myself constantly booting into win instead of ubuntu.  Today, I just had to face the fact that I may have to stop using Ubuntu for a while.

---

### Post by Boorhin on 2013-01-21
> **BandC said:**
> Fixed! Here was the problem in case other people have the same issue: Apparently my grub menu.lst wasn't updated when I did upgrades so it was booting into 3.0.0-26 kernel. I regenerated menu.lst by doing:

sudo update-grub

When my PC booted into the new kernel Nvidia drivers worked fine.

Thanks!

Hi I am regularly running into this problem with Ubuntu 12.04 and it is BandC that provided me with the answer. I regularly have updates that I install and I regularly get my driver not to work. I now understand why. So I will try to be clear on what I did and what I think I understood. 

My actual kernel version was not the one the driver thought I had.

Check your version with:
 uname -r 
It must fit your release '-generic'.

Indeed mine was not fitting so I did:
sudo update-grub

and then I removed my driver (I am not sure this is useful since now the driver will know my kernel version...)
sudo apt-get purge nvidia-current && sudo apt-get -y remove nvidia-current nvidia-current-updates nvidia-experimental-304 
as much as your paranoia goes on what is currently installed on your machine

then you can put the drivers you usually like:

sudo apt-get -y install nvidia-current-updates

And restart X. For the ones which does not know it, use the magic key:

Shift+Ctrl+Alt+SysRq+K

It worked for me, I spent hours and days to understand why my solutions were never stable. Big thanks to BandC. Hope this will help.

Cheers

Boorhin

---

### Post by bogan on 2013-01-21
Hi!, **Boorhin,**

**BandC'**s problem was partly that he had a remnants of a legacy Grub 1.8 or 1.9.[ "grub menu.lst".]

I suspect yours is something different, but what you did is OK.

What usually causes the problem you describe is that a kernal update generates a new grub.conf in an older version, so when you reboot, the grub menu you see has not got the correct address for the newer version.

So it tries to use an nvidia module created for the new version, but is running the older version, which  will be rejected.

This is especially common where more than one version installation are on the same computer.

Running 'sudo update-grub' or 'sudo install-grub sdx', from the new update will correct things. 

Chao,** bogan**.

---

### Post by scottstensland on 2013-04-24
[QUOTE=Lisiano;12307233]Don't install nVidia drivers for Intel GPUs. Same goes for ATI. If you mean you have an onboard Intel GPU AND a separate (discrete) nVidia GPU, you will have to stick to nouveau since using proprietary drivers blocks off access to other GPU drivers.

5 years ago ubuntu worked fine with Nvidia drivers on a laptop with an Nvidia card - however it seems increasingly common today to see laptops who have Nvidia cards to come bundled with a Intel GPU - I wish to code opengl 4.x using my laptop which has a 4.x capable Nvidia card + Intel GPU - so you are saying I need to wait until nouveau handles OpenGL 4.x ?   seems strange linux is behind M$ windows regarding Nvidia card coverage.

---

### Post by andersgb1 on 2013-04-24
Oops, forgot to update this here:

I recently installed BumbleBee ([https://wiki.ubuntu.com/Bumblebee#Installation](https://wiki.ubuntu.com/Bumblebee#Installation)), and everything just worked out of the box, meaning with Optimus enabled in BIOS.

I just followed steps 1-5 in the link above, nothing else. This is on a Ubuntu 12.10 x64 installation on a Lenovo W520 laptop (Intel/NVidia Quadro 2000M).

---

### Post by Bachi on 2013-05-10
For those who still got stuck with a broken Unity even when you're sure your Nvidia/ATI driver's now correct: I noticed that under another user account, evrything was fine, so it must be a user setting that got broken during the driver installations.

After doing 'dconf reset -f /org/compiz' the problem was solved (just had to reconfigure some compiz settings).

---

### Post by Ovy on 2013-06-23
OK, I know this issue has been mentioned and solved, but in my case all solutions which I found aren't working.
 
I have Acer V3 with Geforce 730M and xubuntu 13.04 on it. I want to install drivers from Nvidia for my graphic card. What i did:
 1. Installed linux-headers, linux-source, reinstalled nvidia-current and nvidia-current-updates ([http://ubuntuforums.org/showthread.php?t=2081649&page=2](http://ubuntuforums.org/showthread.php?t=2081649&page=2)).
 2. Did nvidia-xconfig. After rebooting I couldn't change resolution from 640x480, moreover nvidia-xconfig gave an error ```
VALIDATION ERROR: Data incomplete in file /etc/X11/xorg.conf.
 At least one Device section is required.
```
 3.Tried jockey-kde, failed after clicking "turn on", in log i found: ```
Traceback (most recent call last):
 File "/usr/lib/python2.7/dist-packages/jockey/detection.py", line 950, in get_handlers
 execfile(mod, symb)
 File "/usr/share/jockey/handlers/nvidia.py", line 12, in <module>
 from NvidiaDetector.nvidiadetector import NvidiaDetection
 ImportError: No module named NvidiaDetector.nvidiadetector
 2013-06-23 16:38:07,981 DEBUG: loading custom handler /usr/
```
 ```
2013-06-23 16:38:08,071 WARNING: Invalid custom handler module /usr/share/jockey/handlers/fglrx.py
 Traceback (most recent call last):
 File "/usr/lib/python2.7/dist-packages/jockey/detection.py", line 950, in get_handlers
 execfile(mod, symb)
 File "/usr/share/jockey/handlers/fglrx.py", line 11, in <module>
 from NvidiaDetector.alternatives import Alternatives
 ImportError: No module named NvidiaDetector.alternatives
 
```
 
This file has 500 lines, many other warnings and erros in it. I believe that important is that i can't modprobe nvidia-current, there is no such module. I've managed to modprobe a module named nvidia. but after it drivers were't working too.
 
4.nvidia-smi gives 
```
NVIDIA: could not open the device file /dev/nvidiactl (No such device or address).
```
 After making such device with mknod and adding priveleges nothing changes.
 
5.lspci -v gives (here's only graphic card):
 ```
01:00.0 VGA compatible controller: NVIDIA Corporation GK107M [GeForce GT 730M] (rev a1) (prog-if 00 [VGA controller])
 Subsystem: Acer Incorporated [ALI] Device 0648
 Flags: bus master, fast devsel, latency 0, IRQ 7
 Memory at b2000000 (32-bit, non-prefetchable) [size=16M]
 Memory at a0000000 (64-bit, prefetchable) [size=256M]
 Memory at b0000000 (64-bit, prefetchable) [size=32M]
 I/O ports at 2000 [disabled] [size=128]
 Expansion ROM at <ignored> [disabled]
 Capabilities: <access denied>
 
```
 (notice that there are no kernel drivers in use)
 
6.blacklisted few things
 ```

 blacklist amd76x_edac
 blacklist nouveau
 blacklist vga16fb
 blacklist rivafb
 blacklist nvidiafb
 blacklist rivatv
 
```
 Still no effect - I don't know which driver am i using now :/
 
7.purged xserver-xorg-video-nouveau - no effect

8. Tried to install nvidia driver (319.23) manually - installed succesfully, however before installation I've encountered a message saying that this driver couldn't find a chipset compatible with itself (driver's README says it is compatible, so does nvidia website).

9. Did update-grub: there was a change in initail window (the one before logging screen). So I hoped something changed. Nope, still no modules nvidia or nvidia-current

10.Installed bumblebee

So, what else can I do? If there is no hope, which linux should i choose to work with CUDA (I mean, where installation of drivers is easy?).

EDIT: this is what shows during dpkg-reconfigure nvidia-current:
```
 File "/usr/share/apport/package-hooks/dkms_packages.py", line 22, in <module>
    import apport
ImportError: No module named apport
Error! Application of patch buildfix_kernel_3.8.patch failed.
```
and
```

DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/lenovo_thinkpad
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/put_your_quirks_here
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/dell_latitude
DEBUG:Processing quirk ThinkPad T420s
DEBUG:Failure to match V1.13 with ThinkPad T420s
DEBUG:Quirk doesn't match
DEBUG:Processing quirk Latitude E6530
DEBUG:Failure to match Acer with Dell Inc.
DEBUG:Quirk doesn't match

```

---

