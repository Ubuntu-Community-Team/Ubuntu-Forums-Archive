---
title: "'Normal' DM operation only after uninstall/reinstalling DM"
date: 2023-03-31
forum: General Help
---

### Post by lincoln7711 on 2023-03-31
Hi All:

Bit of situation with this laptop that's been an ongoing thing.  HP ProBook 445R G6.  Typically does not boot when entering into Ubuntu 22.04.2 LTS.  This also occurred on 20.04 LTS.  The basics are: 
1) Boot laptop
2) Select Ubuntu from GRUB (no other OS - this is NOT dual booted) 
3) Quick flash of some code
4) Black screen that never does anything.  

What I know: 
-Safe graphics works.  
-Booting to recovery, uninstalling and reinstalling GDM3 typically works for next boot, then back to issue on subsequent reboots
-Changing from current DM to any other DM seems to resolve issue - I often just move between lightDM and GDM3.  
-Adding an external monitor has no effect.  When booting to black screen, nothing appears on the external display either - it seems to not display anything.  This is via integrated HDMI
-The 'working' resolution is set to 1920x1080 60.02Hz Scale 100%

What I've tried: 
-The 'nomodset' tricks.  I've done this by dropping into the 'E menu' via GRUB and by editing /etc/default/grub
-toggling fractional scaling
-enabling proprietary drives
-updating
-reinstalling OS from clean download

Incidentally, I have upgraded the SSD and the memory, this issue was present prior and persists after.  

I'm at a loss here.  Any help would be appreciated.  Happy to provide readouts, just need to know what's of value.  DMs and graphics stuff is a bit out of my wheelhouse.

---

### Post by MAFoElffen on 2023-03-31
If, when you are at a "Black Screen" where it seems to be hung, can you concurrently press the <Cntrl><Alt><F4> keys and toggle to vtty4 virtual console session?

If not, then at the Grub2 menu, try adding
```

nomodeset

```
You had that misspelled above. Just making sure.

If that doesn't work, then same, except remove "quiet splash" and replace with "-- --verbose debug drm.debug=0xe 3". That should put it into a verbose debug messaging mode during the boot, and boot to run level 3, which is console only, without graphics...

Then run the UbuntuForums 'system-info' Script, installed from the [PPA]("https://launchpad.net/~mafoelffen/+archive/ubuntu/system-info") or downloaded from the [Forum's GitHub]("https://github.com/UbuntuForums/system-info"). Please post the URL of the Pastebin the report uploads to. That way we can see what hardware and system config we are looking at, to be able to recommend a solution for.

---

### Post by lincoln7711 on 2023-03-31
Here's the system info: [https://paste.ubuntu.com/p/9CMtpDxhG5/](https://paste.ubuntu.com/p/9CMtpDxhG5/)

So, I did typo, but correcting that doesn't produce the desired result.  It will boot into 1024x768, 4:3 aspect, which is not the desired 1920x1080 16:9 that I get with a 'normal' boot.  

The removal of the "quiet splash" and replacement with "-- --verbose debug drm.debug=0xe 3" hangs (attached).  I pulled system info by booting to safe graphics.

[https://ubuntuforums.org/attachment.php?attachmentid=291996&stc=1](https://ubuntuforums.org/attachment.php?attachmentid=291996&stc=1)

---

### Post by MAFoElffen on 2023-04-01
I see that you are installed with ZFS encrypted volumes. That you have Picasso/Raven 2 [Radeon Vega Series / Radeon Vega Mobile Series] graphics, but that it says it is unclaimed with no driver loaded.

First, lets look at your logs to see if a driver does try to load, and if the kernel modules are loaded... and that other files are present...
```

sudo lsmod | grep -i 'amd'
sudo dmesg | grep 'iommu\|amdgpu'
ls /lib/firmware/amdgpu/ | grep -i 'picasso\|raven'

```
Next try these boot parameters to setup the correct driver being loaded (take out 'nomodeset' and try these)
```

amdgpu.cik_support=1 amdgpu.si_support=1 radeon.si_support=0 radeon.cik_support=0

```
Post the output within code tags... Tell me how that goes.

---

### Post by lincoln7711 on 2023-04-01
Yep.  FWIW, this was happening before I reimaged, and there was no encryption on that setup.  

Output of logs: 
[ATTACH]292002[/ATTACH]

I placed the boot parameters in GRUB, no avail.  It pretty much acts like it does without those parameters - I get a few lines of output as things are loaded, but then black screen.  I added these at the GRUB menu by dropping to edit, that's correct?  I don't need to add these to /etc/default/grub?

---

### Post by MAFoElffen on 2023-04-02
It is not loading the amdgpu kernel modules at all. Does not even try to load a graphics driver.

Hmmm.

```

sudo nano /etc/default/grub

```
Edit this line
```

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash amdgpu.cik_support=1 amdgpu.si_support=1 radeon.si_support=0 radeon.cik_support=0"

```
Save and exit
```

sudo update-grub

```
Then 
```

sudo nano /usr/share/X11/xorg.conf.d/10-amdgpu.conf

```
Add the end to what exists
```

[Section "OutputClass"
    Identifier "AMDgpu"
    MatchDriver "amdgpu"
    Driver "amdgpu"
EndSection  

[COLOR=#ff0000]Section "Device"
    Identifier "Card0"
    Driver "amdgpu"
    Option "TearFree" "on"
    Option "DRI3" "1" 
    BusID "PCI:5:0:0"
EndSection
[/COLOR]
```
Save and exit.
```

sudo nano /etc/modprobe.d/amdgpu.conf

```
Edits:
```

options amdgpu si_support=1
options amdgpu cik_support=1

```
Then 
```

sudo nano /etc/modprobe.d/radeon.conf

```
Edits:
```

options radeon si_support=0
options radeon cik_support=0

```
Save and exit. Update images
```

sudo update-initramfs -c -k all

```
Then install vulcan-tools
```

sudo apt update
sudo apt install vulcan-tools

```
Add repo for current mesa
```

sudo apt-add-repo ppa:kisak/kisak-mesa
sudo apt update
sudo apt install mesa

```
Reboot and test. You are using X11. That should explicitly tell it to use the amdgpu driver for that GPU.

---

### Post by lincoln7711 on 2023-04-05
Reboot produces same issue.  The only issue I had with the above is with the kisak-mesa install. The PPA adds fine, but apt reports unable to locate package mesa.

---

### Post by MAFoElffen on 2023-04-06
> **lincoln7711 said:**
> Reboot produces same issue.  The only issue I had with the above is with the kisak-mesa install. The PPA adds fine, but apt reports unable to locate package mesa.
RE: [https://launchpad.net/~kisak/+archive/ubuntu/kisak-mesa/+packages](https://launchpad.net/~kisak/+archive/ubuntu/kisak-mesa/+packages)

I see 'mesa' packages there built for Bionic, Focal, jammy and Kenetic. If you have tha PPA added in the sources, then it should be there

What does this show?
```

apt list mesa

```

---

### Post by lincoln7711 on 2023-04-06
>  I see 'mesa' packages there built for Bionic, Focal, jammy and Kenetic.  If you have tha PPA added in the sources, then it should be there

What does this show?

```
Listing... Done

```

I also tried to trigger a reinstall via apt, but it errors with Unable to locate package.

---

### Post by MAFoElffen on 2023-04-06
How about we dump a list of what packages it does see in that PPA.
```

ls /var/lib/apt/lists/ppa.launchpad*kisak*Packages
echo ""
awk '$1 == "Package:" { print $2 }' /var/lib/apt/lists/ppa.launchpad*kisak*Packages

```

---

### Post by lincoln7711 on 2023-04-06
[ATTACH]292047[/ATTACH]

My untrained eye sees Mesa packages in the output *shrugs*

---

### Post by MAFoElffen on 2023-04-06
Yes, but... Look at this:
```

mesa-common-dev
mesa-drm-shim
mesa-opencl-icd
mesa-va-drivers
mesa-vdpau-drivers
mesa-vulkan-drivers

```
There is no " mesa " package, that is the main package anymore. They are all "mesa-<something>" packages. So there is no longer a 'mesa' package that installs everything it needs as dependencies.

When I get home from work tonight, I will email the PPA maintainer to see what new changes were made, and what needs to be done (currently) to do what we used to do in the past.

---

### Post by MAFoElffen on 2023-04-07
I forgot a few steps and how that works... It installs the other mesa packages from that.
```

sudo apt update
sudo apt full-upgrade
sudo apt list xserver-xorg-video-amdcpu --installed
glxinfo | grep "OpenGL version"

```

---

