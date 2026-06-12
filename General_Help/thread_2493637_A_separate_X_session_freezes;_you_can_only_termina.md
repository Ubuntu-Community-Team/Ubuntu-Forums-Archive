---
title: "A separate X session freezes; you can only terminate it with the reset button."
date: 2023-12-20
forum: General Help
---

### Post by Diablero on 2023-12-20
Hi all!! I moved to Ubuntu 22.04 from 20.04 and now this is the problem. There is nothing in the Xorg.0.log logs. NVIDIA video card driver 545.29.02 I launch it with the command xinit -- :2
My scripts for a separate X session: 
.xinitrc
> xrdb -merge ~/.Xresources
xbindkeys
xrandr --output HDMI-1 --off --output DP-2 --mode 1920x1080
xterm
#XTerm
> ...
XTerm*foreground: white
XTerm*background: Purple4
XTerm*cursorColor: green
XTerm*scrollBar: True
XTerm*saveLines: 800
# XTerm*font: -xos4-terminus-medium-r-normal--32-320-72-72-c-160-iso10646-1
XTerm*font: -sony-fixed-medium-r-normal--24-230-75-75-c-120-iso8859-1
# XTerm*font: -adobe-courier-bold-o-normal--0-0-100-100-m-0-iso10646-1
# XTerm*font: -sun-open look cursor-----12-120-75-75-p-160-sunolcursor-1
XTerm*geometry: 158x40+0+0
...
.xResources
> xterm*termName: xterm-256color
XTerm*foreground: #ffffff
XTerm*background: #5f005f
XTerm*cursorColor: #ffffff
XTerm*scrollBar: True
XTerm*saveLines: 800
!XTerm*font: -sony-fixed-medium-r-normal--24-230-75-75-c-120-iso8859-1
XTerm*faceName: Ubuntu Mono:style=Regular
XTerm*geometry: 211x56+0+0

.xbindkeysrc
> "xbindkeys_show" 
  control+shift + q
#Screenshot of a separate X session 
"xwd -out /home/diablero/Images/Images/Screenshots/screenshot.xwd -root -display :2" m:0x10 + c:107

blacklist
> blacklist nouveau
blacklist lbm-nouveau
options nouveau modeset=0
alias nouveau off
alias lbm-nouveau off

What it looks like: I switch and after a random(short) time it freezes, even the mouse doesn’t move and you can’t reboot using alt+ctrl+delete, you can’t switch back to any other tty, only reset. You can run MC, it works, but as soon as you quit everything freezes. And if you run glxgears or war thunder, it freezes almost immediately. 
And here's another error:
> kernel:[14544.334745] watchdog: BUG: soft lockup - CPU#4 stuck for 108s! [Xorg:76483]
I searched about this error, but as far as I understand it is not related to it, but I could be wrong.
Dear forum users, please help!

---

### Post by MAFoElffen on 2023-12-20
If you do 'killall' on the Desktop Environment (DE) or Desktop Manager (DM) then it kills it without having to reboot.

Such as <Cntrl><Alt><F4>. Login. 
```

sudo killall -HUD GDM3
# OR
sudo killall -HUD gnome-session

```

---

### Post by Diablero on 2023-12-22
I can't do this because the system freezes completely, the keyboard and mouse do not work... I forgot to write that the monitor goes out about 30 seconds after that.

---

### Post by MAFoElffen on 2023-12-22
What is the CPU & GPU?

---

### Post by Diablero on 2023-12-22
> **MAFoElffen said:**
> What is the CPU & GPU?

CPU - I7-6700K
GPU - ASUS NVIDIA 1080ti ROG STRIX
MB - ASUS Z170P

I think maybe something has changed in the X? And now you need to launch a separate session somehow differently? How to find out?

---

### Post by MAFoElffen on 2023-12-22
Please post the output of this:
```

apt list nvidia-* --installed
nvidia-smi
modinfo nvidia | grep -v '^parm\|^alias'
uname -r

```

---

### Post by Diablero on 2023-12-22
> **MAFoElffen said:**
> Please post the output of this:
```

apt list nvidia-* --installed
nvidia-smi
modinfo nvidia | grep -v '^parm\|^alias'
uname -r

```

diablero@diableropc:~$ apt list nvidia-* --installed
List output... Done

diablero@diableropc:~$ nvidia-smi
Fri Dec 22 19:40:27 2023       
+---------------------------------------------------------------------------------------+
| NVIDIA-SMI 545.29.02              Driver Version: 545.29.02    CUDA Version: 12.3     |
|-----------------------------------------+----------------------+----------------------+
| GPU  Name                 Persistence-M | Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp   Perf          Pwr:Usage/Cap |         Memory-Usage | GPU-Util  Compute M. |
|                                         |                      |               MIG M. |
|=========================================+======================+======================|
|   0  NVIDIA GeForce GTX 1080 Ti     Off | 00000000:01:00.0  On |                  N/A |
|  0%   52C    P0              66W / 250W |    150MiB / 11264MiB |      0%      Default |
|                                         |                      |                  N/A |
+-----------------------------------------+----------------------+----------------------+
                                                                                         
+---------------------------------------------------------------------------------------+
| Processes:                                                                            |
|  GPU   GI   CI        PID   Type   Process name                            GPU Memory |
|        ID   ID                                                             Usage      |
|=======================================================================================|
|    0   N/A  N/A      5142      G   /usr/lib/xorg/Xorg                           97MiB |
|    0   N/A  N/A      5319      G   /usr/bin/gnome-shell                         47MiB |
+---------------------------------------------------------------------------------------+

diablero@diableropc:~$ modinfo nvidia | grep -v '^parm\|^alias'
filename:       /lib/modules/6.2.0-39-generic/updates/dkms/nvidia.ko
version:        545.29.02
supported:      external
license:        NVIDIA
firmware:       nvidia/545.29.02/gsp_tu10x.bin
firmware:       nvidia/545.29.02/gsp_ga10x.bin
srcversion:     8302209549E8FEAC029EDC0
depends:        drm
retpoline:      Y
name:           nvidia
vermagic:       6.2.0-39-generic SMP preempt mod_unload modversions
 
diablero@diableropc:~$ uname -r
6.2.0-39-generic

---

### Post by MAFoElffen on 2023-12-22
Sidenote... Please look at the CODE tags link in my signature line to edit the raw output i your last post... (To keep yourself out of troubles.)

1fallen just PM'ed me about your results. I agree with him. Something is seriously wrong with those results. They are seriously "incomplete".

You installed the NVidia binary driver directly from NVidia, rather than from the drivers from the Ubuntu repo's right?

For example:
```

mafoelffen@msi-ubuntu:~$ apt list nvidia-* --installed
Listing... Done
nvidia-compute-utils-535/jammy-updates,jammy-security,now 535.129.03-0ubuntu0.22.04.1 amd64 [installed,automatic]
nvidia-dkms-535/jammy-updates,jammy-security,now 535.129.03-0ubuntu0.22.04.1 amd64 [installed,automatic]
nvidia-driver-530/jammy-updates,jammy-security,now 535.129.03-0ubuntu0.22.04.1 amd64 [installed]
nvidia-driver-535/jammy-updates,jammy-security,now 535.129.03-0ubuntu0.22.04.1 amd64 [installed,automatic]
nvidia-firmware-535-535.129.03/jammy-updates,jammy-security,now 535.129.03-0ubuntu0.22.04.1 amd64 [installed,automatic]
nvidia-kernel-common-535/jammy-updates,jammy-security,now 535.129.03-0ubuntu0.22.04.1 amd64 [installed,automatic]
nvidia-kernel-source-535/jammy-updates,jammy-security,now 535.129.03-0ubuntu0.22.04.1 amd64 [installed,automatic]
nvidia-prime/jammy,jammy,now 0.8.17.1 all [installed,automatic]
nvidia-settings/jammy,now 510.47.03-0ubuntu1 amd64 [installed]
nvidia-utils-535/jammy-updates,jammy-security,now 535.129.03-0ubuntu0.22.04.1 amd64 [installed,automatic]

mafoelffen@msi-ubuntu:~$ nvidia-smi
Fri Dec 22 09:02:33 2023       
+---------------------------------------------------------------------------------------+
| NVIDIA-SMI 535.129.03             Driver Version: 535.129.03   CUDA Version: 12.2     |
|-----------------------------------------+----------------------+----------------------+
| GPU  Name                 Persistence-M | Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp   Perf          Pwr:Usage/Cap |         Memory-Usage | GPU-Util  Compute M. |
|                                         |                      |               MIG M. |
|=========================================+======================+======================|
|   0  NVIDIA GeForce GTX 1660 Ti     Off | 00000000:01:00.0  On |                  N/A |
|  0%   31C    P8               9W / 130W |    119MiB /  6144MiB |      2%      Default |
|                                         |                      |                  N/A |
+-----------------------------------------+----------------------+----------------------+
                                                                                         
+---------------------------------------------------------------------------------------+
| Processes:                                                                            |
|  GPU   GI   CI        PID   Type   Process name                            GPU Memory |
|        ID   ID                                                             Usage      |
|=======================================================================================|
|    0   N/A  N/A      5995      G   /usr/lib/xorg/Xorg                           84MiB |
|    0   N/A  N/A      7368      G   /usr/bin/gnome-shell                         23MiB |
|    0   N/A  N/A   1265738      G   ...irefox/3416/usr/lib/firefox/firefox        8MiB |
+---------------------------------------------------------------------------------------+

mafoelffen@msi-ubuntu:~$ modinfo nvidia | grep -v '^parm\|^alias'
filename:       /lib/modules/6.2.0-37-generic/updates/dkms/nvidia.ko
firmware:       nvidia/535.129.03/gsp_tu10x.bin
firmware:       nvidia/535.129.03/gsp_ga10x.bin
version:        535.129.03
supported:      external
license:        NVIDIA
srcversion:     3A52EBD98F6E1FB4A4E944F
depends:        drm
retpoline:      Y
name:           nvidia
vermagic:       6.2.0-37-generic SMP preempt mod_unload modversions 
sig_id:         PKCS#7
signer:         ubuntu-server Secure Boot Module Signature key
sig_key:        61:E0:9A:71:83:7C:41:FB:A6:77:8B:3D:CF:C4:88:D1:93:87:1D:15
sig_hashalgo:   sha512
signature:      2B:98:BE:9E:FA:9D:40:73:D4:26:37:FB:CC:56:B6:72:20:94:EA:9F:
        58:F9:9D:92:0C:BB:3D:56:DA:B6:A6:7C:33:57:49:39:B8:ED:80:20:
        8E:BD:B3:DD:C9:C5:00:37:1A:24:1F:15:65:CB:D8:C0:4E:30:63:B5:
        A2:A6:D6:61:75:F3:DB:BC:44:BD:60:05:06:9C:9C:33:A9:CD:F3:A2:
        BD:7E:DC:C6:97:B1:65:6D:E5:D4:44:82:86:3C:18:F3:40:AA:D1:16:
        0B:EF:1C:36:5E:AE:97:18:D2:5A:97:21:C7:0A:91:63:F2:B6:D3:B8:
        F4:1A:DD:70:DB:5F:3C:0E:41:16:56:D2:2A:A4:E7:80:EF:03:CE:E2:
        7C:C1:BE:1E:F1:27:CB:BA:DC:EB:80:61:38:B6:64:20:72:7C:D6:9A:
        38:4A:4B:C8:6B:65:F3:65:ED:01:82:6E:9D:90:6E:9B:45:2A:46:91:
        CB:56:06:50:A5:EA:F3:46:44:CB:F2:84:D3:A8:A8:D8:3F:8A:B0:44:
        41:8F:FD:D4:E0:E0:B2:39:43:10:83:CF:31:8E:F7:47:9A:F8:95:15:
        1A:03:F9:06:BE:36:C2:2A:53:3F:43:39:36:0C:FF:D7:3A:3D:01:05:
        4F:F1:78:2C:F2:4D:0C:55:10:45:10:7A:FB:1E:B6:CE

mafoelffen@msi-ubuntu:~$ uname -r
6.2.0-37-generic

```
@1fallen -- You are using driver 545 right? Could you please post your results for the same so he can see those?

---

### Post by #&amp;thj^% on 2023-12-22
> **MAFoElffen said:**
> 
@1fallen -- You are using driver 545 right? Could you please post your results for the same so he can see those?

Certainly
```
apt list nvidia-* --installed
Listing... Done
nvidia-compute-utils-545/noble,now 545.29.06-0ubuntu0~gpu24.04.1 amd64 [installed,automatic]
nvidia-dkms-545/noble,now 545.29.06-0ubuntu0~gpu24.04.1 amd64 [installed]
nvidia-driver-545/noble,now 545.29.06-0ubuntu0~gpu24.04.1 amd64 [installed]
nvidia-firmware-545-545.29.06/noble,now 545.29.06-0ubuntu0~gpu24.04.1 amd64 [installed,automatic]
nvidia-kernel-common-545/noble,now 545.29.06-0ubuntu0~gpu24.04.1 amd64 [installed,automatic]
nvidia-kernel-source-545/noble,now 545.29.06-0ubuntu0~gpu24.04.1 amd64 [installed,automatic]
nvidia-prime/noble,noble,now 0.8.17.2 all [installed,automatic]
nvidia-settings/noble,now 510.47.03-0ubuntu1 amd64 [installed,automatic]
nvidia-utils-545/noble,now 545.29.06-0ubuntu0~gpu24.04.1 amd64 [installed,automatic]

```
```
nvidia-smi
Fri Dec 22 10:17:44 2023       
+---------------------------------------------------------------------------------------+
| NVIDIA-SMI 545.29.06              Driver Version: 545.29.06    CUDA Version: 12.3     |
|-----------------------------------------+----------------------+----------------------+
| GPU  Name                 Persistence-M | Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp   Perf          Pwr:Usage/Cap |         Memory-Usage | GPU-Util  Compute M. |
|                                         |                      |               MIG M. |
|=========================================+======================+======================|
|   0  NVIDIA GeForce RTX 3050 ...    Off | 00000000:01:00.0  On |                  N/A |
| N/A   29C    P8               4W /  60W |    342MiB /  4096MiB |     14%      Default |
|                                         |                      |                  N/A |
+-----------------------------------------+----------------------+----------------------+
                                                                                         
+---------------------------------------------------------------------------------------+
| Processes:                                                                            |
|  GPU   GI   CI        PID   Type   Process name                            GPU Memory |
|        ID   ID                                                             Usage      |
|=======================================================================================|
|    0   N/A  N/A      1753      G   /usr/lib/xorg/Xorg                          195MiB |
|    0   N/A  N/A      2474      G   xfwm4                                         2MiB |
|    0   N/A  N/A      3862      G   /usr/lib/firefox/firefox                    135MiB |
+---------------------------------------------------------------------------------------+

```
```
 modinfo nvidia | grep -v '^parm\|^alias'
filename:       /lib/modules/6.5.0-9-generic/updates/dkms/nvidia.ko.zst
version:        545.29.06
supported:      external
license:        NVIDIA
firmware:       nvidia/545.29.06/gsp_tu10x.bin
firmware:       nvidia/545.29.06/gsp_ga10x.bin
srcversion:     8302209549E8FEAC029EDC0
depends:        drm
retpoline:      Y
name:           nvidia
vermagic:       6.5.0-9-generic SMP preempt mod_unload modversions 
sig_id:         PKCS#7
signer:         me-Legion-zfs Secure Boot Module Signature key
sig_key:        1D:D6:B4:43:BD:4C:06:CA:A6:58:CA:86:4B:99:6A:A0:5E:C7:D3:7A
sig_hashalgo:   sha512
signature:      AD:38:50:35:F4:F8:49:F0:F7:5B:FB:32:C4:63:5B:CE:31:36:40:81:
		AD:62:E5:9B:FC:3C:3E:60:79:FF:18:E3:9F:25:94:35:08:72:66:6C:
		BC:AE:33:B2:52:BD:F5:CE:23:5A:C2:DD:D3:01:72:B7:97:F2:60:47:
		84:37:EE:6D:F2:42:CC:C9:50:34:C5:A2:9D:F3:C1:45:A0:89:90:4B:
		1D:39:FC:6B:C0:FA:2F:91:0F:40:9F:E6:91:52:16:D0:E1:B7:83:71:
		3A:93:26:84:AB:AC:CD:B8:28:BA:05:E7:21:B4:21:67:51:12:DE:3B:
		9E:D3:AD:30:23:52:08:D4:85:64:43:04:35:6E:02:B6:00:4F:4F:1C:
		77:B7:36:0D:2E:1B:85:69:88:E6:51:D9:20:99:00:69:04:F9:DF:25:
		90:F8:C3:79:E9:B9:10:EA:63:46:FD:C3:E2:A9:57:BB:EF:98:16:2C:
		5F:D0:77:E3:CB:8B:3F:1F:97:1F:7B:C4:25:6C:9D:D5:9F:76:17:4D:
		34:67:5F:73:07:A8:55:28:C2:2D:B1:14:EB:FA:F7:37:02:A8:D8:CD:
		BE:74:E3:4F:CA:CD:EC:98:43:52:37:E4:D9:6B:48:8C:E2:34:FD:0B:
		5A:D8:34:26:FF:C4:BC:F6:18:7B:0E:46:62:59:B0:12
&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;>

```
I will add  "I" wont say 545 is ready for prime time though.
My advice is stick with 535

---

### Post by Diablero on 2023-12-22
[**[COLOR=#DD4814][B]MAFoElffen**[/COLOR][/B]]("https://ubuntuforums.org/member.php?u=1044547"), yes I use the driver downloaded from the Nvidia website. I've been doing this since Ubuntu 10.04. first I delete using the "--uninstall" command, remove the previous driver, then install a new one, with 32-bit libraries and a DKMS module. I do everything from the command line, and before that I turn it off DM "/etc/init.d/gdm3 stop".
"apt list nvidia-* --installed"
after this command there is empty output.

---

### Post by #&amp;thj^% on 2023-12-22
This not meant as snark or negative in manner, but I won't help with that type of install, and yes I do on occasion install from nVidia's site for testing purpose only. (since Ubuntu 5.04)
As much as i hate to admit it, using the Repo Versions result in a more satisfying system experience,

This might be better asking on nVidias forum.

---

### Post by MAFoElffen on 2023-12-22
I am suspecting this is an NVidia 545.29.02545.29.02 binary driver issue...

What about the results to this? Since you haven't figured out how to use CODE Tags yet, please attach the error-log.txt file to your post as an attachment...
```

journalctl -b2 -l -p 6 -o verbose -g 'NVRM|GPU|shutdown' --no-pager > $HOME/Downloads/error-log.txt

```

---

### Post by Diablero on 2023-12-23
> **1fallen said:**
> This not meant as snark or negative in manner, but I won't help with that type of install, and yes I do on occasion install from nVidia's site for testing purpose only. (since Ubuntu 5.04)
As much as i hate to admit it, using the Repo Versions result in a more satisfying system experience,

This might be better asking on nVidias forum.

Everything is fine, I have heard more than once that it is better not to install drivers from the nvidia site, but to use the Repo Versions=)
In any case, thanks for the help! Thanks for the advice to check out the nvidia forum!

---

### Post by Diablero on 2023-12-23
[**[COLOR=#DD4814][B]MAFoElffen**[/COLOR][/B]]("https://ubuntuforums.org/member.php?u=1044547"), the file turned out to be huge, 2.2mb and I can’t attach it due to the size limit of 19kb...

---

### Post by Diablero on 2023-12-23
Should I just install a new version of the driver? Version 535.146.02 was just recently released.

---

### Post by Diablero on 2023-12-23
In general, I installed a new driver - 535.146.02 and everything works great! The problem was in the driver, as you expected. Thanks everyone for your help!

---

### Post by MAFoElffen on 2023-12-23
Good to hear!

Please go to the "Thread Tools" link and select "Solved" to mark your thread as solves, so that others may find what worked for you, so that they may find answers to their similar problems.

FYI -- The output on mine was about 7-10 line entries, so yes, that query found problems. If, in the future, if a log is too large to attach, you could always paste to a pastebin such as paste.ubuntu.com for someone to look at. Just info for the future just-in-cases.

---

