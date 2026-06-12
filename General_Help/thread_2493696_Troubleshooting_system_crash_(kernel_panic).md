---
title: "Troubleshooting system crash (kernel panic?)"
date: 2023-12-21
forum: General Help
---

### Post by Regexaurus on 2023-12-21
I manage 3 Terryza W5 Pro (Intel Atom Z8350) systems. Think Intel Compute Stick. lsb_release -a currently shows Ubuntu 22.04.3 LTS. &#129300; Lubuntu was originally installed. I wonder if I mistakenly switched to Ubuntu during a release upgrade... The systems are used to run RiseVision media player (digital signage). 2 of the systems are very reliable, but one seems to "crash" every 2 weeks or so (sometimes more frequently). Symptoms are no video signal and no network connectivity. I can't ping or access by SSH. When this happens, my current workaround is a forced shutdown (press and hold power button) and power back on. I've tried checking in /var/log/syslog and /var/log/kern.log, but haven't found anything definitive, and don't know what I'm looking for, exactly. Can you offer suggestions for troubleshooting / identifying the problem? I would appreciate your suggestions!

---

### Post by guiverc on 2023-12-21
Lubuntu is an [*official flavor* of Ubuntu]("https://ubuntu.com/desktop/flavours"), and as such installs of Lubuntu are really Ubuntu systems, with different packages installed by default (*those that the [Lubuntu team put in their seed file]("https://ubuntu-archive-team.ubuntu.com/seeds/lubuntu.jammy/desktop"), rather than those the [Ubuntu Desktop did for theirs]("https://ubuntu-archive-team.ubuntu.com/seeds/ubuntu.jammy/desktop")*). If you looked at where you downloaded the system, both came from [https://cdimage.ubuntu.com/](https://cdimage.ubuntu.com/) with only the directory differing (*both having been built by the same infrastructure & builders*).  

That is why you're seeing the output from `lsb_release`. If you want to see the *flavor* you're using (ie. Lubuntu), you'll need to use `neofetch` which will detect your *flavor* of Ubuntu is Lubuntu & show that (*unless you're using root user or other situations when run*).

If you force reboot; many messages will be lost, eg. `dmesg` shows message from boot, which is why nothing useful is found in syslog unless written there in the current boot. The System D journal (`journalctl`) however survives reboot, thus is useful to look for clues if you needed to reboot/start the system.

I'd also look for *crash* files in `/var/crash`, though many third party apps may not put crash files there & leave clues elsewhere on the file-system(s), some won't leave any; as the programmer/packager of the app & type of packaging can influence this (*I don't know RiseVision sorry*).

---

### Post by Regexaurus on 2023-12-26
Thank you for the suggestions! neofetch shows this for the 3 systems (not running as root):
OS: Ubuntu 22.04.3 LTS x86_64
I see no mention of Lubuntu in the output.

---

### Post by #&amp;thj^% on 2023-12-26
I'm curious now, what will this yield:
```
tac /etc/os-release

```

Also just to be sure, I think guiverc suggestion of neofetch would be nicer used as:
```
neofetch --off
```
Mine:
```
neofetch --off
me@parrot 
--------- 
OS: Parrot Security 6.0 (lorikeet) x86_64 
Host: 82JW Legion 5 15ACH6 
Kernel: 6.5.0-13parrot1-amd64 
Uptime: 7 hours, 5 mins 
Packages: 2580 (dpkg), 10 (flatpak) 
Shell: bash 5.2.15 
Resolution: 1920x1080 
DE: MATE 1.26.0 
WM: Metacity (Marco) 
Theme: ARK-Dark [GTK2/3] 
Icons: Mint-Y-Dark-Aqua [GTK2/3] 
Terminal: mate-terminal 
Terminal Font: Monospace 10 
CPU: AMD Ryzen 5 5600H with Radeon Graphics (12) @ 4.280GHz 
GPU: NVIDIA GeForce RTX 3050 Ti Mobile 
Memory: 2095MiB / 15839MiB 

```

---

### Post by guiverc on 2023-12-26
> **Regexaurus said:**
> Thank you for the suggestions! neofetch shows this for the 3 systems (not running as root):
OS: Ubuntu 22.04.3 LTS x86_64
I see no mention of Lubuntu in the output.


If I run `neofetch` using my normal account, I get the following

```

guiverc@d7050-next:~/uwn/issues/819$   neofetch --off
guiverc@d7050-next 
------------------ 
OS: Lubuntu Noble Numbat (development branch) x86_64 
Host: OptiPlex 7050 
Kernel: 6.5.0-10-generic 
Uptime: 6 days, 18 hours, 39 mins 
Packages: 3386 (dpkg), 20 (snap) 
Shell: bash 5.2.21 
Resolution: 1920x1080, 1920x1080, 1920x1080, 1280x1024, 1280x1024 
DE: LXQt 1.4.0 
WM: Xfwm4 
WM Theme: Pills 
Theme: Greybird [GTK2/3] 
Icons: oxygen [GTK2/3] 
Terminal: qterminal 
Terminal Font: IBM Plex Mono Text 14 
CPU: Intel i5-6500 (4) @ 3.600GHz 
GPU: AMD ATI Radeon HD 5000/6000/7350/8350 Series 
GPU: Intel HD Graphics 530 
Memory: 8772MiB / 15842MiB 

```

If however I switch to root user; the result differs

```

root@d7050-next:~#   neofetch --off
root@d7050-next 
--------------- 
OS: Ubuntu Noble Numbat (development branch) x86_64 
Host: OptiPlex 7050 
Kernel: 6.5.0-10-generic 
Uptime: 6 days, 18 hours, 40 mins 
Packages: 3386 (dpkg), 20 (snap) 
Shell: bash 5.2.21 
Resolution: 1920x1080, 1920x1080, 1920x1080, 1280x1024, 1280x1024 
DE: LXQt 1.4.0 
WM: Xfwm4 
Theme: Arc-Darker [GTK3] 
Icons: elementary-xfce-dark [GTK3] 
Terminal: qterminal 
CPU: Intel i5-6500 (4) @ 3.600GHz 
GPU: AMD ATI Radeon HD 5000/6000/7350/8350 Series 
GPU: Intel HD Graphics 530 
Memory: 8764MiB / 15842MiB 

```

As already stated, I consider my Lubuntu system a Ubuntu system, so I'm never worried when tools report it as Ubuntu; as a huge proportion of my system are packages from the main repository; ie. Ubuntu, with only a small portion being from universe or community supported (which includes the Lubuntu & other flavor team packages).

Tools like `neofetch` detect the system as Ubuntu naturally, then have other code that attempts to detect when *flavors* are being used and change the Ubuntu to the *flavor* as that's what many users want to see, eg.

```

            if [[ $distro == "Ubuntu"* ]]; then
                case $XDG_CONFIG_DIRS in
                    *"plasma"*)   distro=${distro/Ubuntu/Kubuntu} ;;
                    *"mate"*)     distro=${distro/Ubuntu/Ubuntu MATE} ;;
                    *"xubuntu"*)  distro=${distro/Ubuntu/Xubuntu} ;;
                    *"Lubuntu"*)  distro=${distro/Ubuntu/Lubuntu} ;;
                    *"budgie"*)   distro=${distro/Ubuntu/Ubuntu Budgie} ;;
                    *"studio"*)   distro=${distro/Ubuntu/Ubuntu Studio} ;;
                    *"cinnamon"*) distro=${distro/Ubuntu/Ubuntu Cinnamon} ;;
                esac

```

so if you've made changes to some defaults (XDG_CONFIG_DIRS for example here, which Lubuntu only configure for the default user, not root) the *flavor* may not be detected by apps coding (`neofetch` in this example), with what the OS actually is (***a Ubuntu system***) only being detected.  My 2c.

---

### Post by #&amp;thj^% on 2023-12-26
> **guiverc said:**
> If I run `neofetch` using my normal account, I get the following

```

guiverc@d7050-next:~/uwn/issues/819$   neofetch --off
guiverc@d7050-next 
------------------ 
OS: Lubuntu Noble Numbat (development branch) x86_64 
Host: OptiPlex 7050 
Kernel: 6.5.0-10-generic 
Uptime: 6 days, 18 hours, 39 mins 
Packages: 3386 (dpkg), 20 (snap) 
Shell: bash 5.2.21 
Resolution: 1920x1080, 1920x1080, 1920x1080, 1280x1024, 1280x1024 
DE: LXQt 1.4.0 
WM: Xfwm4 
WM Theme: Pills 
Theme: Greybird [GTK2/3] 
Icons: oxygen [GTK2/3] 
Terminal: qterminal 
Terminal Font: IBM Plex Mono Text 14 
CPU: Intel i5-6500 (4) @ 3.600GHz 
GPU: AMD ATI Radeon HD 5000/6000/7350/8350 Series 
GPU: Intel HD Graphics 530 
Memory: 8772MiB / 15842MiB 

```

If however I switch to root user; the result differs

```

root@d7050-next:~#   neofetch --off
root@d7050-next 
--------------- 
OS: Ubuntu Noble Numbat (development branch) x86_64 
Host: OptiPlex 7050 
Kernel: 6.5.0-10-generic 
Uptime: 6 days, 18 hours, 40 mins 
Packages: 3386 (dpkg), 20 (snap) 
Shell: bash 5.2.21 
Resolution: 1920x1080, 1920x1080, 1920x1080, 1280x1024, 1280x1024 
DE: LXQt 1.4.0 
WM: Xfwm4 
Theme: Arc-Darker [GTK3] 
Icons: elementary-xfce-dark [GTK3] 
Terminal: qterminal 
CPU: Intel i5-6500 (4) @ 3.600GHz 
GPU: AMD ATI Radeon HD 5000/6000/7350/8350 Series 
GPU: Intel HD Graphics 530 
Memory: 8764MiB / 15842MiB 

```

As already stated, I consider my Lubuntu system a Ubuntu system, so I'm never worried when tools report it as Ubuntu; as a huge proportion of my system are packages from the main repository; ie. Ubuntu, with only a small portion being from universe or community supported (which includes the Lubuntu & other flavor team packages).

Tools like `neofetch` detect the system as Ubuntu naturally, then have other code that attempts to detect when *flavors* are being used and change the Ubuntu to the *flavor* as that's what many users want to see, eg.

```

            if [[ $distro == "Ubuntu"* ]]; then
                case $XDG_CONFIG_DIRS in
                    *"plasma"*)   distro=${distro/Ubuntu/Kubuntu} ;;
                    *"mate"*)     distro=${distro/Ubuntu/Ubuntu MATE} ;;
                    *"xubuntu"*)  distro=${distro/Ubuntu/Xubuntu} ;;
                    *"Lubuntu"*)  distro=${distro/Ubuntu/Lubuntu} ;;
                    *"budgie"*)   distro=${distro/Ubuntu/Ubuntu Budgie} ;;
                    *"studio"*)   distro=${distro/Ubuntu/Ubuntu Studio} ;;
                    *"cinnamon"*) distro=${distro/Ubuntu/Ubuntu Cinnamon} ;;
                esac

```

so if you've made changes to some defaults (XDG_CONFIG_DIRS for example here, which Lubuntu only configure for the default user, not root) the *flavor* may not be detected by apps coding (`neofetch` in this example), with what the OS actually is (***a Ubuntu system***) only being detected.  My 2c.

Makes perfect sense now, Thx guiverc ;)

---

### Post by guiverc on 2023-12-26
> **1fallen said:**
> Makes perfect sense now, Thx guiverc ;)

Sorry, that reply was more for Regexaurus; intended to *clarify* or *amplify* what I'd said in prior message...  That was my intention anyway.

I edited prior message and added quote there.

---

### Post by MAFoElffen on 2023-12-26
I like that,
```

            if [[ $distro == "Ubuntu"* ]]; then
                case $XDG_CONFIG_DIRS in
                    *"plasma"*)   distro=${distro/Ubuntu/Kubuntu} ;;
                    *"mate"*)     distro=${distro/Ubuntu/Ubuntu MATE} ;;
                    *"xubuntu"*)  distro=${distro/Ubuntu/Xubuntu} ;;
                    *"Lubuntu"*)  distro=${distro/Ubuntu/Lubuntu} ;;
                    *"budgie"*)   distro=${distro/Ubuntu/Ubuntu Budgie} ;;
                    *"studio"*)   distro=${distro/Ubuntu/Ubuntu Studio} ;;
                    *"cinnamon"*) distro=${distro/Ubuntu/Ubuntu Cinnamon} ;;
                esac
```
But there is a problem with the logic of that:
```

mafoelffen@Mikes-ThinkPad-T520:~$ echo $XDG_CONGIG_DIRS


```
Above is "null". Many times that VAR is not populated.

Just an idea... When i am looking at things... Many desktops can be installed after an install. I found that out with working on the Ama-Gi Project where I would try to identify what something was, not just for Ubuntu, but for other Distro's. Installing other DE's will throw that all off.

But for Debian Branch Distro's, as a general rule, this never changes. If it was installed from an ISO image (not a pre-installed image):
```

sudo head -n 1 /var/log/installer/media-info

```
Or.. comparing different ways, for example
```

mafoelffen@Mikes-ThinkPad-T520:~$ grep -m1 . /var/log/installer/media-info
Ubuntu 20.04.3 LTS "Focal Fossa" - Release amd64 (20210819)

mafoelffen@Mikes-ThinkPad-T520:~$ gsettings get org.gnome.desktop.interface gtk-theme
'Prof-Gnome-Dark-3.6'

mafoelffen@Mikes-ThinkPad-T520:~$ lsb_release -d
Description:    Ubuntu 22.04.3 LTS

mafoelffen@Mikes-ThinkPad-T520:~$ neofetch --off
mafoelffen@Mikes-ThinkPad-T520 
------------------------------ 
OS: Ubuntu 22.04.3 LTS x86_64 
Host: 4242C29 ThinkPad T520 
Kernel: 6.2.0-37-generic 
Uptime: 4 days, 10 hours, 16 mins 
Packages: 3109 (dpkg), 17 (snap) 
Shell: bash 5.1.16 
Resolution: 1920x1080 
DE: GNOME 42.9 
WM: Mutter 
WM Theme: Yaru-dark 
Theme: Prof-Gnome-Dark-3.6 [GTK2/3] 
Icons: Adwaita [GTK2/3] 
Terminal: gnome-terminal 
CPU: Intel i7-2760QM (8) @ 3.500GHz 
GPU: NVIDIA Quadro NVS 4200M 
GPU: Intel 2nd Generation Core Processor Family 
Memory: 5851MiB / 7811MiB 

```
Just a thought... But am I confused in that all that has little to do with the OP's post #1?

*** Where he is looking for help in diagnosing a random crash? Are any of these logs or snippets of it available on a pastebin somewhere?

---

### Post by Regexaurus on 2023-12-31
Admittedly the question about Ubuntu flavor is something of a diversion. I am mainly interested in trying to post with correct tags, but also curious how I might have switched from Lubuntu to Ubuntu "base". Output below is from running commands as a normal, non-root user, and not using sudo.

**tac /etc/os-release**
```
UBUNTU_CODENAME=jammy
PRIVACY_POLICY_URL="https://www.ubuntu.com/legal/terms-and-policies/privacy-policy"
BUG_REPORT_URL="https://bugs.launchpad.net/ubuntu/"
SUPPORT_URL="https://help.ubuntu.com/"
HOME_URL="https://www.ubuntu.com/"
ID_LIKE=debian
ID=ubuntu
VERSION_CODENAME=jammy
VERSION="22.04.3 LTS (Jammy Jellyfish)"
VERSION_ID="22.04"
NAME="Ubuntu"
PRETTY_NAME="Ubuntu 22.04.3 LTS"
```

**neofetch --off**
```
OS: Ubuntu 22.04.3 LTS x86_64Host: $(DEFAULT_STRING) $(DEFAULT_STRING)
Kernel: 6.2.0-39-generic
Uptime: 7 hours, 17 mins
Packages: 1905 (dpkg), 9 (snap)
Shell: bash 5.1.16
Resolution: 3840x2160
Terminal: /dev/pts/0
CPU: Intel Atom x5-Z8350 (4) @ 1.920GHz
GPU: Intel Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx
Memory: 1033MiB / 7861MiB

```

---

### Post by MAFoElffen on 2023-12-31
> **Regexaurus said:**
> 
**neofetch --off**
```
OS: Ubuntu 22.04.3 LTS x86_64Host: $(DEFAULT_STRING) $(DEFAULT_STRING)
Kernel: 6.2.0-39-generic
Uptime: 7 hours, 17 mins
Packages: 1905 (dpkg), 9 (snap)
Shell: bash 5.1.16
Resolution: 3840x2160
Terminal: /dev/pts/0
[COLOR=#ff0000]CPU: Intel Atom x5-Z8350 (4) @ 1.920GHz
GPU: Intel Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx
Memory: 1033MiB / 7861MiB[/COLOR]

```
I see lots of crashes out there for this CPU trying to run Linux on heavy distro's. If a flavor of Ubuntu, yes Lubuntu would be the choice to stay with... Being very careful of what you try to run on top of that.

I hate to say this, but I have seen Raspberry Pi4's (and similar's) run better than this type of system.

It has very limited resources and capabilities. When the resources runs out, it is known that on this system, it (commonly) crashes with kernel panic.

So suspected, it is running out of system resources. Some say that CPU is maxed out at 2GB of RAM. IDK personally. I can only go off what others have said about it. I don't have that CPU in my test suite. It is just what it is, and the nature of the beast.

My suggestion would be to run the System Monitor and watch your resources closely. Watch what you run, and how many browser tabs you have open at a time. Watch how many applications you have open concurrently at the same time.

---

### Post by Regexaurus on 2023-12-31
> **MAFoElffen said:**
> ...So suspected, it is running out of system resources...Watch what you run, and how many browser tabs you have open at a time. Watch how many applications you have open concurrently at the same time.

The systems run RiseVision media player for digital signage, as my original post indicates. That's it, besides system processes. No browser or other applications. Also, as mentioned in my first post, I have 3 of these systems, and 2 of them run reliably. It's only one of the systems that sometimes apparently crashes. All 3 display similar content, mostly text and some background and still image graphics. No video or audio. The systems originally came with Windows 10 S. They ran just OK, but updates took annoyingly long to apply. Moving to Lubuntu seemed to substantially improve performance.

---

### Post by MAFoElffen on 2023-12-31
Windows "S" is a minimal resource version of Windows, meant for minimal hardware. But that is a distraction with this. It is running fine on your other two systems on Lubuntu.

I think we should compare the 3 systems and see what might be different on this one system.

The easiest way I can figure out how to possibly see that it to run the 'system-info' script (in my signature line) on all three, and upload all 3 to pastebins. That way we can compare all 3 reports, side by side, line by line...

---

### Post by Regexaurus on 2024-01-04
> **MAFoElffen said:**
> ...The easiest way I can figure out how to possibly see that it to run the 'system-info' script (in my signature line) on all three, and upload all 3 to pastebins. That way we can compare all 3 reports, side by side, line by line...

Edit: I just realized that Pastebin folders are visible only to users on their own Pastebin account. I had made the 3 unlisted posts, all in the same folder, and shared (in this response, before edit) the folder URL.
Here are links to the 3 posts:
[Compute stick with problem]("https://pastebin.com/YwGcXPTB")
[Compute stick healthy 1]("https://pastebin.com/FD6gkwgY")
[Compute stick healthy 2]("https://pastebin.com/8wF7J7L5")

---

### Post by wyattwhiteeagle on 2024-05-08
For me, neofetch shows...
```
OS: Lubuntu 22.04.4 LTS x86_64
```

---

