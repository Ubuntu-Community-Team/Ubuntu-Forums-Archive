---
title: "Stuck at grub terminal"
date: 2023-10-05
forum: General Help
---

### Post by deci0000000000 on 2023-10-05
Hi, 

I am stuck at the grub terminal when I start the machine

[LIST]
[*]23.04
[*]full disk encryption
[*]I cannot remember changing anything when I turned off the machine yesterday and don't remember any error messages or anything
[*]I am not prompted for password to decrypt the drive first
[/LIST]

Tried without success

[LIST]
[*]timeshift back up from a couple of months ago which restored but with the same result stuck at grub terminal
[*][https://askubuntu.com/a/1175786/1722689](https://askubuntu.com/a/1175786/1722689) where it asks to find a grub directory and I cannot find it
[*][https://help.ubuntu.com/community/ManualFullSystemEncryption/Troubleshooting](https://help.ubuntu.com/community/ManualFullSystemEncryption/Troubleshooting) and get stuck sudo mount /dev/mapper/system-root /mnt/root and I get mount: /mnt/root: special device /dev/mapper/system-root dot not exist
[/LIST]

Is there anything I can do besides reinstall? 

------
fwiw just overwhelmed with it all, I am ill, no ADHD medication due to the shortages, the machine not working means I cannot go to work who don't have time to help me either, signing up for the forum has been difficult with the above which is why I have the stupid username as the form kept complaining, everything feels just punishing today.

---

### Post by sudodus on 2023-10-05
- It is probably easier to get  working system with Ubuntu version 22.04.x LTS (with long time support).

- Furthermore, it is easier to avoid disk encryption (but if you need it, OK, let us try to fix it).

Anyway, yes, it is probably easiest to reinstall (and hope things turn out better next time).

---

### Post by Rubi1200 on 2023-10-05
Hi and welcome to the forums :-)

Sorry to hear about your troubles. Let's see if we can try and help.

You need to boot the computer with a liveUSB, preferably with the same version of Ubuntu that is installed, and then choose to Try Ubuntu.

Once you are at the desktop please run the scripts in my signature and post the results back here at the forum.

The two scripts will help us diagnose the situation and hopefully offer a solution.

Boot info script and system info script are the ones I am referring to.

---

### Post by deci0000000000 on 2023-10-05
thank you 

Results from scripts
System info script [https://paste.ubuntu.com/p/dCnjQwq4V9/](https://paste.ubuntu.com/p/dCnjQwq4V9/) 
Boot info script [https://paste.ubuntu.com/p/rWYm6Wh3mM/](https://paste.ubuntu.com/p/rWYm6Wh3mM/)

---

### Post by MAFoElffen on 2023-10-05
From the 'system-info' Report:

Lines 211-212:
```

----------  LUKS Information:
System has a LUKS encrypted filesystem.

```
Lines 196-199
```

nvme0n1     953.9G                                                                                            WD PC SN810 SDCQNRY-1T00-1001
|_nvme0n1p1     1G vfat                                                                                       
|_nvme0n1p2     2G ext4                                                                                       
|_nvme0n1p3 950.8G crypto_LUKS                                                                                

```
From the 'boot-info' Report:

Line 51:
```

OS#1:   Ubuntu 23.04 on mapper/ubuntu--vg-ubuntu--lv

```
Lines 26-28
```

nvme0n1p3: _____________________________________________________________________

    File system:       crypto_LUKS

```
Lines 143-144
```

Disk mapper/myvolume: 950.8 GiB, 1020915613696 bytes, 1993975808 sectors
Disk mapper/ubuntu--vg-ubuntu--lv: 950.8 GiB, 1020914565120 bytes, 1993973760 sectors

```
Lines 155-157
```

mapper/ubuntu--vg-ubuntu--lv:1021GB:dm:512:512:loop:Linux device-mapper (linear):;
1:0.00B:1021GB:1021GB:ext4::;
mapper/myvolume:1021GB:dm:512:512:unknown:Linux device-mapper (crypt):;

```
Lines 173-178
```

nvme0n1                                                                                                                                
&#9500;&#9472;nvme0n1p1                 vfat        01E9-D809                              85a217d6-55b0-ca43-9c05-f43a3b48aad1                    
&#9500;&#9472;nvme0n1p2                 ext4        12d74d50-96b7-4e21-9838-bbdfd76486a1   f10dab0c-366c-334c-9ac4-464eca4aa785                    
&#9492;&#9472;nvme0n1p3                 crypto_LUKS 0cacfddd-7c4f-4361-aa47-56c7d4810434   78805d39-acfc-ab45-a1bf-8c6122b97cd7                    
  &#9492;&#9472;myvolume                LVM2_member 1i4IBT-MPZm-wfxg-tJB2-EjE7-CYD7-E4NDAb                                                         
    &#9492;&#9472;ubuntu--vg-ubuntu--lv ext4        ff08c75d-003e-4d03-a596-bac66cbff379                                                           

```
Lines 248-249
```

/dev/mapper/ubuntu--vg-ubuntu--lv: UUID="ff08c75d-003e-4d03-a596-bac66cbff379" BLOCK_SIZE="4096" TYPE="ext4"
/dev/mapper/myvolume: UUID="1i4IBT-MPZm-wfxg-tJB2-EjE7-CYD7-E4NDAb" TYPE="LVM2_member"

```
Recommendation at Line 273
```

You may want to retry after mounting your encrypted partitions so that the tool 
can verify their contents. (sudo cryptsetup luksOpen /dev/nvme0n1p3 myvolume)

```
From what I see from both reports, the partitions, file manager, and filesystems look okay. It is has EFI in nvme0n1p1, with unencrypted boot in nvme0n1p2, and LVM2 with LUKS container at /mapper/myvolume, with the root LV at /mapper/ubuntu--vg-ubuntu--lv within the LUKS container...

I do not see a problem indicated for the Grub2 bootloader from that level, because the LUKS's container is locked.

The recommendation from the 'boot-info' script for unlocking the LUKS container would work if done booted from a Live Image Environment...

What I would try first is to, at the Grub2 boot, press the "E" key to get into an edit mode for the menu. Press the <arrow-down> key until you get to the lie that starts with the word "linux". <Arrow-right> until you get to the words "quiet splash". Replace those words with "--- 3". Press the keys <Cntrl><X> to boot.

Watch the boot messages until it stops at the encryption passphrase prompt. Enter your passphrase. What does it do?

---

### Post by deci0000000000 on 2023-10-05
Sorry I don't understand so for me 

[LIST=1]
[*]turn machine on
[*]Gets to grub terminal
[*]if live usb is available I can type exit
[*]grub menu appears
[*]follow the steps
[/LIST]

output using a phone and lens 
Ubuntu 23.04 ubuntu tty!

ubuntu login:


OK Started snap.firefox.hook.configure.528e89e4-ficc-49c9-9e5e-6386fe86169b.scope.


Mounting var-snap-firefox-common-host\x2dhunspell.mount Mount unit for firefox, revision 2517 vie mount-control... OK Mounted var-snap-firefox-common-host\x2dhunspell.mount Hount unit for firefox, revision 2517 via mount-control.


DK1 Finished NetworkManager-wait-online.service Network Manager Hait Online.

I OK

OK] Reached target network-online.target Network is Online.



Started  update-notifier-download.timer Download data for packages that failed  at package install time. Started update-notifler-motd.timer Check to see  whether there is a new version of ubuntu available.


OK [ OK ] Reached target timers.target Timer Units.


I OK  1 Started cups-broused.service Make remote CUPS printers available  locally. Starting kerneloops.service Tool to automatically collect and  submit kernel crash signatures...

1 OK 1 Started whoopsie.service crash report submission.

LOK  Started kerneloops.service Tool to automatically collect and submit  kernel crash signatures. [ OK 1 Started snap.snap-store.hook.configure.a5e6b997-8987-4acc-b1e3-b6acdb665af1.scope. OK started snap.snapd-desktop-integration.hook.configure.21999ea1-fea9-46a8-af33-fa1df83bb78b.scope.

Ok started snap.ubuntu-desktop-installer.subiquity-server.service Service for snap application ubuntu-desktop-installer.subiquity-server.

Starting systemd-timedated.service-Time & Date Service.... [OK] Started systemd-timedated.service Time & Date Service.

I OK Finished snapd.seeded.service- Hait until snapd is fully seeded.

OK 1 Reached target multi-user.target Multi-User System.

Starting casper-md5check.service- casper-md5check Verify Live ISO checksums... Starting systemd-update-utmp-runlevel.service Record Runlevel Change in UTHP.

[ OK ] Finished systemd-update-utmp-runlevel.service Record Runlevel Change in UTMP.

Starting realnd.service Realm and Domain Configuration... OK] Started realnd.service Realm and Domain Configuration.

OK 1 Finished casper-md5check.service casper-md5check Verify Live ISO checksums.


 





[TABLE="class: cf wS"]
[TR]
[TD="class: amq"][/TD]
[TD="class: amr"][/TD]
[/TR]
[/TABLE]

---

### Post by Rubi1200 on 2023-10-05
You should wait for more precise instructions from MAFoElffen but I think he meant for you to try those commands from the GRUB menu you get when trying to boot normally.

In other words, remove the USB and try again once you restart the computer.

---

### Post by deci0000000000 on 2023-10-06
I have re-read and tried to understand, 

The part with at grub 2 boot, I cannot get to that point where I can get to the menu to press e so for me where I get to is

[LIST=1]
[*]press on button
[*]lenovo logo with to interupt normal start up press enter
[*]grub terminal appears
[/LIST]

If I type exit system resets, if I type boot I get error: you need to load kernel first

With a live usb ran the boot repair again to make sure I wasn't doing anything silly I did run this first this time 

sudo cryptsetup luksOpen /dev/nvme0n1p3 myvolume 

I noticed the output is different at the end 

[https://paste.ubuntu.com/p/sFj9NGhkN7/](https://paste.ubuntu.com/p/sFj9NGhkN7/)
Suggested repair The default repair of the Boot-Repair utility would not act on the boot.

Is there something else I am not doing that I should be doing?

---

### Post by deci0000000000 on 2023-10-07
Pharmacy came through so I am feeling a lot more with it today. Thank you all for the help but I will reinstall.

I will stick with 23.04 as from reading around others with Z16 thinkpads had issues on 22.04, I will keep the version upgrades going then sticking with the next LTS version.

I would have preferred to keep encryption as it is a laptop but it is not worth it for me to get this stuck.

---

