---
title: "Upgraded laptop with Nvidia to 16.04 and can't login - sometimes can't boot."
date: 2016-04-24
forum: General Help
---

### Post by patfla on 2016-04-24
Upgraded to 16.04 and my Asus Optimus laptop (two graphical subsystems: intel and Nvidia) is, at the moment, pretty much useless.  Or rather it is useful but only because it's a dual-boot with Win 10.  The Ubuntu partition then is dead in the water.

If it does boot to the GUI login screen, I try to login, it throws an error that flies by very quickly, and recycles back to the login screen.  So drop down into a tty (ctrl-alt-F1) and login.

Much digging.  /var/log/kern.log shows this, repeated many times, which I believe to the be root error:

> Apr 23 18:55:23 patfla-N550JV kernel: [    7.039052] NVRM: API mismatch: the client has the version 352.79, but
Apr 23 18:55:23 patfla-N550JV kernel: [    7.039052] NVRM: this kernel module has the version 361.42.  Please

Hmm (I'm a programmer) ... an older version of nvidia inside a kernel module as opposed to some kind of graphical client (the X subsystem?) outside the kernel.  Their versions don't match. 

Search the web and it seems that what I might want to do is rebuild initrd which in the process of rebuilding would pick up the newer, "outside" reference to the driver.  That web page says I should use mkinitcpio - except mkinitcpio doens't appear to exist in Ubuntu and that appears to be because Ubuntu is build on Debian and Debian uses initramfs (which I assume means init ram filesystem).

Tried:

> update-initramfs -u (-u was recommended as working on the latest version) and that did produce a new initrd file /boot but when I reboot I get the same error.

And that's where I'm at now.  So - is this what I want to do (rebuild initrd) and if so, how do I do that effectively for Ubuntu/Debian?

I'd simply reinstall but ISO I burned to do this with won't in fact boot - someone somewhere on the web this sometimes happens if you burn the disk at any but the slowest speed - and so I'd need to restart that process if I want to go that root.  Besides I'd rather follow the initrd train of thought and I'd rather not wipe out my current installation (although maybe Ubuntu installs have gotten smart enough not to wipe out bystander files)

Thanks - Pat

---

### Post by patfla on 2016-04-24
Jeez.  I only noticed just now as I posted this, that it's the other way round.  It's the client, not the server, that has the older version.  So maybe it has nothing to do with initrd.  But then if the client is say the X server how is that the X server is picking up a different version of the nvidia driver.

OK I'm further confused.

---

### Post by patfla on 2016-04-24
Ah.  /var/log/X.org.[0|1].log has this to say:

> [     5.241] (II) NVIDIA dlloader X Driver  352.79  Wed Jan 13 15:31:15 PST 2016
[     5.241] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs




---

### Post by mc4man on 2016-04-24
**IF** you previously installed nvidia from a debian package then maybe start with going to a tty (ctrl+alt+f3), login, then run - 
```
sudo apt purge nvidia*
```
If that completes then go sudo reboot & see if it works on intel.

If so then install synaptic, search nvidia & try one the later versioned drivers. Maybe they'll work, maybe not 
(on my skylake with nvidia 940m only the 358 drivers work, earlier & later all fail, usually with a login loop

---

### Post by patfla on 2016-04-24
Tried that and it didn't appear to work.  This too produces the endlessly recycling GUI login screen.

---

### Post by mc4man on 2016-04-24
> **patfla said:**
> Tried that and it didn't appear to work.  This too produces the endlessly recycling GUI login screen.

Did you install nvidia drivers from nvidia with a run file?

---

### Post by patfla on 2016-04-24
Actually no.  Let me look around for where I can get one and I'll give it a try.

---

### Post by patfla on 2016-04-24
Downloaded the .run file from Nvidia downloads and ran it.  Early on it said "pre install script failed - continue to run?".  I filed that for later reference and continued.  Install finished.

It still cycles at the GUI login screen so I entered a tty session.

The nvidia vers err mismatch messages appear to have disappeared from /var/log/kern.log - that's progress.  So why am I still cycling?

Strangely, dpkg -l | grep -i nvid doesn't show a new nvid driver version installed.  That's strange.  gpu-manager does show an nvidia driver loaded however towards the end of its run it asks "is nvidia being used?" and replies "No".  I wonder if that's because intel is currently being used?

Where I last left it, I figured it's maybe an X problem and one that might be fixed by deleting X-related files under my home directory.  Fiddled with those for a while but unsuccessfully.

Part of being an experienced software engineer is to be willing to beat yourself senseless in the process of solving problems.

---

### Post by mc4man on 2016-04-24
While it may be something else,  in general with optimus - 
if on intel & there is an xorg.conf then you'll never login
if on nvidia & there isn't an xorg.conf you'll never login

maybe go to a tty & run - 
```
sudo prime-select intel
```
then ck /etc/X11 for an xorg.conf & remove or mv to a .bak if there
reboot & see

---

### Post by patfla on 2016-04-25
I tried some of that but still got the endlessly looping GUI login screen and finally bit the bullet and reinstalled.  Which I wanted to avoid in part because the first install ISO I burned to disk didn't work but then I noticed on the web that it can sometimes be problematic making these and one should make a bootable linux install dvd with a relatively slower burn speed - which worked.

Only then to find that when I rebooted, hopefully into the new system, it landed at the grub2 prompt.  Jeez.

Followed instructions here [https://www.linux.com/learn/how-rescue-non-booting-grub-2-linux](https://www.linux.com/learn/how-rescue-non-booting-grub-2-linux) to the effect of

> set root=(hd0,gpt6)
linux /boot/...
initrd /boot/...
boot

and that worked (moreover first time which is usually a source of wonder) - except it doesn't, as one would guess, persist so now I'm off to figure out, I guess, how to fully configure grub.

The install should have done all this, but didn't, but did leave a fully working new install so hopefully I'm on the glide path out of this detour from what I really should be doing.

Thanks for your help mc4man.

---

### Post by patfla on 2016-04-25
I might add that I got into this whole pickle in the first place in the process of Ubuntu prompting me to upgrade from what was originally 14-something and then my needing to reinstall my nvidia drivers but in particular CUDA since that's where my real work is.  Image recognition stuff.  So somehow somewhere my fumbling around inside nvidia drivers-CUDA led to my getting different nvidia driver versions in the graphical client as opposed to the kernel.

Still, you do learn from these experiences.

---

### Post by oldfred on 2016-04-25
If you have gpt are you booting with BIOS or UEFI?
If BIOS you must have the 1 or 2MB unformatted partition with the bios_grub flag or else grub does not install correctly. Or you must have an ESP - efi system partition on sda, or grub does not install correctly.

       But may be best to see details:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by patfla on 2016-04-25
Hmm that's interesting.  The laptop is a slightly > 2-yr-old Asus N550JV.  I think of its BIOS as being a UEFI BIOS except that description wouldn't accord with the way you just put it but then I've acquired only enough knowledge of UEFI to have met my needs to date.

It seems that to create a Bootinfo summary, I need to make some kind of Live CD which I'll go off and do when I find the time.  Doesn't help that as of 2-3 mins ago the "m" key on my physical keybd seems to have bit the dust and I'm using the On-Screen keyboard to produce m.  Asus had been great for parts of the desktops I've built but I doubt I'll buy one of their laptops again - or maybe laptops are only supposed to physically hold together for 2 years.

---

### Post by patfla on 2016-04-25
No, it's easier than that (should have read more slowly).  Add a repository; apt-get install Boot-Info packages; and run.  Once I get out of Windows 10 and via cryptic grub2 commands, get back into Ubuntu.

---

### Post by mc4man on 2016-04-25
> **oldfred said:**
>  Or you must have an ESP - efi system partition on sda, or grub does not install correctly.

Is that a 'hard' requirement or whatever one chooses when setting up the install. I happened to notice that on a dual boot (16.04/14.04.3) that when I tried to install 14.04.4 it came up with an error message about grub couldn't do something with the "target" & wouldn't be installed or installed properly.

In this case maybe I left the bootloader choice at sda though I thought I'd set it to sdb
(on that machine sda is 24GB ssd that used to be for Intel faststart, currently it's unallocated. sdb is the internal ssd

---

### Post by oldfred on 2016-04-25
My main install is on sda, but my test installs on sdb, I always say to install to sdb. I have another ESP on sdb, and even during install it says it is installing grub to sdb (my new SSD installs so quick I cannot see it anymore when on that drive), but it overwrites my /EFI/ubuntu folder. Only difference is actually grub.cfg in /EFI/ubuntu and which partition the config file points to. But I quickly learned to backup ESP.

You can run the Boot-Repair from a working Ubuntu, from a live installer or download its own liveCD version.

---

### Post by patfla on 2016-04-25
Actually, I went ahead and did a full Boot-Repair and now the new installation boots up correctly.  Thanks for people's help here.

---

