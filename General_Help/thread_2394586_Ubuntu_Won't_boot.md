---
title: "Ubuntu Won't boot"
date: 2018-06-18
forum: General Help
---

### Post by heroquestelf on 2018-06-18
I have having a very complex issue, and I'm trying to see if you guys can help me figure this out.  First off, I'm running Ubuntu Mate 16.04.1 LTS on a Toshiba Satellite  with a 2x Intel Core2 Duo CPU (T550 @ 1.83GHz) with 3071MB of memory.

I cannot get Ubunu to boot. Whenever I try to get it to boot up, it hangs up with the following error: 
dev/sda1: clean, 552599/6111232 files, 7119295/24414464 blocks

Now, I found this link to try and solve the problem: [https://askubuntu.com/questions/882385/dev-sda1-clean-this-message-appears-after-i-startup-my-laptop-then-it-w](https://askubuntu.com/questions/882385/dev-sda1-clean-this-message-appears-after-i-startup-my-laptop-then-it-w)

I have tried this, and more problems have shown up. First off, I cannot get recovery mode to launch. I get to the GRUB menu and tab down to the recovery mode option, it hangs up and all I get is a blank screen.

Then, if I try to launch Ubuntu using a live CD, it also hangs, only this time, instead of getting a blank screen, I get the Ubuntu logo with the little green and white dots. As of right now, the system has been sitting on the screen with the logo and the dots for over 5 minutes now. I can't get the OS from the live CD to launch either.

I'm grasping at threads here. Anybody got any ideas/suggestions?

I also tried using the Command line interface on the GRUB menu to do fsck, but the command line does not recognize the command "sudo" or the command "fsck".

Any suggestions would be nice.

---

### Post by oldfred on 2018-06-18
Grub's terminal is very limited and only has commands to allow you to manually boot.

You need to get live installer to boot. Are you sure it is correctly configured? Good download of ISO?
Does your system need boot parameters to boot?
Are you seeing boot process? If you remove quiet splash it should show system booting. Last command posted is usually not the issue, but a few lines above may be.

       May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by heroquestelf on 2018-06-18
How do you remove the quiet splash?

---

### Post by heroquestelf on 2018-06-18
**Update**: Okay, so I got the live CD to load, and I ran the following instruction set: 

> 

[LIST]
[*]boot to a Ubuntu Live DVD/USB 
[*]start gparted and determine which /dev/sdaX is your Ubuntu partition 
[*]quit gparted 
[*]open a terminal window 
[*]type sudo fsck -f /dev/sdaX # replacing X with the number you found earlier 
[*]repeat the fsck command if there were errors 
[*]type reboot 
[/LIST]

The  results went by too fast to copy them down, but it went by all five  passes and returned something similar to the error I saw earlier, which  was "dev/sda1: clean, 552599/6111232 files, 7119295/24414464 blocks"

I  then loaded the boot-repair Cd. I got the Cd to load, but before it  would load it generated the following error: (I hand-typed this, so  there ***MIGHT*** be a typo in it. I tried to copy it as closely as possible.)
```
[   0.087530] ACPI Error: [CDW1] Namespace lookup failure, AE_NOT_FOUND (20170531/psargs-364)
[   0.087584] ACPI Error: Method parse/execution failed \_SB.PCIO._OSC, AE_NOT_FOUND (210170531/psparse-550)
[   12.256248]  [drm:drm_atomic_helper_commit_cleanup_done [drm_kms_helper]] *ERROR* [CRTC:35:pipe B] flip_done timed out
```

Once the boot repair disc got loaded, I ran the boot repair. 

Here is the pastebin: [http://paste.ubuntu.com/p/kbx8hhbhmC/](http://paste.ubuntu.com/p/kbx8hhbhmC/)

I  then tried to boot into Ubuntu again, and this time I was able to get  the recovery mode to launch. I ran an Fsck and these were the results:  (and again, I apologize, as I'm hand-typing this:)

```

/dev/sda1: clean, 426479/14458880 files, 22274608/57823488 blocks
             Starting Remount Root and kernel file systems....
[    ok   ]  Started Remount Root and kernel file systems.
             Starting load/Save random seed....

             Starting udev Coldplug all Devices...
             Starting Flush Journal to Persistent Storage...
[    ok   ]  Started Load/Save Random Seed.
Finished, please Press ENTER
[    ok   ] Started Flush journal to Persistent Storage.
[    ok   ] Started udev Coldplug all Devices
[    ok   ] Started Dispatch Password Requests to Consol Directory Watch.
[    ok   ] Found device SSD2SC240G1CS1754D117-820 5.
            Activating swap /dev/disk/by-uuid/3d81b184-1be8-415e-ac76-02569d67f06e
[    ok   ] Activated swap /dev/disk/by-uuid/3d81b184-1be8-415e-ac76-02569d67f06e
[    ok   ] Reached target swap
[    ok   ] Listening on Load/Save RF Kill Switch Status /dev/rfkill Watch
            Started Load/Save RF Kill Switch Status...
[    ok   ] Reached Target Sound Card
[    ok   ] Started Load/Save RF Kill Switch Status

```

I also told the recovery mode to repair the boot loader and I also told it to repair all broken packages.

I  then tried to reboot the system, and I'm back to the error I had at the beginning: "/dev/sda1: clean, 426479/14458880 files, 22274608/57823488 blocks" with a flashing cursor at the end.

---

### Post by heroquestelf on 2018-06-18
I also tried the following:

> 
    boot to the GRUB menu
    choose Advanced Options
    choose Recovery mode
    choose Root access
    at the # prompt, type:
        sudo blkid
        sudo cat /etc/fstab
    edit your question to include the output from the two previous commands
    type reboot


This was the response: (and again, I'm re-typing this manually)

```

$sudo blkid
/dev/sda1: UUID="ff587ea4-6a6d-4fb3-a628-025c314f0ff7" TYPE="ext4" PARTUUID="fbeb928-01"
/dev/sda5: UUID="3d81b184-1be8-415e-ac76-02569d67f06e" TYPE="swap" PARTUUID="fbeb928-05"
$sudo cat /etc/fstab
# /etc/fstab: static file system information.
#
# use "blkid" to print the universally unique identifier for a
# device: this may be used with UUID= as a more robust way to name devices
# that works even if the disks were added and removed. See fstab(5).
#
# <file system> <mount point> <type> <options> <dump> <pass>
# / swap was on /dev/sda5 during installation
UUID=3d81b184-1be8-415e-ac76-02569d67f06e   none  swap  sw  0  0
[TIME] Timed out waiting for device dev-di...\x2dac75\x2d02569d67f06e.device.
[DEPEND] Dependency failed for /dev/disk/by-...184-1be8-415e-ac76-02569d67f06e.
[DEPEND] Dependency failed for Swap. 

```

I did not understand what "**edit your question to include the output from the two previous commands**" meant. 

Also, one other thing I did was to edit the "quiet splash" in the GRUB menu to 'quiet splash nomodeset' in order to see if I could get the OS to launch, and I got the exact same error.

---

### Post by oldfred on 2018-06-18
The Boot-Repair report includes all the drive/partition info.
Better to use the ppa and add Boot-repair to your Ubuntu in live mode. 
The Boot-Repair ISO is an older copy and ppa will be current updated version.

Most of the errors seem to be from ISO, which is not a standard partitioned drive, so normal.
You can run a command & copy & paste into a reply, but system has to be working or from live installer. So you could have just copy & pasted commands. But same info in Summary Report.

Grub says it installed correctly.

Are drives set for AHCI, not IDE nor RAID?

Have you tried booting older kernels?
Usually best to delete older kernels, so you do not have space used.

Some older systems and Ubuntu versions needed these:
       Older Intel video card: i915.modeset=1 or i915.modeset=0 newer:  i915.i915_enable_rc6=1

---

### Post by heroquestelf on 2018-06-19
I finally got it figure out. It was my graphics card. I had to figure out how to get my Intel Graphics card to update from the command line... and THAT was a booger. However, the point is that I fixed it.

---

