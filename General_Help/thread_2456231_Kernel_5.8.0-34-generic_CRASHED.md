---
title: "Kernel 5.8.0-34-generic CRASHED"
date: 2021-01-07
forum: General Help
---

### Post by farlander762 on 2021-01-07
Ubuntu 20.04.  Due to a spotty Internet connection I've been fighting for two months (thanks Comcast), I got a bad DL of the latest Kernel via standard Ubuntu updater.  When attempting to boot it goes through the disk check with the spinning icon and then to a black screen with blinking cursor.  No command line and the screen flickers about every 10 seconds like it's trying to restart the graphics.  Won't start in 5.8.0-34's "safe mode" or "debug mode" or whatever the Grub menu option is either.  It did post an error during the update about the Nvidia graphics driver and I did let the bug reporter do it's thing, but I'm just not advanced enough to know what happened. 

I can boot into the previous 5.4.0-59-generic just fine.  I think what I need to do is remove the newer kernel and then let it update again but am open to most anything that fixes it.  Comcast ran a new temporary cable yesterday so the connection is now stable.  I do have the option to fully R&R Ubuntu since my personal stuff is on a separate drive and am competent to do that.  Can someone walk me through removing the affected kernel first?

Please help!!

---

### Post by CelticWarrior on 2021-01-07
I would try, before anything else
```
sudo apt update && sudo apt full-upgrade
```

---

### Post by CatKiller on 2021-01-07
> **farlander762 said:**
> I got a bad DL of the latest Kernel via standard Ubuntu updater. 

Unlikely. The packages are checksummed and cryptographically signed. If the package was corrupted by the Internet connection the package manager would either download it again or stop and complain. 

> It did post an error during the update about the Nvidia graphics driver 

How did you install the driver?

When it's installed through the package manager it will automatically reconfigure itself on kernel upgrades so that it keeps working. Other methods of installing the driver lack that facility.

---

### Post by farlander762 on 2021-01-07
> How did you install the driver?

I didn't do anything with the Nvidia driver.  Whatever was done was through the updater.  If you're asking about on my original install, that was last year sometime and I don't remember.  If not a bad DL, I don't know what to say.  It was a standard kernel update and I wasn't paying it too much attention.  The system was otherwise idle during the updates because kernels are big important stuff and I knew I was about to restart anyway.

Going to give the "apt" advice above a quick whirl.  UPDATE:  No change after running > sudo apt update && sudo apt full-upgrade

Thanks!

---

### Post by CatKiller on 2021-01-07
> **farlander762 said:**
> If you're asking about on my original install, that was last year sometime and I don't remember.
Yes, that's what I mean.

Installed the Linux way - through the package manager, optionally after adding a PPA with a newer version - the shim that goes between the open source kernel and the proprietary driver module gets automatically rebuilt on kernel upgrades through a process called DKMS. That stops the driver breaking on kernel upgrades, since otherwise they would only work with one specific kernel version.

Nvidia have a .run file on their website, which is intended for package maintainers rather than end users, but ex-Windows users insist on trying to use it because they feel it's sufficiently close to what they're used to doing on Windows. In many cases, that file will not enable DKMS, which means the driver breaks on kernel upgrades. 

A broken graphics driver followed by frustrated forced power downs would give exactly the symptoms you've described. 

If that is what you've done - erroneously installed a driver from a random website - you can boot into the kernel that still has a working graphics driver, uninstall it using the script that you used to install it, and then install the driver through the package manager or the built in automatic tool. That will create working shims for your installed kernels and create a new one for each new kernel that you install in the future.

---

### Post by farlander762 on 2021-01-07
Gotcha, I would not have gone off reservation to get a driver.  Most likely it was the one recommended by Ubuntu (I actually select Nvidia due to their Linux support).  

BTW, I went back in my browser history and found the bug report.  [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-340/+bug/1885344]("https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-340/+bug/1885344")  Looks like this is a real bug and this same issue crops up on fresh installs with this driver/kernel combo.

Thanks for your help, I'll see what they do going forward and keep booting to the older kernel for now.

---

### Post by grahammechanical on 2021-01-07
My 20.04 got a kernel update a couple of hours ago. It was an update to kernel 5.4. An earlier update was to the 18.04 Hardware Enablement Stack. If there is an issue with the 5.8 kernel and the 20.04 Hardware Enablement Stack then under the phased updates system the 5.8 kernel will not be made available to more users until the issue is fixed.

I suggest that the original poster continue loading the 5.4 kernel. At some point there will an update to the 5.8 kernel and when that comes through you can try loading with it again.

Regards

---

### Post by farlander762 on 2021-01-08
5.8.0-36-generic was pushed down this morning.  Same issue.  

Just really happy I still have the older kernel available.

---

### Post by Erlander on 2021-01-08
I was experiencing the same problem but have fixed it by changing from the NVidea driver to the X_org driver.

---

### Post by farlander762 on 2021-01-08
I can't boot into those two kernels at all to be able to do so.  Not even to CLI.

---

### Post by grahammechanical on 2021-01-08
Can you load a recovery kernel from Advanced Options for Ubuntu? If so, then select Network to get a connection to the internet. Then select Root to get to a root shell (terminal). We exit the command line and get back to the recovery menu by typing exit.

At the root shell we can remove the Nvidia driver with

```
apt remove --purge nvidia*
```

When back at the recovery menu Resume will load the Ubuntu desktop with an open source video driver. If you get a black screen, then re-boot. If you cannot load a recovery kernel you may have work from a Live session to install a 5.4 kernel.

Regards.

---

### Post by grabasimo on 2021-01-11
I have issue with nvidia drivers in my 20.10. 
After installation driver and reboot system my X server don't get up.

```
udo lshw -numeric -C display[sudo] has&#322;o u&#380;ytkownika graba: 
  *-display UNCLAIMED       
       description: 3D controller
       product: GP107M [GeForce GTX 1050 Ti Mobile] [10DE:1C8C]
       vendor: NVIDIA Corporation [10DE]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:de000000-deffffff memory:c0000000-cfffffff memory:d0000000-d1ffffff ioport:e000(size=128) memory:df000000-df07ffff
  *-display
       description: VGA compatible controller
       product: HD Graphics 630 [8086:591B]
       vendor: Intel Corporation [8086]
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 04
       width: 64 bits
       clock: 33MHz
       capabilities: pciexpress msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:126 memory:dd000000-ddffffff memory:b0000000-bfffffff ioport:f000(size=64) memory:c0000-dffff

```

---

### Post by farlander762 on 2021-01-14
I have been running in one of the older 5.4 kernels for over a week.  I did even boot into the newest kernel with root access to CLI (5.8.0-38-generic) which was installed this morning.  I have been forbidding the updater to delete the two older 5.4 kernels that still work.  

I'll give this a try later and let you know.  I do know what menu items you're talking about and can use those tools enough to be dangerous.  Just FYI, there are now three 5.8 kernels that do not load on my machine.

Thanks!

---

### Post by CatKiller on 2021-01-14
> **farlander762 said:**
> I have been forbidding the updater to delete the two older 5.4 kernels that still work.  

If you remove the HWE metapackages, it will stop giving you more new kernels, and the non-HWE metapackage will give you security updates to the 5.4 branch. As the kernel branch that came with the release, 5.4 will be supported for the full five years.

---

### Post by CelticWarrior on 2021-01-14
[https://ubuntuforums.org/showthread.php?t=2456501&p=14014151#post14014151](https://ubuntuforums.org/showthread.php?t=2456501&p=14014151#post14014151)

---

### Post by farlander762 on 2021-01-14
> If you remove the HWE metapackages, it will stop giving you more new kernels, and the non-HWE metapackage will give you security updates to the 5.4 branch. As the kernel branch that came with the release, 5.4 will be supported for the full five years.

I understand what you're saying, I don't how to do it.  Additionally, I want it to keep up to date.  To my understanding, updates are the best way to keep a Linux system secure.

> apt remove --purge nvidia*

Tried this, it just said it couldn't find the nvidia* package.  I also tried *nvidia just to be sure.  In the 5.4 kernel it says I am using the attached.  I have no idea about the manually installed part.  Other options are not selectable.

[ATTACH=CONFIG]287739[/ATTACH]

---

### Post by CatKiller on 2021-01-14
> **farlander762 said:**
> I understand what you're saying, I don't how to do it.

The post CelticWarrior linked to gives the instructions. 

The metapackages don't install anything themselves: their function is to depend on the latest version of another package or group of packages so that you can install them in one go, and have multiple versions installed at once in the case of the Linux metapackages. The HWE package, which is giving you 5.8 kernels and that you want to remove, is called linux-generic-hwe-20.04. The non-HWE metapackage, which will give you 5.4 kernels and that you want to make sure you have installed, is called linux-generic. 

> Additionally, I want it to keep up to date.  To my understanding, updates are the best way to keep a Linux system secure. 

The 5.4 branch (and all the Ubuntu packages) get security updates and bug fixes. That's how Ubuntu's release model works. They don't get new features or higher version numbers except in special cases; enabling the use of brand new hardware is one of those special cases, done through the Hardware Enablement stack. In your case, the HWE isn't what you want. You can always reinstall it later, if you see reports that the problem you're experiencing has been fixed and you particularly want the newer features that come with the higher version number kernel. 

>  Tried this, it just said it couldn't find the nvidia* package.  I also tried *nvidia just to be sure.

Apt doesn't support using special characters like *. The alternative apt-get does.

---

### Post by farlander762 on 2021-01-17
All, thanks for the help.  I've got two confusers out of 6 so far that had issues with 5.8 and have been rolled back to 5.4.  CW's link got me there.  I'm stable, which means I'm happy!

Thanks again!!

---

