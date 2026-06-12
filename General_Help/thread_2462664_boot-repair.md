---
title: "boot-repair"
date: 2021-05-25
forum: General Help
---

### Post by e-dmz on 2021-05-25
Hi, 

My PC worked fine till yesterday (config below) and now, without obvious reason, I cannot start it anymore.

I tried several things and in particular I had a boot-repair but nothing is changed when I restart (without the Live USB).

Can somebody help me ? I'm a bit lost and I'm considering complete re-installation...

> 
Boot successfully repaired.

Please write on a paper the following URL:
[https://paste.ubuntu.com/p/6z2SzvYHVS/](https://paste.ubuntu.com/p/6z2SzvYHVS/)


In case you still experience boot problem, indicate this URL to:
[EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL] or to your favorite support forum.

You can now reboot your computer.

Please do not forget to make your UEFI firmware boot on the Ubuntu 20.04.2 LTS entry (nvme0n1p1/EFI/ubuntu/shimx64.efi file) !



(I don't understand the last statement of the message below)

Here is what happens when I hit the start button:

[LIST=1]
[*]splash screen (with TUF logo and "TUF GAMING") with "Please press DEL or F2 to enter UEFI BIOS setting" (or sthg like that) under 
[*]black screen as if it was starting normally 
[*]splash screen again but without "Please press..." under. 
[*]then nothing happens, splash screen is there forever 
[/LIST]

PC config:
[LIST]
[*]mobo : Asus TUF Gaming X570-Plus WiFi 
[*]CPU : AMD Ryzen 5 3600 
[*]RAM : 2x8Gb 
[*]GPU : MSI GeForce GTX 1650 Gaming X 
[*]it boots on SSD 1 Tb 
[*](and there's a HDD 2 Tb) 
[*]I build it myself 
[*]I installed Kubuntu 20.04.2 LTS (only, no Windows) 
[*]it's been working just fine for circa 3 months. 
[/LIST]

What I did : 
[LIST=1]
[*]went into the BIOS but nothing to do... as there is no alt boot or repair boot, 
[*]checked the Q LEDs and it goes through sequence fine (RAM, CPU, VGA, BOOT then all off) 
[*]tried  some quick fixes (probably irrelevant to the actual issue if  it's not hardware-related): remove RAM and back, remove mobo battery 5  min and back 
[*]booted from a live USB Kubuntu 21.4 
[*]had boot-repair this way (sudo add-apt-repository -y ppa:yannubuntu/boot-repair && sudo apt update && sudo apt install -y boot-repair ; boot-repair) from [https://doc.ubuntu-fr.org/boot-repair](https://doc.ubuntu-fr.org/boot-repair) 
[*]it then shows the message at the beginning of this post 
[/LIST]
 
Thx for your help!

---

### Post by yancek on 2021-05-25
Line 54 of boot repair shows Boot0000* Ubuntu which is what you need to select in your BIOS firmware to boot.  You should have a Boot or Boot options section in your BIOS firmware.  Also, you need the nvme drive set to first boot priority.

---

### Post by e-dmz on 2021-05-26
Thank you yancek, 
Unfortunately, the problem is still there... [http://paste.ubuntu.com/p/7CDD5rmWSm/](http://paste.ubuntu.com/p/7CDD5rmWSm/)
On UEFI the two options for boot priority are :
"ubuntu (M.2_1: CT1000P2SSD8) (1000.2 GB)" (i believe it's the Boot0000* ?)
and the live-USB boot


CT1000P2SSD8 appears on the report as 
nvme0n1:1000GB:nvme:512:512:gpt:CT1000P2SSD8:;
1:1049kB:538MB:537MB:fat32:EFI System Partition:boot, esp;
2:538MB:1000GB:1000GB:ext4::;

I noticed that my SSD (where it boots from, normally) is protected / impossible to write on it, at least no easy way to do that. Could it be a problem for effective boot-repair? 

Now if I reinstall everything, is there a risk of losing data or anything ? I moved everything of value into the HDD. Should I try something else?

---

### Post by tea for one on 2021-05-26
Power off the PC
Remove the USB Installation media
Power on the PC and press F8 to reach the Boot Menu
Do you see Ubuntu in the list?
> **e-dmz said:**
> I noticed that my SSD (where it boots from, normally) is protected / impossible to write on it, at least no easy way to do that. Could it be a problem for effective boot-repair? 

By the way, I couldn't see anything about encryption or protection in the report?

---

### Post by e-dmz on 2021-05-26
Thank you @tea for one

With F8 I can see "ubuntu (M.2_1: CT1000P2SSD8) (1000.2 GB)", same as in UEFI BIOS (with F2)
If I press Ok, same thing happen again 
> 
[LIST=1]
[*]black screen as if it was starting normally 
[*]splash screen again but without "Please press..." under. 
[*]then nothing happens, splash screen is there forever 
[/LIST]


What I meant about "protection" is that when I live-USB boot, I can see all my files on SSD and HDD. I can read-only the SSD (1Tb) while I can read/write the HDD (2Tb). I don't know whether this is relevant to my problem or not.

Can we say this is an OS issue and not a boot issue? Maybe I should just install Kubuntu and see what happens? I suppose I'll have to reinstall all the software but it's not a big deal. If I reinstall, can I do that on just a partition of the SSD (preserving the data) or will it erase all the SSD?

---

### Post by oldfred on 2021-05-26
Since single install, grub auto boots only entry.
Can you press Escape key right after UEFI/BIOS screen but before grub menu normally would appear to get grub menu?
And then boot recovery mode?

How did you install video drivers? 
From Ubuntu repo or from nVidia directly. 
If nVidia directly you have to reinstall driver with every kernel update, so always better to use Ubuntu repository.

---

### Post by e-dmz on 2021-05-26
> **oldfred said:**
> Since single install, grub auto boots only entry.
Can you press Escape key right after UEFI/BIOS screen but before grub menu normally would appear to get grub menu?
And then boot recovery mode?

Thx so much, it worked!
I'll try to post pictures.
Now when I restart, I have to do it again. What should I do to repair it completely ?

> How did you install video drivers? 
From Ubuntu repo or from nVidia directly. 
If nVidia directly you have to reinstall driver with every kernel update, so always better to use Ubuntu repository.

Yes I did. Should I uninstall them ?
Here is what i get with [FONT=monospace][COLOR=#000000] [FONT=monospace][COLOR=#000000][FONT=monospace][COLOR=#000000]apt [/COLOR][/FONT]list --installed | grep nvidia
[/COLOR][/FONT][/COLOR]
```
libnvidia-cfg1-460/unknown,now 460.73.01-0ubuntu1 amd64 [installed,auto-removable]
libnvidia-common-460/unknown,now 460.73.01-0ubuntu1 all [installed,auto-removable]
libnvidia-common-465/unknown,unknown,now 465.19.01-0ubuntu1 all [installed]
libnvidia-compute-465/unknown,unknown,now 465.19.01-0ubuntu1 amd64 [installed]
libnvidia-decode-465/unknown,unknown,now 465.19.01-0ubuntu1 amd64 [installed]
libnvidia-encode-465/unknown,unknown,now 465.19.01-0ubuntu1 amd64 [installed]
libnvidia-extra-460/unknown,now 460.73.01-0ubuntu1 amd64 [installed,auto-removable]
libnvidia-fbc1-465/unknown,unknown,now 465.19.01-0ubuntu1 amd64 [installed]
libnvidia-gl-465/unknown,unknown,now 465.19.01-0ubuntu1 amd64 [installed]
libnvidia-ifr1-465/unknown,unknown,now 465.19.01-0ubuntu1 amd64 [installed]
libnvidia-ml-dev/focal,now 10.1.243-3 amd64 [installed,auto-removable]
nvidia-cuda-doc/focal,focal,now 10.1.243-3 all [installed,auto-removable]
nvidia-cuda-gdb/focal,now 10.1.243-3 amd64 [installed,auto-removable]
nvidia-dkms-460/unknown,now 460.73.01-0ubuntu1 amd64 [installed,auto-removable]
nvidia-kernel-common-460/unknown,now 460.73.01-0ubuntu1 amd64 [installed,auto-removable]
nvidia-kernel-source-460/unknown,now 460.73.01-0ubuntu1 amd64 [installed,auto-removable]
nvidia-machine-learning-repo-ubuntu1804/unknown,now 1.0.0-1 amd64 [installed]
nvidia-modprobe/unknown,unknown,now 465.19.01-0ubuntu1 amd64 [installed,auto-removable]
nvidia-opencl-dev/focal,now 10.1.243-3 amd64 [installed,auto-removable]
nvidia-prime/focal-updates,focal-updates,now 0.8.16~0.20.04.1 all [installed,auto-removable]
nvidia-profiler/focal,now 10.1.243-3 amd64 [installed,auto-removable]
nvidia-visual-profiler/focal,now 10.1.243-3 amd64 [installed,auto-removable]
xserver-xorg-video-nvidia-460/unknown,now 460.73.01-0ubuntu1 amd64 [installed,auto-removable]
```[/FONT]

---

### Post by oldfred on 2021-05-26
Do not know if still procedure or not:
Uninstall the .run nVidia driver.
[https://askubuntu.com/questions/219942/how-to-uninstall-manually-installed-nvidia-drivers](https://askubuntu.com/questions/219942/how-to-uninstall-manually-installed-nvidia-drivers)

If wrong nVidia driver or upgrade, you must purge & install correct driver or else conflicts and bigger issues.
[https://ubuntuforums.org/showthread.php?t=2362351&p=13649946#post13649946](https://ubuntuforums.org/showthread.php?t=2362351&p=13649946#post13649946)
[https://ubuntuforums.org/showthread.php?t=2380061](https://ubuntuforums.org/showthread.php?t=2380061)
[https://ubuntuforums.org/showthread.php?t=2362351](https://ubuntuforums.org/showthread.php?t=2362351)

# Shows standard repository versions, which is the same as
System Settings, Software & Updates icon, Additional drivers tab
With 18.04, the only way I can get to this now is with Software Updater & Settings.
ubuntu-drivers devices

Install nVidia If you just want default version - recommended one
sudo ubuntu-drivers autoinstall
Or you can manually choose any in list.
sudo apt-get install nvidia-XXX

---

