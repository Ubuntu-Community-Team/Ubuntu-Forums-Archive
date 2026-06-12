---
title: "Missing settings for touchpad"
date: 2017-12-15
forum: General Help
---

### Post by ray42 on 2017-12-15
Ubuntu Gnome 16.04.4 LTS
Fresh install as of 25th March 2018

I hate touchpads, I always disable. But the option is not there, see picture.

[ATTACH=CONFIG]277850[/ATTACH]

It always used to be there on the several installs i have done before.

---

### Post by ray42 on 2018-03-26
bump

---

### Post by mörgæs on 2018-03-26
Which hardware are you using?

---

### Post by ray42 on 2018-03-26
Is this enough?

================

 description: Notebook
    product: E6227 (0)
    vendor: Medion
    version: 1.0

H/W path                   Device      Class          Description
=================================================================
                                       system         E6227 (0)
/0                                     bus            E6227
/0/0                                   memory         64KiB BIOS
/0/29                                  memory         512KiB L2 cache
/0/2a                                  memory         128KiB L1 cache
/0/2b                                  memory         3MiB L3 cache
/0/2c                                  memory         4GiB System Memory
/0/2c/0                                memory         4GiB SODIMM DDR3 Synchrono
/0/2d                                  processor      Intel(R) Core(TM) i3-2350M
/0/100                                 bridge         2nd Generation Core Proces
/0/100/2                               display        2nd Generation Core Proces
/0/100/14                              bus            7 Series/C210 Series Chips
/0/100/14/0                usb3        bus            xHCI Host Controller
/0/100/14/0/2                          input          Microsoft 5-Button Mouse w
/0/100/14/0/3              scsi6       storage        Cruzer Fit
/0/100/14/0/3/0.0.0        /dev/sdb    disk           16GB Cruzer Fit
/0/100/14/0/3/0.0.0/0      /dev/sdb    disk           16GB 
/0/100/14/0/3/0.0.0/0/1    /dev/sdb1   volume         11GiB EXT4 volume
/0/100/14/0/3/0.0.0/0/2    /dev/sdb2   volume         3989MiB Extended partition
/0/100/14/0/3/0.0.0/0/2/5  /dev/sdb5   volume         3989MiB Linux swap / Solar
/0/100/14/1                usb4        bus            xHCI Host Controller
/0/100/16                              communication  7 Series/C210 Series Chips
/0/100/1a                              bus            7 Series/C210 Series Chips
/0/100/1a/1                usb1        bus            EHCI Host Controller
/0/100/1a/1/1                          bus            Integrated Rate Matching H
/0/100/1a/1/1/1                        multimedia     Chicony USB 2.0 Camera
/0/100/1b                              multimedia     7 Series/C210 Series Chips
/0/100/1c                              bridge         7 Series/C210 Series Chips
/0/100/1c.1                            bridge         7 Series/C210 Series Chips
/0/100/1c.1/0              wlp2s0      network        Centrino Wireless-N 2230
/0/100/1c.2                            bridge         7 Series/C210 Series Chips
/0/100/1c.2/0              enp3s0      network        RTL8111/8168/8411 PCI Expr
/0/100/1d                              bus            7 Series/C210 Series Chips
/0/100/1d/1                usb2        bus            EHCI Host Controller
/0/100/1d/1/1                          bus            Integrated Rate Matching H
/0/100/1f                              bridge         HM76 Express Chipset LPC C
/0/100/1f.2                            storage        7 Series Chipset Family 6-
/0/100/1f.3                            bus            7 Series/C210 Series Chips

---

### Post by mörgæs on 2018-03-31
Here is an option:
[https://askubuntu.com/questions/65951/how-to-disable-the-touchpad?answertab=votes#tab-top](https://askubuntu.com/questions/65951/how-to-disable-the-touchpad?answertab=votes#tab-top)

---

### Post by ray42 on 2018-03-31
[ATTACH=CONFIG]279140[/ATTACH]

Oh yes I can do that, but see image.  I assume everyone else can see the above.  I used to be able to see this in settings.

I can also use an extension, which is what I'm doing currently. 

But why has this option disappeared from a fresh install, is this normal?

---

### Post by mc4man on 2018-03-31
Don't have ubuntu-gnome (16.04) but post results of this
```
apt-cache policy xserver-xorg-input-libinput xserver-xorg-input-synaptics
```

---

### Post by ray42 on 2018-04-01
xserver-xorg-input-libinput:
  Installed: (none)
  Candidate: 0.18.0-1ubuntu0.1
  Version table:
     0.18.0-1ubuntu0.1 500
        500 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/universe amd64 Packages
     0.18.0-1 500
        500 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial/universe amd64 Packages
xserver-xorg-input-synaptics:
  Installed: (none)
  Candidate: 1.8.2-1ubuntu3
  Version table:
     1.8.2-1ubuntu3 500
        500 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial/main amd64 Packages

---

### Post by mc4man on 2018-04-01
> **ray42 said:**
> xserver-xorg-input-libinput:
  Installed: (none)
  Candidate: 0.18.0-1ubuntu0.1
  Version table:
     0.18.0-1ubuntu0.1 500
        500 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/universe amd64 Packages
     0.18.0-1 500
        500 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial/universe amd64 Packages
xserver-xorg-input-synaptics:
  Installed: (none)
  Candidate: 1.8.2-1ubuntu3
  Version table:
     1.8.2-1ubuntu3 500
        500 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial/main amd64 Packages
Not sure of the state of libinput in 16.04, the synaptics will probably work ok or better than libinput.

You could start by installing xserver-xorg-input-libinput, reboot & see. If no go or not good enough then install the synaptics one, reboot.
Or start with installing xserver-xorg-input-synaptics, reboot & see. If no go, ect. then remove it, install the libinput one, reboot.

---

### Post by ray42 on 2018-04-02
Is this the same issue?

[https://unix.stackexchange.com/questions/292350/debian-gnome-touchpad-settings-missing-use-libinput-instead-of-synaptics](https://unix.stackexchange.com/questions/292350/debian-gnome-touchpad-settings-missing-use-libinput-instead-of-synaptics)

---

### Post by mc4man on 2018-04-02
> **ray42 said:**
> Is this the same issue?

[https://unix.stackexchange.com/questions/292350/debian-gnome-touchpad-settings-missing-use-libinput-instead-of-synaptics](https://unix.stackexchange.com/questions/292350/debian-gnome-touchpad-settings-missing-use-libinput-instead-of-synaptics)

Basically that could be true in 16.04 (not 18.04
Your main issue is you've nothing installed. So as said either install xserver-xorg-input-libinput, reboot & see or  install xserver-xorg-input-synaptics, reboot & see.
(- xserver-xorg-input-synaptics will overidde xserver-xorg-input-libinput so to test xserver-xorg-input-libinput the xserver-xorg-input-synaptics package can't be installed.

---

### Post by ray42 on 2018-04-05
Neither worked

```
sudo apt-get install xserver-xorg-input-libinputReading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies.
 xserver-xorg-input-libinput : Depends: xorg-input-abi-22
                               Depends: xserver-xorg-core (>= 2:1.17.99.902)
E: Unable to correct problems, you have held broken packages.
```

```
sudo apt-get install xserver-xorg-input-synapticsReading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies.
 xserver-xorg-input-synaptics : Depends: xorg-input-abi-22
                                Depends: xserver-xorg-core (>= 2:1.17.99.902)
E: Unable to correct problems, you have held broken packages.
```

That is my technical limit with using Terminal

---

### Post by cruzer001 on 2018-04-05
Please post the output of:
```
apt policy xserver-xorg-core && ls /etc/apt/sources.list.d/*.list
```

---

### Post by ray42 on 2018-04-06
```
apt policy xserver-xorg-core && ls /etc/apt/sources.list.d/*.listxserver-xorg-core:
  Installed: (none)
  Candidate: 2:1.18.4-0ubuntu0.7
  Version table:
     2:1.18.4-0ubuntu0.7 500
        500 http://gb.archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu xenial-security/main amd64 Packages
     2:1.18.3-1ubuntu2 500
        500 http://gb.archive.ubuntu.com/ubuntu xenial/main amd64 Packages
/etc/apt/sources.list.d/danielrichter2007-ubuntu-grub-customizer-xenial.list
/etc/apt/sources.list.d/dropbox.list
/etc/apt/sources.list.d/google-chrome.list
/etc/apt/sources.list.d/libdvdcss2.list
/etc/apt/sources.list.d/numix-ubuntu-ppa-xenial.list
/etc/apt/sources.list.d/peterlevi-ubuntu-ppa-xenial.list
/etc/apt/sources.list.d/stebbins-ubuntu-handbrake-releases-xenial.list
/etc/apt/sources.list.d/teamviewer.list
/etc/apt/sources.list.d/webupd8team-ubuntu-tor-browser-xenial.list

```

---

### Post by cruzer001 on 2018-04-06
Need to verify one more thing.  Please post the output of:

```
apt policy xserver-xorg-core-hwe-16.04 && uname -r
```

**Edit**
I had hoped to hear back from you before I called it a night, but since I didn't here is the next step.

I expect xserver-xorg-core-hwe-16.04 to show as installed.  If this is true, then the following package(s) should be used (or already installed).  Please check using "apt policy".

xserver-xorg-input-libinput-hwe-16.04

xserver-xorg-input-synaptics-hwe-16.04

---

### Post by ray42 on 2018-04-07
```

xserver-xorg-core-hwe-16.04:  Installed: 2:1.19.5-0ubuntu2~16.04.1
  Candidate: 2:1.19.5-0ubuntu2~16.04.1
  Version table:
 *** 2:1.19.5-0ubuntu2~16.04.1 500
        500 http://gb.archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages
        100 /var/lib/dpkg/status
     2:1.19.3-1ubuntu1~16.04.4 500
        500 http://security.ubuntu.com/ubuntu xenial-security/main amd64 Packages
4.13.0-38-generic

```

---

### Post by ray42 on 2018-04-07
```

Package files: 100 /var/lib/dpkg/status
     release a=now
 500 http://ppa.launchpad.net/webupd8team/tor-browser/ubuntu xenial/main i386 Packages
     release v=16.04,o=LP-PPA-webupd8team-tor-browser,a=xenial,n=xenial,l=Tor Browser,c=main,b=i386
     origin ppa.launchpad.net
 500 http://ppa.launchpad.net/webupd8team/tor-browser/ubuntu xenial/main amd64 Packages
     release v=16.04,o=LP-PPA-webupd8team-tor-browser,a=xenial,n=xenial,l=Tor Browser,c=main,b=amd64
     origin ppa.launchpad.net
 500 http://linux.teamviewer.com/deb preview/main i386 Packages
     release o=TeamViewer GmbH,a=preview,l=TeamViewer,c=main,b=i386
     origin linux.teamviewer.com
 500 http://linux.teamviewer.com/deb preview/main amd64 Packages
     release o=TeamViewer GmbH,a=preview,l=TeamViewer,c=main,b=amd64
     origin linux.teamviewer.com
 500 http://linux.teamviewer.com/deb stable/main i386 Packages
     release o=TeamViewer GmbH,a=stable,l=TeamViewer,c=main,b=i386
     origin linux.teamviewer.com
 500 http://linux.teamviewer.com/deb stable/main amd64 Packages
     release o=TeamViewer GmbH,a=stable,l=TeamViewer,c=main,b=amd64
     origin linux.teamviewer.com
 500 http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu xenial/main i386 Packages
     release v=16.04,o=LP-PPA-stebbins-handbrake-releases,a=xenial,n=xenial,l=HandBrake Releases,c=main,b=i386
     origin ppa.launchpad.net
 500 http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu xenial/main amd64 Packages
     release v=16.04,o=LP-PPA-stebbins-handbrake-releases,a=xenial,n=xenial,l=HandBrake Releases,c=main,b=amd64
     origin ppa.launchpad.net
 500 http://ppa.launchpad.net/peterlevi/ppa/ubuntu xenial/main i386 Packages
     release v=16.04,o=LP-PPA-peterlevi,a=xenial,n=xenial,l=Peter Levi's PPA,c=main,b=i386
     origin ppa.launchpad.net
 500 http://ppa.launchpad.net/peterlevi/ppa/ubuntu xenial/main amd64 Packages
     release v=16.04,o=LP-PPA-peterlevi,a=xenial,n=xenial,l=Peter Levi's PPA,c=main,b=amd64
     origin ppa.launchpad.net
 500 http://ppa.launchpad.net/numix/ppa/ubuntu xenial/main i386 Packages
     release v=16.04,o=LP-PPA-numix,a=xenial,n=xenial,l=PPA for the Numix Project Ltd.,c=main,b=i386
     origin ppa.launchpad.net
 500 http://ppa.launchpad.net/numix/ppa/ubuntu xenial/main amd64 Packages
     release v=16.04,o=LP-PPA-numix,a=xenial,n=xenial,l=PPA for the Numix Project Ltd.,c=main,b=amd64
     origin ppa.launchpad.net
 500 http://download.videolan.org/pub/debian/stable  Packages
     release o=videolan,a=stable,n=stable,l=videolan,c=
     origin download.videolan.org
 500 http://dl.google.com/linux/chrome/deb stable/main amd64 Packages
     release v=1.0,o=Google, Inc.,a=stable,n=stable,l=Google,c=main,b=amd64
     origin dl.google.com
 500 http://linux.dropbox.com/ubuntu wily/main amd64 Packages
     release o=Dropbox.com,a=wily,n=wily,l=Dropbox Ubuntu Repository,c=main,b=amd64
     origin linux.dropbox.com
 500 http://linux.dropbox.com/ubuntu wily/main i386 Packages
     release o=Dropbox.com,a=wily,n=wily,l=Dropbox Ubuntu Repository,c=main,b=i386
     origin linux.dropbox.com
 500 http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu xenial/main i386 Packages
     release v=16.04,o=LP-PPA-danielrichter2007-grub-customizer,a=xenial,n=xenial,l=Launchpad PPA for Grub Customizer,c=main,b=i386
     origin ppa.launchpad.net
 500 http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu xenial/main amd64 Packages
     release v=16.04,o=LP-PPA-danielrichter2007-grub-customizer,a=xenial,n=xenial,l=Launchpad PPA for Grub Customizer,c=main,b=amd64
     origin ppa.launchpad.net
 500 http://security.ubuntu.com/ubuntu xenial-security/multiverse i386 Packages
     release v=16.04,o=Ubuntu,a=xenial-security,n=xenial,l=Ubuntu,c=multiverse,b=i386
     origin security.ubuntu.com
 500 http://security.ubuntu.com/ubuntu xenial-security/multiverse amd64 Packages
     release v=16.04,o=Ubuntu,a=xenial-security,n=xenial,l=Ubuntu,c=multiverse,b=amd64
     origin security.ubuntu.com
 500 http://security.ubuntu.com/ubuntu xenial-security/universe i386 Packages
     release v=16.04,o=Ubuntu,a=xenial-security,n=xenial,l=Ubuntu,c=universe,b=i386
     origin security.ubuntu.com
 500 http://security.ubuntu.com/ubuntu xenial-security/universe amd64 Packages
     release v=16.04,o=Ubuntu,a=xenial-security,n=xenial,l=Ubuntu,c=universe,b=amd64
     origin security.ubuntu.com
 500 http://security.ubuntu.com/ubuntu xenial-security/restricted i386 Packages
     release v=16.04,o=Ubuntu,a=xenial-security,n=xenial,l=Ubuntu,c=restricted,b=i386
     origin security.ubuntu.com
 500 http://security.ubuntu.com/ubuntu xenial-security/restricted amd64 Packages
     release v=16.04,o=Ubuntu,a=xenial-security,n=xenial,l=Ubuntu,c=restricted,b=amd64
     origin security.ubuntu.com
 500 http://security.ubuntu.com/ubuntu xenial-security/main i386 Packages
     release v=16.04,o=Ubuntu,a=xenial-security,n=xenial,l=Ubuntu,c=main,b=i386
     origin security.ubuntu.com
 500 http://security.ubuntu.com/ubuntu xenial-security/main amd64 Packages
     release v=16.04,o=Ubuntu,a=xenial-security,n=xenial,l=Ubuntu,c=main,b=amd64
     origin security.ubuntu.com
 500 http://archive.canonical.com/ubuntu xenial/partner i386 Packages
     release v=16.04,o=Canonical,a=xenial,n=xenial,l=Partner archive,c=partner,b=i386
     origin archive.canonical.com
 500 http://archive.canonical.com/ubuntu xenial/partner amd64 Packages
     release v=16.04,o=Canonical,a=xenial,n=xenial,l=Partner archive,c=partner,b=amd64
     origin archive.canonical.com
 100 http://gb.archive.ubuntu.com/ubuntu xenial-backports/universe i386 Packages
     release v=16.04,o=Ubuntu,a=xenial-backports,n=xenial,l=Ubuntu,c=universe,b=i386
     origin gb.archive.ubuntu.com
 100 http://gb.archive.ubuntu.com/ubuntu xenial-backports/universe amd64 Packages
     release v=16.04,o=Ubuntu,a=xenial-backports,n=xenial,l=Ubuntu,c=universe,b=amd64
     origin gb.archive.ubuntu.com
 100 http://gb.archive.ubuntu.com/ubuntu xenial-backports/main i386 Packages
     release v=16.04,o=Ubuntu,a=xenial-backports,n=xenial,l=Ubuntu,c=main,b=i386
     origin gb.archive.ubuntu.com
 100 http://gb.archive.ubuntu.com/ubuntu xenial-backports/main amd64 Packages
     release v=16.04,o=Ubuntu,a=xenial-backports,n=xenial,l=Ubuntu,c=main,b=amd64
     origin gb.archive.ubuntu.com
 500 http://gb.archive.ubuntu.com/ubuntu xenial-updates/multiverse i386 Packages
     release v=16.04,o=Ubuntu,a=xenial-updates,n=xenial,l=Ubuntu,c=multiverse,b=i386
     origin gb.archive.ubuntu.com
 500 http://gb.archive.ubuntu.com/ubuntu xenial-updates/multiverse amd64 Packages
     release v=16.04,o=Ubuntu,a=xenial-updates,n=xenial,l=Ubuntu,c=multiverse,b=amd64
     origin gb.archive.ubuntu.com
 500 http://gb.archive.ubuntu.com/ubuntu xenial-updates/universe i386 Packages
     release v=16.04,o=Ubuntu,a=xenial-updates,n=xenial,l=Ubuntu,c=universe,b=i386
     origin gb.archive.ubuntu.com
 500 http://gb.archive.ubuntu.com/ubuntu xenial-updates/universe amd64 Packages
     release v=16.04,o=Ubuntu,a=xenial-updates,n=xenial,l=Ubuntu,c=universe,b=amd64
     origin gb.archive.ubuntu.com
 500 http://gb.archive.ubuntu.com/ubuntu xenial-updates/restricted i386 Packages
     release v=16.04,o=Ubuntu,a=xenial-updates,n=xenial,l=Ubuntu,c=restricted,b=i386
     origin gb.archive.ubuntu.com
 500 http://gb.archive.ubuntu.com/ubuntu xenial-updates/restricted amd64 Packages
     release v=16.04,o=Ubuntu,a=xenial-updates,n=xenial,l=Ubuntu,c=restricted,b=amd64
     origin gb.archive.ubuntu.com
 500 http://gb.archive.ubuntu.com/ubuntu xenial-updates/main i386 Packages
     release v=16.04,o=Ubuntu,a=xenial-updates,n=xenial,l=Ubuntu,c=main,b=i386
     origin gb.archive.ubuntu.com
 500 http://gb.archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages
     release v=16.04,o=Ubuntu,a=xenial-updates,n=xenial,l=Ubuntu,c=main,b=amd64
     origin gb.archive.ubuntu.com
 500 http://gb.archive.ubuntu.com/ubuntu xenial/multiverse i386 Packages
     release v=16.04,o=Ubuntu,a=xenial,n=xenial,l=Ubuntu,c=multiverse,b=i386
     origin gb.archive.ubuntu.com
 500 http://gb.archive.ubuntu.com/ubuntu xenial/multiverse amd64 Packages
     release v=16.04,o=Ubuntu,a=xenial,n=xenial,l=Ubuntu,c=multiverse,b=amd64
     origin gb.archive.ubuntu.com
 500 http://gb.archive.ubuntu.com/ubuntu xenial/universe i386 Packages
     release v=16.04,o=Ubuntu,a=xenial,n=xenial,l=Ubuntu,c=universe,b=i386
     origin gb.archive.ubuntu.com
 500 http://gb.archive.ubuntu.com/ubuntu xenial/universe amd64 Packages
     release v=16.04,o=Ubuntu,a=xenial,n=xenial,l=Ubuntu,c=universe,b=amd64
     origin gb.archive.ubuntu.com
 500 http://gb.archive.ubuntu.com/ubuntu xenial/restricted i386 Packages
     release v=16.04,o=Ubuntu,a=xenial,n=xenial,l=Ubuntu,c=restricted,b=i386
     origin gb.archive.ubuntu.com
 500 http://gb.archive.ubuntu.com/ubuntu xenial/restricted amd64 Packages
     release v=16.04,o=Ubuntu,a=xenial,n=xenial,l=Ubuntu,c=restricted,b=amd64
     origin gb.archive.ubuntu.com
 500 http://gb.archive.ubuntu.com/ubuntu xenial/main i386 Packages
     release v=16.04,o=Ubuntu,a=xenial,n=xenial,l=Ubuntu,c=main,b=i386
     origin gb.archive.ubuntu.com
 500 http://gb.archive.ubuntu.com/ubuntu xenial/main amd64 Packages
     release v=16.04,o=Ubuntu,a=xenial,n=xenial,l=Ubuntu,c=main,b=amd64
     origin gb.archive.ubuntu.com
Pinned packages:

```

---

### Post by cruzer001 on 2018-04-07
That last command did not output right.  Try this:
```

apt policy xserver-xorg-input-libinput-hwe-16.04 xserver-xorg-input-synaptics-hwe-16.04 && xinput list
```

This has become a long thread for just turning off a touchpad, don't lose hope.  If the GUI will not work then it can just be shut down manually as pointed out in post #5.

---

### Post by ray42 on 2018-04-07
```

apt policy xserver-xorg-input-libinput-hwe-16.04 xserver-xorg-input-synaptics-hwe-16.04 && xinput listxserver-xorg-input-libinput-hwe-16.04:
  Installed: (none)
  Candidate: 0.25.0-0ubuntu1~16.04.1
  Version table:
     0.25.0-0ubuntu1~16.04.1 500
        500 http://gb.archive.ubuntu.com/ubuntu xenial-updates/universe amd64 Packages
xserver-xorg-input-synaptics-hwe-16.04:
  Installed: 1.9.0-1ubuntu1~16.04.1
  Candidate: 1.9.0-1ubuntu1~16.04.1
  Version table:
 *** 1.9.0-1ubuntu1~16.04.1 500
        500 http://gb.archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages
        100 /var/lib/dpkg/status
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Microsoft Microsoft 5-Button Mouse with IntelliEye(TM)	id=9	[slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad              	id=12	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=8	[slave  keyboard (3)]
    &#8627; Chicony USB 2.0 Camera: Chicony         	id=10	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=11	[slave  keyboard (3)]

```

---

### Post by ray42 on 2018-04-07
> [COLOR=#000000]This has become a long thread for just turning off a touchpad, don't lose hope. If the GUI will not work then it can just be shut down manually as pointed out in post #5.[/COLOR]

Yes I can, but it should be seen in settings. As I say this was a fresh install, on a freshly for formatted HDD.

I have done this twice recently, both times the touchpad setting was not visible.

If you manage to find a fix it should help others, I suppose this is the way to view this situation.

Thx for trying

---

### Post by mc4man on 2018-04-07
try installing the xserver-xorg-input-libinput-hwe-16.04 package & removing the xserver-xorg-input-synaptics-hwe-16.04 package, then reboot

---

### Post by ray42 on 2018-04-12
Yes seems fixed.

Can see touchpad option, any ideas as why on a new install its missing

---

### Post by mc4man on 2018-04-12
> **ray42 said:**
> Yes seems fixed.

Can see touchpad option, any ideas as why on a new install its missing
Likely because on a fresh install both xserver packages are included & the synaptics one overrides the libinput one.
This will not be the case in 18.04 which will default provide only libinput xserver package.

---

### Post by ray42 on 2018-04-12
solved, thanks once again :D

---

