---
title: "Fresh Install; problems still exist"
date: 2013-01-17
forum: General Help
---

### Post by Lightning Dragon on 2013-01-17
Hello,

Long story short, Ubuntu 12.04 broke because I could not access the HDD for a few months (lost my PC), tried to log in, did, found hundreds of problems like updating, installing things, removing things and resolution problems. A week straight I tried to fix these problems, including the resolution problem, but couldn't. So today I did a fresh install.

But some of those problems still exist. One is my resolution. My monitor supports 1440x900, but it only gives me 800x600 all the way to 1024x768, and all of those are horrendously zoomed in. 

After the fresh install and the 256 updates installed, I went to my Drivers and activated the recommended driver (which version was in the 200s and not 304.64 for my [Geforce SPARKLE 6600 LE card]("http://www.xgcdb.com/cards/sparkle/geforce-6600-le-sf-px43ldh-passive-edition.html") as that's what I am using on Mint and Windows, and is what is asked for by the computer), but that did not help anything. In fact, after restarting the PC I now get random black blinkings, and then a white-black bar code screen for a few seconds before it gets me to my log in screen. It now recognizes my desktop screen as a labtop screen. Here is an image of it; [http://postimage.org/image/h5ttipzu3/](http://postimage.org/image/h5ttipzu3/)

I tried the command "                            $ xrandr -s 1440x900", but it came back with the following; **Failed to change the screen configuration!**

How can I fix my resolution to 1440x900  and install my card's *proper* driver?  

Any and all help is greatly appreciated.

Thanks!

EDIT: Instructions on how to install 304.64 drivers in Ubuntu 12.04 (should work, I have been told, on Linux Mint and Ubuntu 11.10 ) for a **legacy card** (mine is a Geforce Sparkle **6600** LE);

First, you will need to follow ManamiVixen's instructions, just in case you have other stuff installed.

```
sudo apt-get remove --purge nvidia-current && sudo apt-get autoremove && sudo apt-get install nvidia-current 
```Next, run; 

```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
```Now we need to update it;

```
sudo apt-get update
```Here is where I turned the computer off, not restarted. I unplugged the power supply after it was off, pressed the on button, plugged the cord back in and then turned the system on. Once everything loads up, open the terminal again and run;

```
sudo apt-get install nvidia-current nvidia-settings
```Now you have the nvidia x settings. Open up the Dash menu and type 'nvidia', it should pop up. Look in there and see if you can see this;

[http://postimage.org/image/ycy370otd/](http://postimage.org/image/ycy370otd/)

If you don't see it, then your card is does not need 304.64, but a different driver and the one installed is most likely the one you need. However, if you know that it is wrong (for example, I have 304.64 installed in Mint and Windows), then you can remove them and attempt a manual install of the drivers by downloading the Linux version of it and the right bit type, drag it to the home folder, right click and make it executable, close and then follow these instructions;

[http://neelmohile.wordpress.com/2011/11/02/how-to-manually-install-latest-nvidia-drivers-on-ubuntu-oneiric-11-10/](http://neelmohile.wordpress.com/2011/11/02/how-to-manually-install-latest-nvidia-drivers-on-ubuntu-oneiric-11-10/)

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

As well as the official instructions off Nvidia, which you can find on the same download page where you got the driver. Just click "additional information" and it will tell you what to do, and if that isn't enough, they have a link you can click that has further details.

Unfortunately, I never manual installed drivers in Ubuntu, only in Mint, so I cannot help much on that....

Good luck!
[U]
*notes; if you had resolution problems both before and after driver installation,  try changing from the cord you are using to another. Let's say you had DVI in, try your monitor with VGA and vice-versa.[/U]

---

### Post by prodigy_ on 2013-01-17
> **Lightning Dragon said:**
> I went to my Drivers and activated the recommended driver
Why don't you just d/l the latest driver directly from nVidia website?

---

### Post by Lightning Dragon on 2013-01-17
Hello,

I have tried that method but it refuses to install it. Just doesn't open if I run the .run file and if I go into the CLI, I get kernel problems about Nouveau. I did do it in Mint, but it doesn't seem to work in 12.04--or maybe there is a different way to do it?

---

### Post by prodigy_ on 2013-01-17
> **Lightning Dragon said:**
> if I go into the CLI, I get kernel problems about Nouveau.
Nouveau shouldn't block the proprietary drivers installation. Can you try again and post the exact text of the error message here?

---

### Post by prodigy_ on 2013-01-17
[Del]

---

### Post by Lightning Dragon on 2013-01-17
Hello,

Oh, no, I am allowed to install the proprietary drivers from the Additional Drivers (app?) within Ubuntu without any problems like that, but none of the drivers available there are the correct one for my LE card. Well, there is an experimental 304, but I'm not sure if I should try that one since it gives a warning about it.

---

### Post by ManamiVixen on 2013-01-17
Have you tried installing nvidia-common? It may be missing or broken.

---

### Post by Lightning Dragon on 2013-01-17
Hello,

I have not. Should I install this before or after I attempt to install my driver manually, or through the Additional Drivers?

Thank you,

EDIT;

Trying to install the .deb files for my driver from [here]("http://archive.ubuntu.com/ubuntu/pool/restricted/n/") sends me in a dependency loop, so I guess that option is out of the question.

---

### Post by ManamiVixen on 2013-01-17
nvidia-common is required for proper Nvidia card support. It needs to be installed. 

Also, YOU HAVE TO USE the pre 200's series drivers as the ones after the 200's, only support at the oldest, the 8400 series.

---

### Post by Lightning Dragon on 2013-01-17
Hello,

Then I will install it now. But it wants me to remove the following; *linux-headers-3.2.0-29 linux-headers-3.2.0-29-generic-pae*

That is unfortunate and disappointing. :( So there is no luck to get my graphics card's driver to install? Err.

---

### Post by ManamiVixen on 2013-01-17
All is not lost! I assume you motherboard has AGP, just search online for Nvidia 8400 or newer cards for AGP format.

---

### Post by Lightning Dragon on 2013-01-17
Hello,

I am not sure what AGP is, but I will see if my mobo has it, but my Narra6 is pretty old so I won't hold out hope too much.  Well, since I can't get my card to work for Ubuntu 12.04, I'll go back to Mint (which installs my driver from here) after I mess around some more in here (might be I can find some driver that works for my card). 

But for now, I would still like to fix my resolution problems, if possible, and this pesky "/usr/bin/jockey-text" error I get *constantly*.

---

### Post by ManamiVixen on 2013-01-17
an AGP slot, Accelerated Graphics Port, is a slot designated to graphics cards on a computer motherboard. [IMG]http://tips4pc.com/images/agp_slot.jpg[/IMG]
Pictured there.

The slot tech may be old, but there are still cards for it.

As to the other things you mentioned, Jockey is Ubuntu's driver manger. It's just complaining that there is no driver installed for graphics. The resolution is not fixable due to the fact that by default the resolutions are set to older style monitors as a precaution since Ubuntu cannot detect the actual screen resolution and it cannot be fixed to the correct size. So it chooses resolutions most likely supported by a monitor.

---

### Post by Lightning Dragon on 2013-01-17
Hello,

Yes, I have some slots, one of which has my card already in it. It sucks I would have to buy another card to get it to work in Ubuntu. I plan on building a PC in the next few months, so I would hate having to buy two cards.

EDIT:

Good news and bad news. I followed these instructions and nvidia x settings was installed, and now I have 304.64 driver installed for my card. However, I have still a few problems left; 1) I still get blinking at boot up and for a minute after I sign in, I get white bar code screens when booting into Ubuntu 12.04 2) jockey-text and program installing problems 3) OpenGL support 4) my resolution is still a problem. I am only getting 640x480.

I tried the command once again, but get this error still;

> LightningDragon@LDPC:~$ xrandr -s 1440x900
Size 1440x900 not found in available modes
My monitor does support the size, as I have it in Mint and Windows. I have an HP w1707.

If I could get this problem to leave, then I will only have to deal with the jockey-text problem.

---

### Post by ManamiVixen on 2013-01-17
open nvidia-settings and click "X Server Display Configuration" That lets you set your resolution.

---

### Post by Lightning Dragon on 2013-01-17
> **ManamiVixen said:**
> open nvidia-settings and click "X Server Display Configuration" That lets you set your resolution.

I only have inputs for 640x480 and 800x768 through nvidia's x settings.

---

### Post by ManamiVixen on 2013-01-17
One last attempt... sudo apt-get remove --purge nvidia-current && sudo apt-get autoremove && sudo apt-get install nvidia-current 

Sometimes the linux headers are broken on new installs and breaks kernel modules compiled with DKMS. Removing it, then reinstalling it almost always works. it will automatically reinstall when nvidia-current installs again.

If that dosen't work then you really do need the older than 200 series Nvidia driver. how 304 installed really is a mystery to me seeing as it doesn't support the card. Unfortuantly, even though Linux supports older hardware, Linux is at the mercy of proprietary drivers. If Nvidia so chooses to kill the card, they will.

---

### Post by Lightning Dragon on 2013-01-17
Hello,

I followed this and it worked when manual install wouldn't. I was used to manual installs too, as I had done the same thing in Linux Mint (304.64 for my Geforce SPARKLE 6600 LE), so might be for older cards there is a way, but it isn't shown in the Additional Drivers or whatnot page.

Alright then, I'm doing the commands now (only wants to remove one package). This is what it says;

```

(Reading database ... 196186 files and directories currently installed.)
Removing nvidia-current ...
Removing all DKMS Modules
Done.
update-alternatives: using /usr/lib/i386-linux-gnu/mesa/ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode.
INFO:Disable nvidia-current
DEBUG:Parsing /usr/share/nvidia-common/quirks/lenovo_thinkpad
DEBUG:Parsing /usr/share/nvidia-common/quirks/put_your_quirks_here
DEBUG:Parsing /usr/share/nvidia-common/quirks/dell_latitude
DEBUG:Processing quirk ThinkPad T420s
DEBUG:Failure to match Compaq-Presario with LENOVO
DEBUG:Quirk doesn't match
DEBUG:Processing quirk Latitude E6530
DEBUG:Failure to match Compaq-Presario with Dell Inc.
DEBUG:Quirk doesn't match
update-initramfs: deferring update (trigger activated)
Purging configuration files for nvidia-current ...
update-initramfs: deferring update (trigger activated)
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for man-db ...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.2.0-36-generic-pae
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  dkms linux-headers-3.2.0-29 linux-headers-3.2.0-29-generic-pae
0 upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
After this operation, 67.8 MB disk space will be freed.
Do you want to continue [Y/n]? y

(Reading database ... 196015 files and directories currently installed.)
Removing dkms ...
Removing linux-headers-3.2.0-29-generic-pae ...
Removing linux-headers-3.2.0-29 ...
Processing triggers for man-db ...
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  dkms
The following NEW packages will be installed:
  dkms nvidia-current
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/38.2 MB of archives.
After this operation, 109 MB of additional disk space will be used.
Do you want to continue [Y/n]? 

Selecting previously unselected package nvidia-current.
Unpacking nvidia-current (from .../nvidia-current_304.64-0ubuntu1~precise~xup1_i386.deb) ...
Processing triggers for man-db ...
Setting up dkms (2.2.0.3-1ubuntu3) ...
Setting up nvidia-current (304.64-0ubuntu1~precise~xup1) ...
update-alternatives: using /usr/lib/nvidia-current/ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode.
update-alternatives: warning: skip creation of /usr/lib32/libOpenCL.so because associated file /usr/lib32/nvidia-current/libOpenCL.so (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/lib32/vdpau/libvdpau_nvidia.so.1 because associated file /usr/lib32/nvidia-current/vdpau/libvdpau_nvidia.so.1 (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/lib32/libvdpau_nvidia.so because associated file /usr/lib32/nvidia-current/vdpau/libvdpau_nvidia.so (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: using /usr/lib/nvidia-current/alt_ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode.
update-initramfs: deferring update (trigger activated)
INFO:Enable nvidia-current
DEBUG:Parsing /usr/share/nvidia-common/quirks/lenovo_thinkpad
DEBUG:Parsing /usr/share/nvidia-common/quirks/put_your_quirks_here
DEBUG:Parsing /usr/share/nvidia-common/quirks/dell_latitude
DEBUG:Processing quirk ThinkPad T420s
DEBUG:Failure to match Compaq-Presario with LENOVO
DEBUG:Quirk doesn't match
DEBUG:Processing quirk Latitude E6530
DEBUG:Failure to match Compaq-Presario with Dell Inc.
DEBUG:Quirk doesn't match
Loading new nvidia-current-304.64 DKMS files...
First Installation: checking all kernels...
Building only for 3.2.0-36-generic-pae
Building for architecture i686
Building initial module for 3.2.0-36-generic-pae
Done.

nvidia_current:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.2.0-36-generic-pae/updates/dkms/

depmod....

DKMS: install completed.
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.2.0-36-generic-pae
done


```Hopefully this fixes my resolution, white/black boot screens and everything else.

---

### Post by ManamiVixen on 2013-01-17
So, it worked then? :)

---

### Post by Lightning Dragon on 2013-01-17
I hoped it would, but it didn't. Just in case I restarted the computer. I still get the white bar code screen, the black blinking and still no other monitor size supports in either native Linux Displays, or the nvidia x settings. ):

---

### Post by ManamiVixen on 2013-01-17
I'm sorry then... This is out of my league. I did my best though to help. Hopefully someone else will come by with the answer. Sorry... Best hopes to you.

---

### Post by Lightning Dragon on 2013-01-17
Hello,

That is fine. (: I thank you for the help you have provided for me, though. And here is hoping someone can fix this for me, because three fresh installs have done nothing.

Should I try to change the xorg.conf?

EDIT:

I tried this, but it ignores my commands. 

[http://www.vxbus.com/software/linux/148-how-to-change-monitor-resolution-in-ubuntu-1204.html](http://www.vxbus.com/software/linux/148-how-to-change-monitor-resolution-in-ubuntu-1204.html)

Please, if anyone has anything to try, I'll try it....

**EDIT 2:**

                                  So, the only way to fix the problem with Geforce SPARKLE 6600 LE cards is...not to use VGA cords. The system refuses to acknowledge VGA cords, but does fine with DVI. The problem is that I **want** to use VGA cords for a setup I have. See, my PC monitor is also a gaming monitor and I have DVI set up for my gaming consoles because that's the only set up the consoles take, but I can't do both. If anyone could tell me how to fix this I would greatly appreciate it.

For now, I fixed it another way, too, if anyone else should happen upon this thread with the same issue, but it will require an adapter or a DVI cable. The adapter turns the VGA to DVI, which I plugged into my GPU. It seems VGA cords cannot be used with 304.64 driver on a Geforce SPARKLE 6600 LE card within Ubuntu 12.04, but it does work in Linux Mint and probably in other distros. *I also edited the main post with how I installed 304.64 drivers in case another person like me needs it on a 32bit system!*

Here is a link to an adapter I am now using since my VGA port is worthless in Ubuntu; [http://www.amazon.com/StarTech-DVI-Cable-Adapter-DVIVGAMF/dp/B000067SOH/ref=sr_1_1?ie=UTF8&qid=1358473098&sr=8-1&keywords=VGA+to+DVI+adapter](http://www.amazon.com/StarTech-DVI-Cable-Adapter-DVIVGAMF/dp/B000067SOH/ref=sr_1_1?ie=UTF8&qid=1358473098&sr=8-1&keywords=VGA+to+DVI+adapter)

I guess this is good enough for me. I'll see if this set up/fix destroys my Mint resolution next. 

For now, I would like to take care of the black blinking and white bar code boot screens I get. I have no idea how to look it up to fix it, though, so if anyone knows this problem and how to fix it, please&#8212;please&#8212;share. I also need help getting OpenGL support in Ubuntu (even Mint [laughs]).

Thanks!

---

### Post by Lightning Dragon on 2013-01-18
Hello,

I rebooted into the computer this morning and found it unresponsive in the white screens I have been getting after nvidia installations, so I had to reinstall fresh....again. Resolution is no longer a problem (if I ever switch to VGA it will be though), but now I need to figure out a way to properly install nvidia drivers for my card without having it break literally everything. How can I tell if the Additional Driver list of nvidia drives is the correct one for me? Or how do I even find the correct driver for my card? I tried [GeForce's detection,]("http://www.geforce.com/drivers") but it doesn't work in Mozilla and that's all I have in Ubuntu... 

I took a picture of the white screens, too.

[http://postimage.org/image/jzadj66sz/](http://postimage.org/image/jzadj66sz/)

(try to clean the screen to remove more of the glare...)

Please, any help is appreciated. 

Thank you!

---

### Post by ManamiVixen on 2013-01-18
Alright, I did a little research and found that X.Org has since abandoned support for Nvidia drivers older than the 200 series. Your card requires 173.xx. 

BUT in a little twist, there DOES exist a package that supports your card and new xorg. Give it a go.

[https://launchpad.net/ubuntu/+source/nvidia-graphics-drivers-173-updates/173.14.35-0ubuntu1/+build/3597638](https://launchpad.net/ubuntu/+source/nvidia-graphics-drivers-173-updates/173.14.35-0ubuntu1/+build/3597638)

Only works on 32bit installs.

---

### Post by Lightning Dragon on 2013-01-18
Hello,

Thank you so much for researching into this to help me with my problems. I appreciate it very much. O:)

I just did an attempt install of 173.14.36-pkg1.run file and it resulted in giving me white screens and making it so I cannot use CLI (same kind of white screen problems), so I might either do another fresh install or figure out how to remove what I just did.  

And then I will download the package you linked to and luckily I am 32bit!  If I may ask it, the link you gave me has a lot of links, which would I download and how would I install?

Thank you! ):P

---

### Post by ManamiVixen on 2013-01-18
[https://launchpad.net/ubuntu/+source/nvidia-graphics-drivers-173-updates/173.14.35-0ubuntu1/+build/3597638/+files/nvidia-173-updates_173.14.35-0ubuntu1_i386.deb](https://launchpad.net/ubuntu/+source/nvidia-graphics-drivers-173-updates/173.14.35-0ubuntu1/+build/3597638/+files/nvidia-173-updates_173.14.35-0ubuntu1_i386.deb)

Save it, and click on it to install. That should do.

---

### Post by Lightning Dragon on 2013-01-18
Hello,

Alright, I installed it through the Software Center (as it opened when I double clicked the deb file) and was prompted to reboot. There are still the white screens, and now I get a message saying "crash report daemon is running [OK]" on a purple screen with the Ubuntu 12.04 logo to the top left, but it boots into Ubuntu fine after ward.  

Also, the CLI (CTRL+ALT+F1) is all white and I am unable to do anything with it. There is also this now; 

[http://postimage.org/image/pk42uk6kt/](http://postimage.org/image/pk42uk6kt/)

NVIDIA X Server Settings is there, but when I click it it does not open up.

EDIT:

Another reboot gave me this when I attempted to log into the main account;

> Could not update ICEauthority file /home/LD/.ICEauthorityOnly guest accounts work now. Looks like I'm in for another re-install...

EDIT:

Is there at **least** a way to make it so Linux/Ubuntu using the board instead of the external GPU while it is plugged in? This would save me from hooking and unhooking my GPU whenever I switch back to another OS.

---

### Post by Lightning Dragon on 2013-01-21
Hello,

I guess this is another bump for very desperate help. If I could just have a way to at least have Ubuntu boot up with on board even with the GPU in, that would be better than nothing...

Thanks,

EDIT:

I did another fresh install, this time with 64bit version because reading some sites said AMD processors would work best in Ubuntu with 64bit and Nvidia. Once I had it installed, I went to "Additional Drivers" and selected the 304 experimental driver.

However, I can't seem to find where the settings are. Any help?

EDIT:

Found them. Took several reboots for the settings to appear. But after taking the GPU out, the computer boots in fine using on board GPU  with NVIDIA GeForce 6150SE nForce 430, which seems to be supported by  the same driver. So I guess it is the driver for the card or the lack of  full support for this one card, or something. For now, the following  distros have the exact problem; *Ubuntu, Kubuntu, Linux Mint, Manjaro, Edbuntu, Xubuntu, and Fedora*.  Except in Manjora the installation pre-installed the exact driver I  needed, so that was very helpful for my board GPU, however, can't use my  external GPU so I can't perform any high applications or play videos  above 300p.

This is disappointing, but I am glad it appears not to be a problem with  the distros itself. At least that's how it seems. Any help, or ideas? I read something about nomodeset being needed with NVIDIA, but I have no idea what that is. I am DYING to fix this problem. :(

---

### Post by Lightning Dragon on 2013-01-25
Bump! And with updates!

So I got into the BIOS and set it to my GPU slot. Now I can boot past the Ubuntu logo screen, which is superb news. However, I am greeted by new problems that hopefully can be resolved. I have tried everything on the Internet concerning this issue, but maybe I was just not looking for the right solution. 

**_Here is what goes on;_**

I am brought into Command Line Interface. So I tried to restart lightdm.

sudo service lightdm restart

The  screen blackened out and reappeared, asking me to update 33 packages despite me updating right before I turned the computer off (so that's weird),  which I did, and then it rebooted and came back with a screen of the  following commands;

[http://pastebin.com/2Ut9tC5Q](http://pastebin.com/2Ut9tC5Q)
(where the "----" is means the screen cut off so I could not see the rest of it)

All  of them reported "[OK]" to the far right except the ones that actually said  "failed/stopped" before it reboot again and gave me the following TTY1  command line;

plymouthd: ./plugin.c: 540: map_to_device: Assertion 'head->size > o' failed
mountall: DIsconnected from Plymouth
Checking battery state... (on a desktop, though)

So I turned it off, took out the GPU again and booted back in. Hopefully someone can offer me some assistance, I am desperate! 

Thank you all!

EDIT 2:

Nevermind, booting up with a GPU in now takes me to a black screen past the Ubuntu logo screen with no text. It acts as if my keyboard is off, so I cannot type anything. However, turning the system off my a button on the computer gives me text that says it is terminating all processes and separately mentions terminating ALSA.

Also, it appears kvm has been disabled. I'm not sure what that is, but I get that on boot after installing nvidia drivers. Running the code "grep svm /proc/cpuinfo" brings me this;

> 
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt hw_pstate npt lbrv svm_lock nrip_save
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt hw_pstate npt lbrv svm_lock nrip_save

So, issue still here.

---

### Post by Lightning Dragon on 2013-05-07
Hi,

I realize this is pretty old but hopefully it isn't too old enough for me to seek help again. I am still having install problems all over the place. I have been using the install in its broken condition because no matter what I did I could not fix the install. However, let me get some things out of the way that are no longer a problem; It was definitely my GPU. I now have a Geforce 8600 GT and I can see and use the Ubuntu drivers for it (in which I'm not ever going to use official drivers), however, fresh installs of Ubuntu still results in issues. 

A lot of the icons and images for my system are broken or gone even though it was a fresh install. At first I thought it was because I needed to update, upgrade and reboot, but that didn't work. Here is an example of what I mean;

[[IMG]http://s22.postimg.org/b8ghd2yj1/Screenshot_from_2013_05_07_22_50_49.png[/IMG]]("http://postimg.org/image/b8ghd2yj1/")

[[IMG]http://s22.postimg.org/q1v4xu6a5/Screenshot_from_2013_05_07_23_19_17.png[/IMG]]("http://postimg.org/image/q1v4xu6a5/")

[[IMG]http://s22.postimg.org/r5f99sqx9/Screenshot_from_2013_05_07_23_24_52.png[/IMG]]("http://postimg.org/image/r5f99sqx9/")

Those are just a few and some of all that I can find. Also, a lot of the time if I log in the desktop is broken and everything is frozen. The same thing happens in Ubuntu 2D, only onnce I select it and log in the screen turns gray for about ten seconds and then loads into a completely screwed up desktop. The only way to get out of this is to power-down the hard way.

What could be causing this even on a fresh install? Is there something I can do to fix this? I really want to use Ubuntu 12.04 again.

Thanks!

---

### Post by oldfred on 2013-05-07
Since you changed cards, did you totally uninstall the old nVidia driver and then  install the new one. Sometimes their can be left overs that cause issues.

I have a 9600GT and just install the nVidia driver offered in system settings, Software & updates, add'l Drivers tab.

       # only reason to purge is there are several versions, if you know you have different nVidia use that:
#To see available versions:
dpkg -l | grep -i nvidia*
apt-cache search nvidia-sett*
# Houseclean out all old versions to avoid issues
sudo apt-get remove --purge < nvidiadriverpackagename>
# [ using the correct names] for each driver, before running:
sudo apt-get purge nvidia*


 # Install version you prefer
# I used nvidia-current-updates & nvidia-settings-updates, example below is just nvidia-current
sudo apt-get install nvidia-current
sudo apt-get install nvidia-settings
sudo dpkg-reconfigure nvidia-current
sudo nvidia-xconfig
sudo reboot
May want nvidia-current, nvidia-current-updates or nvidia-current-experimental-XXX for most recent testing version.
apt-cache search nvidia-sett* 

      
 Re: How To Install Nvidia Drivers [v8.1.2.12 by Bogan]. post 1126
[http://ubuntuforums.org/showthread.php?t=1743535&page=113](http://ubuntuforums.org/showthread.php?t=1743535&page=113)
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)
[http://ubuntuforums.org/showthread.php?t=2081649](http://ubuntuforums.org/showthread.php?t=2081649)

---

### Post by Lightning Dragon on 2013-05-07
Hi oldfred and thanks for looking at my thread, I appreciate it. :)

Yes, that was the first thing I did try on my last install. However, it was not working so I did a fresh install of Ubuntu and installed the recommended driver in "Additional Drivers" through the Dash Home. The sudo command gives out the following, which I assume to be correct for my card;

[IMG]http://s16.postimg.org/xcctmu539/Screenshot_from_2013_05_07_23_54_00.png[/IMG]

The GPU seems to be working fine now though only because I decided on using drivers from Additional Drivers, it is just all these random errors popping up and the missing images that seems to persist even over fresh installs like Metacity and Compiz crashing _constantly_. I tried different desktop environments like Cinnamon, GNOME and 2D, but images are always missing. I have been wracking my head over these issues for weeks, can't seem to get it fixed, but hopefully the solution will be found soon. 

Thanks!

EDIT;

Here is another example of broken/missing images. It is the red circle with the "\" through it in the box;

[IMG]http://s12.postimg.org/65uxip16l/Screenshot_from_2013_05_08_00_16_01.png[/IMG]

Should I download 12.04 LTS again and try to install with that and see if the issue is gone?

EDIT2:

Aha! I fixed _one_ of my problems! The image issue...sadly it needed a reinstall, but _**not**_ from the same disc. I only had a 16GB USB Toshiba left so I used [LinuxLive USB Creator]("http://www.linuxliveusb.com/"), had it download Ubuntu 12.04 LTS *automatically* and then set it so it was live mode (_**no**_ persistence), and then booted by pressing ESC key--Using a stupid compaq which doesn't have a set boot priority for USBs--and then selected my USB.

I also noticed that my disc, which was burned pretty recently, was labeled 12.04.1 and the new download was 12.04.2. Also,  before I reinstalled and is why I did the reinstall, my update manager told me *Precise* was _no longer supported_. I have no idea if this was just a bug, but it made me do the steps.

Now I just need to install drivers for my Geforce 8600 GT 1GB and I'm golden. Gotta figure out how to properly find my driver, first, though. #-o

---

### Post by oldfred on 2013-05-08
There are now actually two versions of 12.04 or two different kernels. The original 12.04 keeps its original kernel. But for very long term like 5 years, I think they realized hardware will change a lot and the kernel will need more than just backports of security fixes. New kernels support a lot of the new hardware.

       Release notes 12.04.2 Feb 2013
[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop#PrecisePangolin.2BAC8-ReleaseNotes.2BAC8-CommonInfrastructure-1.Kernel](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop#PrecisePangolin.2BAC8-ReleaseNotes.2BAC8-CommonInfrastructure-1.Kernel)
LTS Enablement Stack 12.04.2
[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop#LTS_Hardware_Enablement_Stack](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop#LTS_Hardware_Enablement_Stack)
12.04 to 12.04.2 new kernel
sudo apt-get install linux-generic-lts-quantal xserver-xorg-lts-quantal
[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

---

### Post by Lightning Dragon on 2013-05-08
Hi,

> **oldfred said:**
> There are now actually two versions of 12.04 or two different kernels. The original 12.04 keeps its original kernel. But for very long term like 5 years, I think they realized hardware will change a lot and the kernel will need more than just backports of security fixes. New kernels support a lot of the new hardware.

       Release notes 12.04.2 Feb 2013
[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop#PrecisePangolin.2BAC8-ReleaseNotes.2BAC8-CommonInfrastructure-1.Kernel](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop#PrecisePangolin.2BAC8-ReleaseNotes.2BAC8-CommonInfrastructure-1.Kernel)
LTS Enablement Stack 12.04.2
[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop#LTS_Hardware_Enablement_Stack](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop#LTS_Hardware_Enablement_Stack)
12.04 to 12.04.2 new kernel
sudo apt-get install linux-generic-lts-quantal xserver-xorg-lts-quantal
[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

Oh, I understand now. I thought somehow something was wrong with my burned disc! I have another Ubuntu 12.04.1 drive waiting to be fixed, so I will test this out on it. However, the instructions say to install <release> and I'm assuming you change "<release>" to the release you need? Or, for me, would I just install the Quantal hardware enablement *your sudo command and their sudo command*?

Thanks!

---

### Post by oldfred on 2013-05-08
I have not converted my 12.04 to the newer kernel. I used to update every 6 months, but my wife complained about too many changes, so now I am staying with 12.04 as my main working system, probably until 14.04. 
But I have also installed all the newer ones just to see what changes they have made.

---

### Post by Lightning Dragon on 2013-05-08
Hi,

I understand. I will try to run the Quantal sudo command on another drive and see if that updates my kernel and hopefully allows me to install my nvidia drivers without problems.

---

