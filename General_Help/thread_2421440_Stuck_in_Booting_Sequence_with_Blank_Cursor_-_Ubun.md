---
title: "Stuck in Booting Sequence with Blank Cursor - Ubuntu 19.04"
date: 2019-06-21
forum: General Help
---

### Post by ne5552 on 2019-06-21
Hello everyone!

Just installed Ubuntu 19.04 on my Dell XPS 15 9560. Everything worked fine so I went on installing [Regolith]("https://regolith-linux.org/") as a desktop session. Battery life was around 1h, but that I already knew coming from [Elementary OS]("https://elementary.io/"). Not usable for a laptop, so I tried some power saving options:


[LIST=1]
[*]powertop: no problems there; toggled everything from "bad" to "good";
[*]pm-utils: installed it and ran ```
pm-powersave true
```;
[*]laptop-mode-tools: installed it and created a hook like described in [this article on power saving]("https://help.ubuntu.com/community/PowerManagement/ReducedPower");
[*]restarted pm-powersave by toggling true>false>true;
[*]looked back at powertop, but now all entries were listed as "bad";
[*]installed bumblebee as described in [this article]("https://wiki.ubuntu.com/Bumblebee#Installation");
[*]closed the machine, because I had to get groceries;
[*]as I reopened my laptop, the login screen wouldn't show up; => I had to shut it down hard;
[*]booting it up doesn't work anymore;
[/LIST]

The bumblebee install finished, so I don't have a corrupt installation. I don't have any idea what I could do to get around this, besides going for a fresh install.

I am using LVM to encrypt my drive.

I heard about an issue with the Dell XPS line and bumblebee [here]("https://www.reddit.com/r/Dell/comments/63cavx/fixed_nvidia_1050_freezing_in_ubuntu_linux/"). But the people reporting this issue only see the problem when they are switching between graphics cards.

I tried to get into the grub screen by either using the shift or the esc keys, but nothing worked for me. To better show you whats going on, I made [a video of the boot sequence]("https://www.youtube.com/watch?v=PZ1LXjkVYTk"). (Sorry that it's in portrait mode, but I wanted to get all the messages in frame.)

The first thing that popped into my eyes was the warning: ```
Cannot process volume group ubuntu-vg
```. Someone answered himself and suggests a kernel update [here]("https://askubuntu.com/questions/1040554/volume-group-ubuntu-vg-not-found"). But I don't think that this is the problem.

Best Regards,
Nico

---

### Post by oldfred on 2019-06-21
Have you updated UEFI from Dell and SSD firmware (if SSD?).

Bumblebee may not be required with nVidia Optimus which is installed automatically with newest nVidia driver.
Bumblebee has been depreciated in favor of nvidia-prime
Bumblebee - allows both nVidia & Intel to be used, nVidia Prime was just nVidia, but now updated: 
Some of your links are now old, and things have changed.
Others with same system:
      
 Dell XPS 13 9560 install without issues
[https://ubuntuforums.org/showthread.php?t=2357321](https://ubuntuforums.org/showthread.php?t=2357321)
[https://wiki.archlinux.org/index.php/Dell_XPS_15_9560](https://wiki.archlinux.org/index.php/Dell_XPS_15_9560)
[https://askubuntu.com/questions/1043842/running-ubuntu-via-live-usb-error-on-dell-xps-15-9560](https://askubuntu.com/questions/1043842/running-ubuntu-via-live-usb-error-on-dell-xps-15-9560)

---

### Post by ne5552 on 2019-06-21
Thank you!

After Ubuntus fresh install it asked me to do a UEFI update and I did. But I was able to shutdown the machines (and start it again) a couple of times.

Okay, so you would recommend a fresh install and try it out again without bumblebee but with nvidia prime?

One more question: The [Archlinux wiki page]("https://wiki.archlinux.org/index.php/Dell_XPS_15_9560#Disable_discrete_GPU") states that in order to cut the power consumption you can/should use bbswitch, but you clearly said that it it deprecated. So installing the nvidia prime package should cut down the power consumption?

I'll get a live usb stick and do a [boot repair]("https://help.ubuntu.com/community/Boot-Repair"), if that doesn't help, I'll go for the new install.

Best regards,
Nico

---

### Post by ne5552 on 2019-06-21
Okay so boot-repair coudn't solve the issue (even though it says "[COLOR=#000000]Boot successfully repaired." in the log file[/COLOR]). Here is the output from [pastebin]("https://paste.ubuntu.com/p/K56nnzg98J/").

---

### Post by oldfred on 2019-06-21
Do not know LVM with encryption.
But generally you have to mount the LVM &  decrypt the partition for Boot-Repair to work.
Boot-Repair will not fix video issues.

You should be able to purge & reinstall nVidia.
       If wrong nVidia driver or upgrade, you must purge & install correct driver
[https://ubuntuforums.org/showthread.php?t=2362351&p=13649946#post13649946](https://ubuntuforums.org/showthread.php?t=2362351&p=13649946#post13649946)
[https://ubuntuforums.org/showthread.php?t=2380061](https://ubuntuforums.org/showthread.php?t=2380061)
[URL="https://ubuntuforums.org/showthread.php?t=2362351"]https://ubuntuforums.org/showthread.php?t=2362351

      [/URL]
 If you have installed any version, you must purge first, old will conflict with new as new install does not overwrite old version.
sudo apt-get remove --purge nvidia-*
sudo apt-get purge nvidia* bumblebee primus bbswitch-dkms
This xorg file may not exist, so if error that would be ok
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup 
    [URL="https://ubuntuforums.org/showthread.php?t=2362351"]
[/URL]

---

### Post by ne5552 on 2019-06-23
Okay, so I just re-installed Ubuntu. I did similar steps as before:

1) fresh install of Ubuntu 19.04 without LVM (and encrypted drive)
2) installed recommended updates
3) sudo ubuntu-drivers autoinstall
4) sudo apt autoremove
5) sudo apt install powertop
6) sudo powertop => "bad" --> "good"
7) sudo apt install pm-utils
8) sudo pm-powersave true
9) created hook at /usr/lib/pm-utils/power.d/hook_lesswatts_org
10) sudo chmod a+x hook_lesswatts_org
11) sudo pm-powersave false
12) sudo pm-powersave true
13) sudo apt install laptop-mode-tools

After putting my laptop into sleep mode, it woke up again. There have been 3 times where I got graphic card glitches manifesting in a weird pattern instead of my desktop background. Everything else seems to work. Battery lasting about 2h at this moment though :(

Thank you for the help!

---

