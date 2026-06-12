---
title: "Ubuntu 23.04 -- login not possible using &quot;Ubuntu on Xorg&quot;"
date: 2023-04-21
forum: General Help
---

### Post by Dennis N on 2023-04-21
I installed the just released Ubuntu 23.04 on two QEMU/KVM virtual machines, each on a different computer.

on computer 1: I did a new install from the ISO of the release.
on computer 2: I did an upgrade of 22.10 using Software Updater.

On both, the installation was successful, but after installing, in both cases, attempting to log in using "Ubuntu on Xorg" fails - instead, I get a brief screen blank and a return to the log in screen. If I select "Ubuntu" (Wayland) for my log in, it's successful.

Any ideas why an Xorg session is no longer starting and Wayland is working?

---

### Post by #&amp;thj^% on 2023-04-21
I'm guessing it's because Ubuntu 23.04 runs Wayland by default, and is installed to handle Wayland over X11/Xorg. Wayland essentially handles all the GFX stuff, in laymans terms, which would explain why Xorg isn't working as well in Ubuntu 22.04.

awhile back I was able to open "Settings" and select "About" , and where it read Windowing System i was then able to use an X11 after these 2 commands:
One by One:
```
sudo cp /etc/environment /etc/environment.back
```
and:
```
sudo cp /etc/gdm3/custom.conf /etc/gdm3/custom.conf.back
```

If you need to reverse use:
```

sudo mv /etc/environment.back /etc/environment
```
and:
```

sudo mv /etc/gdm3/custom.conf.back /etc/gdm3/custom.conf
```
I'm curious if this still work Dennis N
NO MORE Gnome for me :P

---

### Post by Dennis N on 2023-04-21
After posting, I have looked at the Xorg.0.log file. I'm no expert on analyzing log files, but from what's there, I see an xorg-server fatal server error logged:

exerpt from Xorg.0.log:

```
Fatal server error:
[   205.500] (EE) Caught signal 6 (Aborted). Server aborting
[   205.500] (EE) 
[   205.500] (EE) 
Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
[   205.500] (EE) Please also check the log file at "/home/dmn/.local/share/xorg/Xorg.0.log" for additional information.
[   205.500] (EE) 
[   205.504] (EE) Server terminated with error (1). Closing log file.
```
End of log.

This could be the problem.

---

### Post by #&amp;thj^% on 2023-04-21
Dennis N is this after my suggestions???
See if the same info shows with:
```
cat /home/dmn/.local/share/xorg/Xorg.0.log >xorg-log.txt
```

---

### Post by Dennis N on 2023-04-21
The output in post #3 was before the commands. After running the commands, I restarted and found that the commands had no effect on logging into Xorg session. The same error message (below) is at the end of the log (this time I used the other machine from that of the previous post).

```
Fatal server error:
[    49.676] (EE) Caught signal 6 (Aborted). Server aborting
[    49.676] (EE) 
[    49.676] (EE) 
Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
[    49.677] (EE) Please also check the log file at "/home/dmn/.local/share/xorg/Xorg.0.log" for additional information.
[    49.677] (EE) 
[    49.681] (EE) Server terminated with error (1). Closing log file. 
```

I may try a non-vm install to see if that might work, but I doubt it. Most people probably use the default login option, and would not notice this problem.

---

### Post by tea for one on 2023-04-22
> **Dennis N said:**
> I may try a non-vm install to see if that might work, but I doubt it. Most people probably use the default login option, and would not notice this problem.
Ubuntu 23.04 non-vm allows the user to log-in both Wayland and Xorg sessions.

---

### Post by Dennis N on 2023-04-22
> **tea for one said:**
> Ubuntu 23.04 non-vm allows the user to log-in both Wayland and Xorg sessions.

Thanks for the information. I already have a 22.10 non-vm installation, so I expect upgrading it with Software Updater should continue to allow the Xorg logins.

---

### Post by tea for one on 2023-04-22
I should have mentioned that I did a clean installation using an Ubuntu 23.04 iso, not an upgrade.

---

### Post by Dennis N on 2023-04-22
> **tea for one said:**
> I should have mentioned that I did a clean installation using an Ubuntu 23.04 iso, not an upgrade.

O.K, It will have to be upgraded in any case before it goes out-of-support, so no harm in trying. If it fails after an upgrade attempt, then I would do a new install.

---

### Post by #&amp;thj^% on 2023-04-22
> **Dennis N said:**
> O.K, It will have to be upgraded in any case before it goes out-of-support, so no harm in trying. If it fails after an upgrade attempt, then I would do a new install.

Let me save you some time:
Fresh install not an upgrade, 
```
apt list --upgradable
Listing... Done
python3-distupgrade/lunar-updates 1:23.04.6 all [upgradable from: 1:23.04.5]
ubuntu-release-upgrader-core/lunar-updates 1:23.04.6 all [upgradable from: 1:23.04.5]
ubuntu-release-upgrader-gtk/lunar-updates 1:23.04.6 all [upgradable from: 1:23.04.5]
```

As far as the session goes :
```
ls /usr/bin/*session
/usr/bin/dbus-run-session  /usr/bin/gnome-session

```

Now it gets fun, what session is used?
```
loginctl show-session 2 -p Type      
Failed to get session path: No session '2' known

```
I've filed bugs on ubuntu-bug xiccd
and ubuntu-bug x11
I feel this might also include xwayland, but not enough info to *not* send developers on a rodeo.
Here is what I've found and filed against ATM:
```
_usr_bin_gnome-shell.1000.crash     _usr_bin_xfsettingsd.1000.crash
_usr_bin_gnome-shell.1000.upload    _usr_bin_xiccd.1000.crash
_usr_bin_gnome-shell.1000.uploaded  _usr_lib_xorg_Xorg.1000.crash

```
Even if I install another DE (XFCE4) it bounces me to login>>>No X11 sessions work.
EDIT: I would include a link on the bugs, but I've pissed popey off :P
```

Oops!

Sorry, something just went wrong in Launchpad.

We&#8217;ve recorded what happened, and we&#8217;ll fix it as soon as possible. Apologies for the inconvenience.

If you can't login, join us on #launchpad IRC channel at irc.libera.chat, e-mail us or visit our feedback page.

If you report this as a bug, please include the error ID below, preferably by copying and pasting it rather than by taking a screenshot.

(Error ID: OOPS-85006b81ed205464ed4c43a502d2cb89)

    Provide feedback or report a bug
    Return to the Launchpad front page


```

---

### Post by tea for one on 2023-04-22
@Dennis N
I've just installed Ubuntu 23.04 in [COLOR="#0000FF"]UEFI[/COLOR] mode in a VM using Qemu/KVM.
Both Wayland and Xorg were available and log-in was successful each time.

---

### Post by #&amp;thj^% on 2023-04-22
> **tea for one said:**
> @Dennis N
I've just installed Ubuntu 23.04 in [COLOR="#0000FF"]UEFI[/COLOR] mode in a VM using Qemu/KVM.
Both Wayland and Xorg were available and log-in was successful each time.

My install .iso was only 2 days old, could you show me the link to your down load.

---

### Post by tea for one on 2023-04-22
> **1fallen said:**
> My install .iso was only 2 days old, could you show me the link to your down load.
Mine also two days ago - direct (not torrent) from [https://ubuntu.com/download/desktop](https://ubuntu.com/download/desktop).
New installer _not_ Legacy Desktop Installer

---

### Post by #&amp;thj^% on 2023-04-22
> **tea for one said:**
> Mine also two days ago - direct (not torrent) from [https://ubuntu.com/download/desktop](https://ubuntu.com/download/desktop).
New installer _not_ Legacy Desktop Installer

Yes Sir, the wrong .iso, whoosh i worried for about a split second. LOL
 Dennis N and I are working with 23.04 and not 22.04, but i agree both X11 and wayland logins work on 22.04
EDIT: BTW I see both listed there but this is the .iso I've been working: [https://releases.ubuntu.com/lunar/](https://releases.ubuntu.com/lunar/)

---

### Post by tea for one on 2023-04-22
I am using Ubuntu 23.04 from the page I linked.

---

### Post by #&amp;thj^% on 2023-04-22
> **tea for one said:**
> I am using Ubuntu 23.04 from the page I linked.
Yes i saw that, try my link and report back please. 	2023-04-18 21:06 
And yes UEFI and the new installer used for the install.(KVM)

---

### Post by Dennis N on 2023-04-22
> **tea for one said:**
> @Dennis N
I've just installed Ubuntu 23.04 in [COLOR="#0000FF"]UEFI[/COLOR] mode in a VM using Qemu/KVM.
Both Wayland and Xorg were available and log-in was successful each time.

I also used UEFI on both of those VMs. See the screenshot of the new install overview screen. Do you see anything there that might be problemic? These are settings I have always used. I am baffled. 

I thought it might be the video, but switching to QXL or even VGA did not matter.

One thing: I don't use qcow2 file as the storage - instead I am using an LV as the storage volume. But the OS installation was a standard install onto partitions. This has been working well in the past.

As to the two iso versions, I have tried both of them. No difference except the installer itself.

One more thing: The host of these QEMU/KVM is not Ubuntu. Its Manjaro Gnome. Now I wonder if that could make any difference, but I doubt it.

---

### Post by #&amp;thj^% on 2023-04-22
Just my 2 cents i see the same as you show with Ubuntu as the host.
EDIT: and just now purged all gnome-shell and gnome and I now can use a X11 session.
```
cat /etc/os-release
PRETTY_NAME="Ubuntu 23.04"
NAME="Ubuntu"
VERSION_ID="23.04"
VERSION="23.04 (Lunar Lobster)"
VERSION_CODENAME=lunar
ID=ubuntu
ID_LIKE=debian
HOME_URL="https://www.ubuntu.com/"
SUPPORT_URL="https://help.ubuntu.com/"
BUG_REPORT_URL="https://bugs.launchpad.net/ubuntu/"
PRIVACY_POLICY_URL="https://www.ubuntu.com/legal/terms-and-policies/privacy-policy"
UBUNTU_CODENAME=lunar
LOGO=ubuntu-logo

```

---

### Post by sudodus on 2023-04-22
Maybe it works better in the VMs with Ubuntu 23.04 from **[FONT=Courier New]	lunar-preinstalled-server-amd64.img.xz[/FONT]** (where you can install **[FONT=Courier New]ubuntu-desktop[/FONT]** or some community flavour desktop afterwards). 

See [this link](https://ubuntuforums.org/showthread.php?t=2474692) and [cdimage.ubuntu.com/ubuntu-server/daily-preinstalled/current/](http://cdimage.ubuntu.com/ubuntu-server/daily-preinstalled/current/)

---

### Post by tea for one on 2023-04-22
> **1fallen said:**
> And yes UEFI and the new installer used for the install.(KVM)
Your 23.04 iso and mine seem to be the same.
I've just run the sha256sum on mine and the result is:-
```
a8cd6ccff865e17dd136658f6388480c9a5bc57274b29f7d5bd0ed855a9281a5  ubuntu-23.04-desktop-amd64.iso
```

---

### Post by tea for one on 2023-04-22
> **Dennis N said:**
> I also used UEFI on both of those VMs. See the screenshot of the new install overview screen. Do you see anything there that might be problemic? These are settings I have always used. I am baffled. 
I thought it might be the video, but switching to QXL or even VGA did not matter.
One thing: I don't use qcow2 file as the storage - instead I am using an LV as the storage volume. But the OS installation was a standard install onto partitions. This has been working well in the past.
As to the two iso versions, I have tried both of them. No difference except the installer itself.
One more thing: The host of these QEMU/KVM is not Ubuntu. Its Manjaro Gnome. Now I wonder if that could make any difference, but I doubt it.

My host is Ubuntu 22.04 (gnome 42.5 Wayland session).
I use qcow2 as storage
4096MiB memory
The Ubuntu 23.04 VM installation used default options other than my UEFI mode choice.

I notice that you are baffled and #metoo ;)

Just out of curiosity, is it important for you to have access to both Xorg and Wayland in a VM?

---

### Post by #&amp;thj^% on 2023-04-22
> **tea for one said:**
> Your 23.04 iso and mine seem to be the same.
I've just run the sha256sum on mine and the result is:-
```
a8cd6ccff865e17dd136658f6388480c9a5bc57274b29f7d5bd0ed855a9281a5  ubuntu-23.04-desktop-amd64.iso
```

Well they are not the same, your link works fine for both X11 and wayland, the link i show flops on X11 anything.

---

### Post by Dennis N on 2023-04-22
> **tea for one said:**
> My host is Ubuntu 22.04 (gnome 42.5 Wayland session).
I use qcow2 as storage
4096MiB memory
The Ubuntu 23.04 VM installation used default options other than my UEFI mode choice.
I notice that you are baffled and #metoo ;)
Just out of curiosity, is it important for you to have access to both Xorg and Wayland in a VM?

Here's what I did:

I decided to use Software Updater and try updating my existing Ubuntu 22.10 (a non-vm LVM install) to 23.04 and the resulting 23.04 is working with the "Ubuntu on Xorg" selection so I was happy with this. The problem may be restricted to VMs, not regular installations. I'm keeping the 22.10 &#8594; 23.04 VM upgrade that was done with Software Updater - who knows, Xorg may start working again with 23.10.   

As to wanting Xorg available in the VMs is because of two things: 1) the Ubuntu dock can't be set to autohide because once it's hidden, you can't access it over a full screen application like Firefox - it refuses to appear. With Xorg, I can install Plank in an Xorg session, and it autohides correctly in VMs (and once themed, looks nice too)  and 2) I like to have amazing screensavers on my computers and Xscreensaver will not work with Wayland - only with Xorg. Check out some of the rss-glx screensavers if you never have. 

When time permits, I will test other VM install options and see if (less exotic) choices still work with Xorg. My current VM install options may be at fault, but have worked up to now. 
 
Anyway, I'm glad you commented (in post #6) that the regular install still worked with Xorg - that led me to try that.

---

### Post by Dennis N on 2023-04-22
They have two isos accessible to the public, without explaining the difference anywhere I could see. The bigger one (4.6G) uses the new installer, which I found was easy to use. I am wondering if it allows the user to choose the EFI system partition you want to use when you have more than one. That would be nice. Also, I noticed choosing LVM now requires a separate boot partition even when not encrypting. The old installer did not.

And thanks to all commenters for your ideas and observations.

---

### Post by Dennis N on 2023-04-23
Update:

Tested 3 other install options in a VM:

1) qcow2 storage - UEFI mode - Default Erase disk and install Ubuntu 
2) qcow2 storage - UEFI mode - Choose the LVM install option and install Ubuntu
3) LV storage - BIOS mode - Default Erase disk and install Ubuntu

All these failed just as the original examples in post #1 when selecting the "Ubuntu on Xorg" session. All 3 of these tests work when "Ubuntu" (Wayland) is used as the session.

Conclusion: The installation method is probably not the problem.

---

### Post by #&amp;thj^% on 2023-04-23
> **Dennis N said:**
> Update:

Tested 3 other install options in a VM:

1) qcow2 storage - UEFI mode - Default Erase disk and install Ubuntu 
2) qcow2 storage - UEFI mode - Choose the LVM install option and install Ubuntu
3) LV storage - BIOS mode - Default Erase disk and install Ubuntu

All these failed just as the original examples in post #1 when selecting the "Ubuntu on Xorg" session. All 3 of these tests work when "Ubuntu" (Wayland) is used as the session.

Conclusion: The installation method is probably not the problem.
+1
I filed 3 bugs yesterday:
```
_usr_bin_gnome-shell.1000.crash     _usr_bin_xfsettingsd.1000.crash
_usr_bin_gnome-shell.1000.upload    _usr_bin_xiccd.1000.crash
_usr_bin_gnome-shell.1000.uploaded  _usr_lib_xorg_Xorg.1000.crash
```
That's just from an attempt on Xorg

---

### Post by comyivio on 2023-06-06
I had the same problem with Ubuntu 23.04 VM in Virtual Box 7.0.  The solution that made things work for me was to enable 3D acceleration for the VM.

---

### Post by MAFoElffen on 2023-06-06
IDK. See attached.

KVM on Ubuntu 22.04 Host. Lunar 23.04. Desktops come up in all those DE's and Graphics Engines.

That was not installed via the installer ISO, but manually, using Try and debootstrap.

I have others that Installed from the aplha and beta (pre-release) daily ISO's that still boot all modes.

I have one after-release 23.04 VM that boots all modes.

Not sure what is different on mine. Maybe the Host system??? But mine are across three KVM Hosts-- Two with Intel CPU and one with AMD(??? albiet an older Opteron 6420 SE)

---

### Post by redbearak on 2023-09-19
I had this problem months ago with Ubuntu 23.04 shortly after release, and gave up on trying to figure out how to use the X11/Xorg session in a VM without it crashing back to the login screen. 

Just installed a new VM yesterday with Ubuntu 23.04 from the same ISO and applied all available updates. Once again ran into the X11/Xorg problem, while Wayland sessions work fine. 

This is in a QEMU/KVM virtual machine created with `virt-manager`. 

Based on some clues from the earlier posts in this thread, here's what got it working for me: 

- Changing the video driver from "QXL" to "Virtio"
- Enabling 3D acceleration
- (Click "Apply")
- Enabling OpenGL in the "Display Spice" tab
- Setting "Listen type" to "None" (same tab)
- (Click "Apply" again)

With these changes you should be able to boot up and log into an X11/Xorg session. For me it defaulted to 1280x800 resolution. 

GNOME Boxes doesn't allow this kind of control unless you know how to manually edit the XML files and redefine the VM in the terminal with `virsh`. I'm using `virt-manager` to get access to more settings in the GUI.

Edit: The host is openSUSE Tumbleweed running on a 2011 iMac 27-inch, and I chose the AMD option in the "Display Spice" tab for OpenGL.

---

### Post by Dennis N on 2023-09-19
> With these changes you should be able to boot up and log into an X11/Xorg session. For me it defaulted to 1280x800 resolution. 

Thanks for your reply. 

I'm impressed. These settings do allow a log in to Xorg session. I had wanted to enable graphical acceleration in the past but I think the option was not available. The same might be true for OpenGL option. I have another computer with some older version of the virtualization  software and will check on this. 

I will look further at the performance, but a quick check of video stream: YouTube video looks good with CPU at 40% with integrated graphics using a not-that-recent Intel i3 gen 8 processor.  

Host: Fedora Workstation 38
Virt Manager version 4.1.0
Guest: Ubuntu 23.04 installed in UEFI mode.

---------------------------------------------------------
Update: The other virt-manager is 3.2.0 and it also works with these settings. In both cases, I think what I was missing was setting the "Display Spice" correctly.

---

