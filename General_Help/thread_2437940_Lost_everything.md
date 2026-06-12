---
title: "Lost everything"
date: 2020-03-03
forum: General Help
---

### Post by torbentf on 2020-03-03
Hi,
I have lost all my data. It is if I log in on a completely new Ubuntu. I am not aware of having deleted anything and even if I had I should find the data in the rubbish bin, but that is empty.
I had backup on a Toshiba hard drive but I cant access that now.
Can anyone help?
Best regard
torben

---

### Post by Autodave on 2020-03-03
Can we have some specs on your machine and what version of 'buntu that you are using?

---

### Post by torbentf on 2020-03-03
Hi,
The machine is an ASUS X750J portable and UBUNTU is UBUNTU-18.04.2-Desktop-amd64.
torben

---

### Post by CelticWarrior on 2020-03-03
Thank you.

Also helpful to know is what that "everything" is and where it was supposed to be, what do you see instead...

---

### Post by HermanAB on 2020-03-03
What I would do:
Boot from an install disk.
Do not install obviously - just look at the hard disk drive and see what is going on.
Backup any still unbacked data.
Then re-install if I can’t figure out how to fix the problem in a reasonable time.

---

### Post by oldfred on 2020-03-03
While more for boot issues & grub related, it does dump a lot of info on your configuration.
Do not run any suggested fixes, at least until someone has reviewed report.

May be best to see details, use ppa version with your live installer (2nd option) or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by deadflowr on 2020-03-03
> I had backup on a Toshiba hard drive but I cant access that now.
Why not?

---

### Post by torbentf on 2020-03-03
Hi,
The repair did not work, but I have a URL:

[http://paste.ubuntu.com/p/ScqxJB9jz3/](http://paste.ubuntu.com/p/ScqxJB9jz3/)

When I try and restore backup I get:

Storage location not available/Waiting for '1.0 TB Volume' to become connected...

I hope that helps.
Best regard
torben

The machine is an ASUS X750J portable and UBUNTU is UBUNTU-18.04.2-Desktop-amd64.
torben

---

### Post by oldfred on 2020-03-03
Looks like typical default UEFI install with just ESP & / (root).
With large 1TB drive like yours often better to have smaller / & then large /home, but not required. 
Default install of just / was back when 100GB drive was large and most users were dual booting with Windows.

You did not show the other drive? Is it not an internal drive or a USB connected drive?

It also looks like you set grub timeout to 0, so it immediately boots Ubuntu without grub menu.
But that also means you just about cannot get to grub menu to try to boot in recovery mode. I like to set to 3 sec, so if I am fast I can get to grub menu.

You now show unknown entries in UEFI boot menu. That is because Acer requires you to set a password and set "trust" and rename those entries. They are duplicates, so not required to rename, probably can just delete.

---

### Post by torbentf on 2020-03-03
Hi oldfred,
I ran boot-repair and got an error. I sent the URL to [email]boot.repair@gmail.com[/email].
I tried to start ubuntu anyway and it did not work.
I have the boot seq. starting with "EFI File Boot 0: qqqqq"
I checked the GRUB Time Delay and it is 10 sec.
Can I do more?
Best regards
torben

---

### Post by torbentf on 2020-03-03
Hi oldfred,
How can I see if it starts on "sda1/EFI/ubuntu/shimx64.efi"?
torben

---

### Post by torbentf on 2020-03-03
Hi oldfred,
Where can I see if "sda1/EFI/ubuntu/shimx64.efi" is used?
Is there any difference between "Power off" and "Restart"?
torben

---

### Post by oldfred on 2020-03-03
Full power off, or cold boot will normally let you get into UEFI settings or one time boot key if UEFI fast boot is on. You often have to unplug system, remove battery if laptop, and hold power switch on for 10 sec or so to drain any remaining power.

When fast boot is on, system assumes no changes and skips the scan of hardware & write of that info to drive for operating system.

Warm boot or a reboot just starts default UEFI setting. You can see that in your Boot-Repair summary report, line 1019, or with this from any working Ubuntu.
sudo efibootmgr -v

It is showing your qqqq entry as default boot or 0002.

Lines 998 & and 1010 show error code of 0 or no error.
But error seems to be verbose install.
I assume the reinstall of grub created the unknown entries.

I might delete 1, 2, 3, & 4 UEFI entries as only 0000 is required & you have renamed it to ubuntu.

# from liveDVD or flash booted in UEFI mode and use efibootmgr
sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:, with Ubuntu you need sudo, others must be at root. some need all 4 hex chars, others only need significant digits
sudo efibootmgr -b XXXX -B
man efibootmgr
[http://linux.die.net/man/8/efibootmgr](http://linux.die.net/man/8/efibootmgr)

---

### Post by torbentf on 2020-03-04
Hi oldfred,
I get:

torben@torben-Aspire-E5-773G:~$ sudo efibootmgr -v
[sudo] password for torben: 
BootCurrent: 0002
Timeout: 0 seconds
BootOrder: 2001,0002,0001,2002,2003
Boot0000* ubuntu    HD(1,GPT,f9f7beb0-0f7c-4bf6-a5e8-eeb7a9bae9e0,0x800,0x100000)/File(\EFI\ubuntu\shimx64.efi)
Boot0001* Command Linpus lite    HD(1,GPT,f9f7beb0-0f7c-4bf6-a5e8-eeb7a9bae9e0,0x800,0x100000)/File(\EFI\Boot\bootx64.efi)RC
Boot0002* qqqqq    PciRoot(0x0)/Pci(0x17,0x0)/Sata(0,0,0)/HD(1,GPT,f9f7beb0-0f7c-4bf6-a5e8-eeb7a9bae9e0,0x800,0x100000)/File(\EFI\ubuntu\shimx64.efi)A01 ..
Boot0003* USB CDROM: SlimtypeDVD A  DS8A1P    PciRoot(0x0)/Pci(0x14,0x0)/USB(0,0)/CDROM(1,0xe02b3,0x1240)RC
Boot0004* Unknown Device:     HD(1,GPT,f9f7beb0-0f7c-4bf6-a5e8-eeb7a9bae9e0,0x800,0x100000)/File(\EFI\ubuntu\shimx64.efi)RC
Boot2001* EFI USB Device    RC
Boot2002* EFI DVD/CDROM    RC
Boot2003* EFI Network    RC

So Timeout is 0 sec, and that is/maybe a problem, right?

torben@torben-Aspire-E5-773G:~$ sudo efibootmgr -t 10
[sudo] password for torben: 
Could not set Timeout: Invalid argument

So I cant chanage it, but that seems to be an error/a bug?

How do I get "sudo efibootmgr -v" to give the line numbers?

I can't run the live version from my old installation dvd. If I try, I still only get the bad Ubuntu. 

Would'nt it be easiest to download and install a new Ubuntu? I assume that would'nt interfere with my data - if they are still there?
Best regards
torben

---

### Post by dragonfly41 on 2020-03-04
[COLOR=#000000]I will chip in with some ideas although - *caveat empto*r - I am a Dell user and not an ASUS user.[/COLOR]

[COLOR=#000000]From ASUS manual find how to enable/disable boot options. In Dell it is F2 when starting up.[/COLOR]
[COLOR=#000000]You can deselect (untick) a number of boot options for that boot session (for example you might choose only qqqqq or dvd options). They can be restored at next boot session using F2.[/COLOR]

[COLOR=#000000]Your efibootmgr output shows an asterisk (bootable) against every (8) item in the list. That is a lot of bootable options.[/COLOR]

[COLOR=#000000]My efibootmgr list is more selective - only a few asterisks.[/COLOR]

> [COLOR=#000000]I can't run the live version from my old installation [/COLOR][COLOR=#000000]dvd[/COLOR][COLOR=#000000]. If I try, I still only get the bad Ubuntu.[/COLOR]

[COLOR=#000000]If you wish to try LiveDVD just select only DVD in boot options.[/COLOR]

[COLOR=#000000]You appear to have two?[/COLOR]

[COLOR=#000000]Boot0003[/COLOR][COLOR=#000000]* USB [/COLOR][COLOR=#000000]CDROM[/COLOR][COLOR=#000000]: [/COLOR][COLOR=#000000]SlimtypeDVD[/COLOR][COLOR=#000000] A [/COLOR][COLOR=#000000]DS8A1P[/COLOR][COLOR=#000000]PciRoot[/COLOR][COLOR=#000000](0x0)/[/COLOR][COLOR=#000000]Pci[/COLOR][COLOR=#000000](0x14,0x0)/USB(0,0)/[/COLOR][COLOR=#000000]CDROM[/COLOR][COLOR=#000000](1,0xe02b3,0x1240)RC[/COLOR]

[COLOR=#000000]Boot2002[/COLOR][COLOR=#000000]* [/COLOR][COLOR=#000000]EFI[/COLOR][COLOR=#000000] DVD/[/COLOR][COLOR=#000000]CDROM[/COLOR][COLOR=#000000] RC[/COLOR]


[COLOR=#000000]You could try advancing DVD to start of boot order?[/COLOR]

[COLOR=#000000]If this does not work I will offer another suggestion.[/COLOR]

---

### Post by oldfred on 2020-03-04
The timeout is in the grub menu. Line 548 in your Boot-Repair report.

cat /etc/default/grub

Default is 10, I changed mine to 3
GRUB_TIMEOUT=3

Only one of my systems have I changed UEFI timeout, but only from within UEFI, not using efibootmgr.

---

### Post by CatKiller on 2020-03-04
A couple of things;

You *can* still invoke the Grub menu even if the timeout is set to 0 by spamming the button. It's easier to just change the timeout setting if you're going to need it more than once, though.

You can reboot into the UEFI setup if you've got fast boot turned on with ```
sudo systemctl reboot --firmware-setup
```

---

### Post by torbentf on 2020-03-04
Hi Everybody,
I made a new installation DVD and tried live installation - still no data. I then installed Ubuntu - still no data and no backup data. So I guess that the data are lost - I wonder what happened.
Thank you for your help.
torben

---

### Post by oldfred on 2020-03-04
Depending on how you reinstalled, you may have erased all data on sda.
But Boot-Repair report showed sdb's Linux partition. Are you not able to mount it?
You may just need fsck?

---

### Post by torbentf on 2020-03-04
Hi oldfred,
It appears that I have installed the new Ubuntu alongside the old one. 

sda1 og sda2are already mounted

I have tried the fsck command in that system
:

torben@torben-Aspire-E5-773G:~$ fsck
fsck from util-linux 2.31.1
e2fsck 1.44.1 (24-Mar-2018)
/dev/sda2 is mounted.



WARNING!!!  The filesystem is mounted.   If you continue you ***WILL***
cause ***SEVERE*** filesystem damage.


Do you really want to continue<n>? no
check aborted.
fsck.fat 4.1 (2017-01-24)
open: Permission denied

I did not dare to continue - what do you suggest?

I still cant find the files in general, but I may have found the backup files:

torben@torben-Aspire-E5-773G:~$ ls /media/torben/350D-ECB9/torben-Aspire-E5-773G
duplicity-full.20200304T163210Z.manifest.gpg
duplicity-full.20200304T163210Z.vol1.difftar.gpg
duplicity-full-signatures.20200304T163210Z.sigtar.gpg

But the contents are peculiar:
2J#&#65533;M&#65533;&#65533;&#65533;(&#65533;y&#65533;Gk&#65533;n3<7&#65533;r&#65533;&#65533;&#65533;&#65533;=3&#65533;&#1176;4+&#65533;!&#65533;D&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;*&#65533;&#65533;9n&#65533;2&#65533;&#65533;t77]R3
                                                          &#65533;Dj,&#65533;yxQ\&#65533;&#65533;&#65533;&#65533;&#65533;U&#65533;?&#65533;<L[&#65533;&#891;#&#65533;&#65533;&#832;&#65533;&#65533;&#65533;&#1877;&#547;A&#65533;&#65533;c&#65533;&#65533;&#65533;&#311;&#1302;&#65533;&#65533;
&#643;&#65533;&#65533;&#65533;&#65533;5&#65533;&#65533;i&#65533;Z?YD&#65533;}&#65533;&#65533;
i&#65533;&#65533;&#65533;w&#65533;[&#65533;&#65533;'&#65533;g3&#65533;&#65533;&#65533;&#65533;P&#519;&#65533;H&#65533;&#65533;x&#65533;*`fT&#65533;3&#65533;q&#65533;&#65533;&#65533;3&#65533;H&#294;r&#65533;z&#65533;&#65533;&#65533;z&#65533;c0&#65533;E.|&#65533;&#65533;&#1205;y&#65533;&#65533;&#65533;&#65533;g&#65533;&#65533;{&#65533;40&#65533;}v&#65533;&#65533;1&#65533;M&#65533;!&#65533;&#65533;&#65533;f:&#65533;-=&#65533;&#65533;zJs&#65533;&#1763;&#65533;&#65533;&#65533;S&#65533;&#65533;
:&#65533;#&#65533;&#65533;TLJ&#65533;p.&#1315;I&#65533;V,I&#65533;&#65533;&#65533;&#2889;&#65533;  &#65533;&#65533;&#65533;m&#65533;t&#65533;&#65533;&#65533;>&#65533;7j&#65533;N&#65533;;B&#65533;+Y&#65533;&#65533;&#65533;w&#65533;&#65533;z&#65533;-&#65533;&#65533;&#65533;Qez3=&#1842;&#65533;&#65533;&#65533;

Is it worth while to continue?
torben

---

### Post by torbentf on 2020-03-05
Hi oldfred,
I did a umount and: torben@torben-Aspire-E5-773G:~$ sudo fsck /dev/sdb6
fsck from util-linux 2.31.1
e2fsck 1.44.1 (24-Mar-2018)
/dev/sdb6: clean, 185609/30433280 files, 4058434/121728256 blocks
 No return code, but the file disappeared (not in fstab, bot in lsblk). What happened? Can I get it back?

the files appear to be there:

torben@torben-Aspire-E5-773G:~$ ls /media/torben/350D-ECB9/torben-Aspire-E5-773G
duplicity-full.20200304T163210Z.manifest.gpg
duplicity-full.20200304T163210Z.vol1.difftar.gpg
duplicity-full-signatures.20200304T163210Z.sigtar.gpg

torben

---

### Post by torbentf on 2020-03-05
Hi oldfred,
I did a umount and: torben@torben-Aspire-E5-773G:~$ sudo fsck /dev/sdb6
fsck from util-linux 2.31.1
e2fsck 1.44.1 (24-Mar-2018)
/dev/sdb6: clean, 185609/30433280 files, 4058434/121728256 blocks
 No return code, but the file disappeared (not in fstab, bot in lsblk). What happened? Can I get it back?

the files appear to be there:

torben@torben-Aspire-E5-773G:~$ ls /media/torben/350D-ECB9/torben-Aspire-E5-773G
duplicity-full.20200304T163210Z.manifest.gpg
duplicity-full.20200304T163210Z.vol1.difftar.gpg
duplicity-full-signatures.20200304T163210Z.sigtar.gpg

torben

---

### Post by oldfred on 2020-03-05
I do not know duplicity, I assume it is a compressed image.

Many years ago with a floppy drive I had damage on the partition table and could not read any of the data with normal tools.
Now drives are a lot cheaper so space is cheap & I will not use compression. Also makes it easier to just restore one file.

---

### Post by CatKiller on 2020-03-05
> **oldfred said:**
> I do not know duplicity, I assume it is a compressed image.


Versioned files packaged with tar. The easiest way to restore them is to just use duplicity again (or Déjà Dup). Specify which date's files you want extracted and where to and they'll magically appear.

---

### Post by deadflowr on 2020-03-05
Based on the content output if duplicity is installed take a look at what
```
duplicity collection-status file:///media/torben/350D-ECB9/torben-Aspire-E5-773G
```
But on the disk spaced used for the partition in question it doesn't look like anything was actually backed up.
df output from the pastebin shows this:
```
/dev/sdb1      vfat      932G   32K  932G   1% /media/torben/350D-ECB9
```
meaning it's only using 32K of space.

Unfortunately you seemed to have run into issues before:
[https://ubuntuforums.org/showthread.php?t=2394680]("https://ubuntuforums.org/showthread.php?t=2394680")
And we never learned how anything was resolved only that you stated you got it right.

---

### Post by torbentf on 2020-03-09
Hi everybody,
I have given up restoring lost files. I have backed up the files I have in the re-installed system after having formatted the usb hard disk:

sdb      8:16   0 931.5G  0 disk 
&#9500;&#9472;sdb1   8:17   0 931.5G  0 part /media/torben/4C7D57E86EC2BCC6
&#9500;&#9472;sdb2   8:18   0  47.1M  0 part 
&#9492;&#9472;sdb3   8:19   0 931.5G  0 part
 
I am surprised by the sdb - how can there be 3 partitions whos' spaces do not add up?
torben


The backup appears to work so maybe I should leave it at that.
torben

---

### Post by oldfred on 2020-03-09
If sdb1 was FAT32, the largest file you could store is 4GB, so if compressed image & large, it is just truncated, normaly with no warning.
Do not use FAT32 for larger partitions. (I did way back and lost many backups, but luckily did not need them.)

---

### Post by torbentf on 2020-03-10
Hi oldfred.
I have formatted the Toshiba with ntfs.
torben

---

