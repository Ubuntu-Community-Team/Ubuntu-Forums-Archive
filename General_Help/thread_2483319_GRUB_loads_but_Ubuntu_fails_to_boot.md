---
title: "GRUB loads but Ubuntu fails to boot"
date: 2023-01-26
forum: General Help
---

### Post by gusgf on 2023-01-26
After picking Ubuntu in the grub menu (dual booting with W10 which still loads fine) I'm seeing this message: 
```
Recovering Journal...../dev/nvme0n1/p6 clean, n/n files, n/n blocks
```

From the Ubuntu live USB I've run fsck on all the partitions and I don't see any errors reported.

I've just run Boot Repair and pasted it [here]("https://paste.ubuntu.com/p/r46f6RZxBV/")

---

### Post by tea for one on 2023-01-26
[COLOR="#0000FF"]Line 88[/COLOR] - The firmware is EFI-compatible, but this live-session is in Legacy/BIOS/CSM mode (not in EFI mode).
[COLOR="#0000FF"]Line 272[/COLOR] - The current session is in BIOS-compatibility mode. Please disable BIOS-compatibility/CSM/Legacy mode in your UEFI firmware, and use this software from a live-CD (or live-USB) that is compatible with UEFI booting mode

Can you boot the live session in UEFI mode and run the report again.

By the way, did you install Nvidia drivers at all?

---

### Post by TheFu on 2023-01-26
Folks, we've already gone down the fsck route. That isn't the issue.  He's getting to grub, but Ubuntu won't boot, win10 does boot.  Anyway, check out the boot-info data. Hopefully someone can see the problem.

---

### Post by gusgf on 2023-01-26
Here we go see pastebin [here]("https://paste.ubuntu.com/p/grKzgG74KF/") hopefully this is what you are looking for

---

### Post by tea for one on 2023-01-26
I can't see anything untoward in the latest boot-repair report therefore I would try the default boot-repair function.
Hopefully, Ubuntu will boot but you will have to address the installation of Nvidia drivers.

---

### Post by gusgf on 2023-01-26
Sorry I didn't personally install any nvidia drivers and relied on the initial install to get it right

---

### Post by gusgf on 2023-01-26
This all happened when I decided to try and install Onedrive using the instructions on [makeuseof.com]("https://www.makeuseof.com/how-to-install-microsoft-onedrive-on-ubuntu/") using the code below

sudo apt-get update
sudo apt-get upgrade -y
sudo apt-get dist-upgrade -y
sudo apt-get autoremove -y
sudo apt-get autoclean -y

When I rebooted after running the above that's when it all went wrong. Can you see anything in the above that would cause problems?

[Pastebin]("https://paste.ubuntu.com/p/BW94nPBqFn/") after running Boot Repair

Feedback from Boot Repair:
Boot successfully repaired.

Please write on a paper the following URL:
[https://paste.ubuntu.com/p/BW94nPBqFn/](https://paste.ubuntu.com/p/BW94nPBqFn/)


In case you still experience boot problem, indicate this URL to:
[email]boot.repair@gmail.com[/email] or to your favorite support forum.

You can now reboot your computer.
Please do not forget to make your UEFI firmware boot on the Ubuntu 22.04.1 LTS entry (nvme0n1p1/efi/ubuntu/grubx64.efi file) !
If your computer reboots directly into Windows, try to change the boot order in your UEFI firmware.
If your UEFI firmware does not allow to change the boot order, change the default boot entry of the Windows bootloader.
For example you can boot into Windows, then type the following command in an admin command prompt:
bcdedit /set {bootmgr} path \EFI\ubuntu\grubx64.efi

---

### Post by tea for one on 2023-01-26
> **gusgf said:**
> This all happened when I decided to try and install Onedrive using the instructions on [makeuseof.com]("https://www.makeuseof.com/how-to-install-microsoft-onedrive-on-ubuntu/") using the code below

sudo apt-get update
sudo apt-get upgrade -y
sudo apt-get dist-upgrade -y
sudo apt-get autoremove -y
sudo apt-get autoclean -y

When I rebooted after running the above that's when it all went wrong. Can you see anything in the above that would cause problems?
Without knowing which packages (if any) were removed by autoremove and autoclean, it's impossible to offer precise advice.

Did boot-repair not fix Grub for you?

---

### Post by gusgf on 2023-01-26
No :(

When I select W10 boots fine, when I select Ubuntu from Grub (GNU GRUB v2.06) this is all that appears on a black screen

```
/dev/nvme0n1p6: recovering journal
/dev/nvme0n1p6: clean, 267972/1466368 files, 3482749/5859328 blocks
[     4.956901] 
```

What was a bit weird on one occasion when I pressed the power button on the above screen, a screen flashed up which looked like it was going to boot up into Ubuntu but it was too late and the PC shutdown. Not see that before. Unfortunately no further along?!

---

### Post by gusgf on 2023-01-26
Okay when I boot into recovery and choose 'resume normal boot' it only gets as far as a black screen again, but this time with a steady cursor in the top left corner. But I can't enter anything. I think I've figured out why I keep getting 'recovering journal', it's because I keep having to force shutdown down when I get black screened. This message originally led me to believe that there was partition corruption, there isn't it's because of the force shutdowns when the GUI isn't coming up or the boot processes haven't completed. More likely the latter.

Question is where do I go from here?

---

### Post by tea for one on 2023-01-26
Forced shutdowns generate system checks on next boot, hence recovering journal.

As you always arrive at a black screen, I still wonder if your Nvidia drivers are correct.
However, I cannot help with the exact commands because I do not have Nvidia GPU.

If you can still boot Advanced > Recovery, I found this recent info [https://askubuntu.com/questions/1437323/ubuntu-no-longer-boots-after-reinstalling-graphics-driver](https://askubuntu.com/questions/1437323/ubuntu-no-longer-boots-after-reinstalling-graphics-driver)

If it doesn't help, there are many posts about "remove and install Nvidia" drivers in these forum pages, take a bit of time and have a look...........

---

### Post by #&amp;thj^% on 2023-01-26
From as far as a black screen again, but this time with a steady cursor in the top left corner, in this window use:<Ctrl+Alt+F2>
login at the prompt and try the below.
Could you please try this if it's not to late:
```
sudo apt install --reinstall nvidia-driver-525 
sudo apt install --reinstall nvidia-dkms-525 
```
reboot

---

### Post by tea for one on 2023-01-26
@1fallen
Pleased to see you here.
Thank you for the lifebelt.
I've reached the shoreline safely, let's hope gusgf does too.

---

### Post by gusgf on 2023-01-26
@tea for one
Thank you for the link it allowed me to view the GPU spec and drivers but I didn't run the install commands and wasn't going to until I was sure. Thank you again for your help :)

@1fallen
I could cry with relief. I've finally got my life back after 3 days of hacking around. It's so frustrating when you don't know very much about Ubuntu. Yes I've got my system back and normal life can resume, thank you so much :)

---

### Post by #&amp;thj^% on 2023-01-26
:) and that makes me happy

---

### Post by tea for one on 2023-01-26
> **gusgf said:**
> @1fallen
I could cry with relief. I've finally got my life back after 3 days of hacking around. It's so frustrating when you don't know very much about Ubuntu. Yes I've got my system back and normal life can resume, thank you so much :)
Splendid.
Now, make sure that you regularly back up your data, especially your Odin project files.
Once you have backups, the ultimate disaster recovery is re-installation and restore data - can't be more than a couple of hours.

That 1fallen, he's a diamond geezer!

---

### Post by TheFu on 2023-01-26
I removed nvidia from my systems to avoid these dumb issues.  Staring at a 1030 GT sitting on on the desk now. Pulled it from this system to use the iGPU instead.  Have to say, I never had the black screen issue at boot with any nvidia cards myself.  None of my laptops have nvidia.

BTW, in prior releases, we could just run 
```
$ sudo ubuntu-drivers autoinstall
```
and the correct proprietary nvidia driver would be installed.  Guess that was too easy, so they removed it from 22.04.  It wasn't always that easy, but for 18.04 and 20.04, it was, for supported nvidia hardware.  My 430GT on 20.04 works that way still, but not the 7200 GS which has long been dropped by nvidia from Linux support.

Even if AMD iGPU support on Linux is tied to kernels and it isn't a fast on Linux as on Windows, it is no-hassle when you have a current enough kernel for the GPU.  I'm on a system that doesn't have AMD driver support due to the kernel being 5.4.x.  Support for the iGPU was provided in 5.10, so when I move to 20.04 and the 5.15 kernel, it will be supported and I won't need to worry about it until the APU is replaced.

When 20.04 was released, there were some nvidia issues with Wayland, to the point that Canonical removed Wayland as the default display server about 2 weeks later for any systems with nvidia GPUs.

Regardless, happy this is all solved.

---

### Post by #&amp;thj^% on 2023-01-26
@ TheFu I just can't imagine that you with your vast knowledge would ever have any problems. (Genuine)
at least none you couldn't fix quickly.
EDIT: I'm addicted to the Video Quality, and encoding.

---

### Post by guy-delathouwer on 2023-01-28
> **TheFu said:**
> I removed nvidia from my systems to avoid these dumb issues.  Staring at a 1030 GT sitting on on the desk now. Pulled it from this system to use the iGPU instead.  Have to say, I never had the black screen issue at boot with any nvidia cards myself.  None of my laptops have nvidia.

BTW, in prior releases, we could just run 
```
$ sudo ubuntu-drivers autoinstall
```
and the correct proprietary nvidia driver would be installed.  Guess that was too easy, so they removed it from 22.04.  It wasn't always that easy, but for 18.04 and 20.04, it was, for supported nvidia hardware.  My 430GT on 20.04 works that way still, but not the 7200 GS which has long been dropped by nvidia from Linux support.

Even if AMD iGPU support on Linux is tied to kernels and it isn't a fast on Linux as on Windows, it is no-hassle when you have a current enough kernel for the GPU.  I'm on a system that doesn't have AMD driver support due to the kernel being 5.4.x.  Support for the iGPU was provided in 5.10, so when I move to 20.04 and the 5.15 kernel, it will be supported and I won't need to worry about it until the APU is replaced.

When 20.04 was released, there were some nvidia issues with Wayland, to the point that Canonical removed Wayland as the default display server about 2 weeks later for any systems with nvidia GPUs.

Regardless, happy this is all solved.

I got a similar issue on mine. The GT1030 was running happily with Nvidia driver 515 on Linuxmint 20.3.
Then for all of a sudden, it booted on a black screen. Turns out the driver had been upgraded to 525.

--> purge 525, reinstall 515 and it is running again (kernel 5.4.0).

---

### Post by TheFu on 2023-01-28
> **1fallen said:**
> @ TheFu I just can't imagine that you with your vast knowledge would ever have any problems. (Genuine)
at least none you couldn't fix quickly.
EDIT: I'm addicted to the Video Quality, and encoding.

There are so many things I don't know.  I'm careful to avoid replying to things I haven't any clue about here.  Even then, sometimes I overstep my knowledge.  Perhaps I'm lucky, but I've only had boot issues with Linux, perhaps 5 times over the last 30+ yrs, so I never needed to learn much about that stuff.

Everyone has different experiences.  Sometimes I get frustrated with changes in distros, so I'll strip out the new stuff and get it working like it did in 2010.  For most system-level stuff, I think 10.04 was the peak of Ubuntu doing what was expected.  Since then, things have been changed for little good reason as far as I'm concerned, at least at the system-level.  I have no use for systemd, pulseaudio, Unity, Gnome3+, snap packages, UEFI, resolvconf, systemd-resolved, systemd-timed, systemd-mount, systemd-login,  .... I will admit to liking journalctl and systemd logging. THAT is an improvement.  I'm sure there have been some improvements, but because they are working, they aren't squeaky, so I don't feel them daily.  So many things in systemd broke things that worked well and changed the interface for no reason at all.

I miss ifupdown, but if the code hasn't been maintained since 2011, the Linux community needed a replacement.  ip is that replacement, but they seemed to go out of their way to break output formats that we  all knew.  Just look at 'route -n'. It made nice columns that were easy for humans to read.  The closest with ip, is 'ip r | column' which is a poor imitation.  Even 'ip -h r' (human readable), sucks compared to 'route -n'  Sigh.

Netplan is finally becoming usable.  I fail to see why the old format and commands couldn't be parsed and used, just with a new networking subsystem.  More "new for the sake of new" junk.

More and more I really miss 'sudo touch /forcefsck'  as a way to get an fsck to be run on a file system at the next boot.  Simple. Elegant. Doesn't require console access to do it, unlike modifying grub parameters or choosing grub recovery mode.  It is definitely worse that what we had before.  Just this week, there were 3 long threads in these forums which would trivially have been solved with 'sudo touch /forcefsck', if that still worked.  Systemd-mount improvements, my a$$.  Stuff like this leaves me despondent. They (systemd-mount team) broke something what was working for 20+ yrs and provided multiple crappy replacement options.

Sorry for the rants.  I feel better now. ;)  I need to get outside and enjoy the day.

---

### Post by #&amp;thj^% on 2023-01-29
I can truly appreciate your input here, and I see we both have about the same assessment, and at time's I let my frustration run here for the world to see as well.;) (Tension breaker just has to be done to stay sane)

---

