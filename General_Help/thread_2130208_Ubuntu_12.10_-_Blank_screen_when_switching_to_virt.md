---
title: "Ubuntu 12.10 - Blank screen when switching to virtual terminals"
date: 2013-03-28
forum: General Help
---

### Post by Drone4four on 2013-03-28
When using Ctrl+Alt+F1-6 to go to the virtual terminals, I experience a blank screen. 

I fiddled around with some variables and settings in /etc/default/grub.  After modifying each parameter I entered sudo update-grub.  Unfortunatley, everything I have tried has failed to fix the problem with my virtual terminals.

Here is what I have tried in search of a solution.  

For starters I removed the comment to activate GRUB_TERMINAL=console.  I also added the ‘text’ parameter to the ‘GRUB_CMDLINE_LINUX_DEFAULT’ field as per the recommendation by izx [here]("http://askubuntu.com/questions/147618/how-do-i-get-ctrlaltf-virtual-terminals-to-work-in-ubuntu-12-04?rq=1").  When I rebooted, instead of loading ldm, it gave me a CLI login.  I logged in, like the good ol’ days on Slackware 9 when I was first introduced to *nix.  I entered xwmconfig, but no dice.  I entered startx to see what would happen and all I saw was my stupid wallpaper.  There was no way to load an app b/c Alt+F2 did nothing.  There was no top bar (I run gnome 3) and therefore no way to log out.  Switching back to tty1 also was impossible Ctrl+Alt+F1 through F6 did nothing.  I had no option but to do a cold reboot. 

I added "vga=normal" to my ‘GRUB_CMDLINE_LINUX_DEFAULT’ next to "quiet splash" as per neon_overload’s post [here]("http://askubuntu.com/questions/150610/why-are-virtual-terminal-blank-using-nvidia-propietary-drivers").  

I also tried changing the vga variable from normal to 791 which also didn’t allow me to switch virtual terminals.

EDIT: One more thing, there is no ~/.config/monitors.xml for me to change the parameters for the resolution which was the case for the other posters.

Here is my /etc/default/grub

```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash vga=normal"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

```

Here is lsmod and lspci
```

gnull@quantal ~ $ lsmod
Module                  Size  Used by
snd_hda_codec_hdmi     32007  4 
pci_stub               12622  1 
vboxpci                23157  0 
vboxnetadp             25670  0 
vboxnetflt             23442  0 
vboxdrv               287189  3 vboxpci,vboxnetadp,vboxnetflt
coretemp               13400  0 
kvm_intel             132759  0 
kvm                   414070  1 kvm_intel
hid_generic            12493  0 
gpio_ich               13383  0 
snd_hda_codec_realtek    77876  1 
usbhid                 46947  0 
hid                   100366  2 hid_generic,usbhid
snd_usb_audio         130279  2 
snd_usbmidi_lib        24953  1 snd_usb_audio
snd_hda_intel          33491  6 
snd_hda_codec         134212  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13602  2 snd_usb_audio,snd_hda_codec
snd_pcm                96580  5 snd_hda_codec_hdmi,snd_usb_audio,snd_hda_intel,snd_hda_codec
psmouse                95552  0 
microcode              22803  0 
snd_seq_midi           13324  0 
snd_rawmidi            30512  2 snd_usbmidi_lib,snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61521  2 snd_seq_midi,snd_seq_midi_event
serio_raw              13215  0 
bnep                   18140  2 
rfcomm                 46619  0 
bluetooth             209199  10 bnep,rfcomm
parport_pc             32688  1 
ppdev                  17073  0 
snd_timer              29425  2 snd_pcm,snd_seq
snd_seq_device         14497  3 snd_seq_midi,snd_rawmidi,snd_seq
nvidia              11300875  40 
binfmt_misc            17500  1 
mac_hid                13205  0 
snd                    78734  27 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_usb_audio,snd_usbmidi_lib,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
lpc_ich                17061  0 
soundcore              15047  1 snd
snd_page_alloc         18484  2 snd_hda_intel,snd_pcm
lp                     17759  0 
parport                46345  3 parport_pc,ppdev,lp
e1000                 114778  0 
pata_jmicron           12747  0 
r8169                  61650  0 
usb_storage            48838  1 
gnull@quantal ~ $ lspci
00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 4 Series Chipset PCI Express Root Port (rev 03)
00:1a.0 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4
00:1a.1 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5
00:1a.2 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6
00:1a.7 USB controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
00:1c.0 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 1
00:1c.4 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 5
00:1c.5 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 6
00:1d.0 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1
00:1d.1 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2
00:1d.2 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3
00:1d.7 USB controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 90)
00:1f.0 ISA bridge: Intel Corporation 82801JIB (ICH10) LPC Interface Controller
00:1f.2 IDE interface: Intel Corporation 82801JI (ICH10 Family) 4 port SATA IDE Controller #1
00:1f.3 SMBus: Intel Corporation 82801JI (ICH10 Family) SMBus Controller
00:1f.5 IDE interface: Intel Corporation 82801JI (ICH10 Family) 2 port SATA IDE Controller #2
01:00.0 VGA compatible controller: NVIDIA Corporation GF114 [GeForce GTX 560 Ti] (rev a1)
01:00.1 Audio device: NVIDIA Corporation GF114 HDMI Audio Controller (rev a1)
03:00.0 IDE interface: JMicron Technology Corp. JMB368 IDE controller
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
05:03.0 Ethernet controller: Intel Corporation 82541PI Gigabit Ethernet Controller (rev 05)
gnull@quantal ~ $ 

```
Here is my xorg.conf:
```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 304.64  (buildmeister@swio-display-x86-rhel47-12)  Tue Oct 30 12:04:46 PDT 2012


Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       30.0 - 81.0
    VertRefresh     50.0 - 63.0
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```
I don’t know how relevant my xorg.conf is b/c  I thought I read somewhere that when using nvidia’s proprietary drivers it doesn't employ the xorg.conf to store its settings.  If this is true, then where does X11 store all of its configuration settings.

---

### Post by bogan on 2013-03-29
Hi!, **Drone4four**,

I have had similar problems on occasions, usually following a kernal update, but never found the exact cause.

I overcame it by reinstalling the nvidia driver - that is with a GT 520 card - by booting to what you call a CLI log-in prompt, making sure the xserver is shut down with: ' sudo service lightdm stop', and running nvida-installer or 'sudo sh NVIDIA-Linux-x86-304.51.run --dkms'.[ Of course the later assumes you already have the driver downloaded or installed, otherwise use: ```
sudo apt-get remove --purge nvidia-current # change packagename if needed, to remove the existing driver
sudo apt-get install nvidia-current # after:
```

In addition you would need to ensure first that build-essential, linux-headers-generic & linux-headers-'uname -r' are all installed if this problem started after a kernal update or upgrade.

If you need further advice, please Post: ```
lspci -nnk | grep -iA3 vga
/usr/lib/nux/unity_support_test -p # this will only work if your Xserver is running
```Chao!, **bogan.**

---

### Post by Drone4four on 2013-03-29
I removed and reinstalled nvidia-current as per your recommendation.  I rebooted yet the problem persisted.  

I then upgraded my kernel from the stock one that came with 12.10.  I had been putting off this update b/c I assumed it would break my nvidia kernel module.  Over the past few months I didn't want to take that risk b/c everything was working perfectly.  So today I finally upgraded with, sudo aptitude safe-upgrade.  I reinstalled nvidia-current.  Still no virtual terminals.

I then purged my system of nvidia-current one last time.  I then tried installing nvidia-experimental and presto!  I have my virtual terminals again.  

So thanks bogan for your insight, bogan. My problem is solved.

---

