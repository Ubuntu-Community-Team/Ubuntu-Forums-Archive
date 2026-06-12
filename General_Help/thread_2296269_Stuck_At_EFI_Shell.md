---
title: "Stuck At EFI Shell"
date: 2015-09-24
forum: General Help
---

### Post by Neko_no_Nya on 2015-09-24
I hope this is the right place to post this.

I am currently dual booting Windows 7 and Ubuntu 14.04 from a single hard drive. I am using an MSI 970 Gaming motherboard and have been running with EUFI only enabled. Last night I had to boot into Windows 7 to do some game capture with my USB capture device. There is a little issue with this motherboard where sometimes the USB 3.0 ports won't detect anything you plug in. This was one of those times. The quick and dirty solution is to boot into the BIOS and either enable or disable the Overclock Genie depending on whether you have it on or off. Don't ask me why this fixes it. It just does. Apparently updating to the latest BIOS fixes the issue but I've been too lazy to do it.  I have used the dirty fix countless times and NEVER had a single issue doing it but last night was different.

After toggling the OC Genie, upon restart I was sent to the EFI shell. I get a message saying press ESC in xxx seconds to skip startup.nsh, any other key to continue. Both options just put me at Shell> and then an option to type something. I do get a post screen and am able to access the BIOS and boot menu with no problems. I searched online and it seems pretty much everyone who has this issue is running Windows 8 and has fastboot enabled. I am not running Win 8 and do not have fastboot enabled.

I didn't change anything else in the BIOS so I don't know what could have triggered this. If I pull up the boot menu I am only given the option of UEFI: Built-in EFI shell and enter setup which takes me into the BIOS. I am able to boot from the optical drive if I put in a bootable disc. Looking in the BIOS, I can see that my boot order is correct but when I click UEFI hard disk drive BBS priorities there is a list of 21 boot options. The first 16 are blank and the last five all say Ubuntu. I'm not sure what that is about.

Pretty much all the advice I find online is for people running Win 8 and fastboot and many of them can't even get into the BIOS. Obviously, this doesn't apply to me at all. So I'm kind of at loss for leads here.

Any help would be very much appreciated as I can't use my machine right now...

---

### Post by oldfred on 2015-09-24
Can you boot live installer from DVD or flash drive?

If so run this:
sudo efibootmgr -v

Is hard drive shown correctly in UEFI?
From Disks in live installer and icon in upper right check Smart Status of drive.

Other MSI posts:
 MSI UEFI bug work around A75MA-G55 UEFI boot entries disappear 
[http://forum-en.msi.com/index.php?topic=153411.0](http://forum-en.msi.com/index.php?topic=153411.0)
[http://forum-en.msi.com/](http://forum-en.msi.com/)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1129524](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1129524)
Disable MSI Z87 fast boot to get it to work
[http://ubuntuforums.org/showthread.php?t=2272131&p=13258725#post13258725](http://ubuntuforums.org/showthread.php?t=2272131&p=13258725#post13258725)

---

### Post by Neko_no_Nya on 2015-09-24
Yes, I can boot from a live cd (I haven't tried a flash drive).

I ran sudo efibootmgr -v and got this:

```
BootCurrent: 000E
Timeout: 1 seconds
BootOrder: 000E,0003,0000,0002,000A,0005,000D,0001
Boot0000  Windows Boot Manager    HD(1,800,32000,a9e70dbe-8858-4f74-b4b9-4155dfdb084f)File(\EFI\Microsoft\Boot\bootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...a................
Boot0001  Hard Drive     BIOS(2,0,00)..GO..NO........o.T.O.S.H.I.B.A. .D.T.0.1.A.C.A.3.0.0....................A...........................>..Gd-.;.A..MQ..L. . . . . . . . . . .Y. .5.4.B.U.U.5.S.G........BO
Boot0002  ubuntu    HD(1,800,32000,a9e70dbe-8858-4f74-b4b9-4155dfdb084f)File(\EFI\ubuntu\shimx64.efi)
Boot0003* UEFI: Built-in EFI Shell     Vendor(5023b95c-db26-429b-a648-bd47664c8012,)..BO
Boot0005  CD/DVD Drive     BIOS(3,0,00)..GO..NO........o.H.L.-.D.T.-.S.T. .B.D.-.R.E. . .W.H.1.0.L.S.3.0....................A...........................>..Gd-.;.A..MQ..L.9.K.A.3.F.5.4.8.2.1. .0. . . . . . . . ........BO..NO........o.P.L.D.S. .D.V.D.+./.-.R.W. .D.H.-.1.6.A.6.S....................A...........................>..Gd-.;.A..MQ..L. . . . . . . . . . . . . . . . . . . . ........BO
Boot000A  ubuntu    HD(1,800,32000,a9e70dbe-8858-4f74-b4b9-4155dfdb084f)File(\EFI\Ubuntu\grubx64.efi)
Boot000D  Unknown Device     BIOS(8,0,00)..GO..NO........a. .F.C.R.-.H.S.3. .-.0.1...0.0....................A.......................4..Gd-.;.A..MQ..L. .F.C.R.-.H.S.3. .-.0.1...0.0........BO..NO........i. .F.C.R.-.H.S.3. .-.1.1...0.0....................A...............................4..Gd-.;.A..MQ..L. .F.C.R.-.H.S.3. .-.1.1...0.0........BO..NO........i. .F.C.R.-.H.S.3. .-.2.1...0.0....................A...............................4..Gd-.;.A..MQ..L. .F.C.R.-.H.S.3. .-.2.1...0.0........BO..NO........i. .F.C.R.-.H.S.3. .-.3.1...0.0....................A...............................4..Gd-.;.A..MQ..L. .F.C.R.-.H.S.3. .-.3.1...0.0........BO
Boot000E* UEFI: HL-DT-ST BD-RE  WH10LS30    ACPI(a0341d0,0)PCI(11,0)03120a000200ffff0000CD-ROM(1,77483,1240)..BO 
```

As you can see, it is quite a garbled mess. But if I am reading it correct, It is showing EFI. Am I missing something or is there no Windows entry? I see the Windows boot manager but no Windows. I can access the partition just fine in a live session so I don't know what's up. Could this be the cause? I wouldn't think it should matter because grub should come up anyway.

I ran the quick smart test for my drive and it came back saying nothing is above any threshold. I am running the long scan now and it probably going to take quite a while. Is there something in particular I'm looking for?

I followed the links you gave but the MSI one just gives me an error, even after creating an account. The launch pad page work arounds don't work for me. They suggest changing from EUFI to legacy but I have my OS install set up for EUFI so I have to have the BIOS set to EUFI, right? I did try changing it to legacy for kicks but that didn't work. I'm not sure if I have acpi enabled or not. I'm running the smart test right now so I can't reboot into the BIOS to check. It has been at 10% for some time now. Is that normal?

The other link was about disabling fast boot and I already have it disabled. In fact, I've never had it enabled. I've been running these installs for months and didn't make any changes in the BIOS other than the OC toggling. I haven't done any modifications to either OS either.

I'm looking through the last link you gave me now. Hopefully I'll find something in there. Edit: I didn't really find anything in there pertaining to my issue. It seems to be more about getting EUFI set up for the first time. I'm pretty sure I have everything set up properly since everything has been working up to this point.

---

### Post by oldfred on 2015-09-24
You have many UEFI boot entries but only two have the *.
I believe the * means they are the ones that can be used or are currently working.
Windows boot manager is Windows.

I really would suggest updating UEFI from MSI.
And I would stay with UEFI. 
Ubuntu can easily be converted from UEFI to BIOS, but you cannot convert Windows without erasing drive and reinstalling Windows in BIOS mode with MBR partitioning.

If you run this, does it show your partitions and installs?
 Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by Neko_no_Nya on 2015-09-25
That would make sense that only two are able to be used. I'm guessing that is my two partitions that I run Windows and Ubuntu from. I actually have a total of six partitions. Windows created two during install. One had something to do with UEFI and I forget the other. The last two are the swap partition and my file storage partition.

Here is the link for the test: [http://paste.ubuntu.com/12551494/](http://paste.ubuntu.com/12551494/)

I don't know why it says my sixth partition has Vista. That is most certainly not the case. It just an NTFS partition I use for storage. 

I have been using UEFI since I upgraded my hard drive and did a fresh install of Win and Ubuntu. I know I installed them in UEFI mode because I followed a guide to the letter. I'm not sure if I can find the guide now though. This problem just seems so random. I don't get why this started seemingly out of nowhere.

I do plan on updating the BIOS. After this fiasco, I will probably do it right away. I just want to fix this problem first. I don't want to introduce any new variables if it can be avoided.

---

### Post by oldfred on 2015-09-25
Installs looks normal.
With your 3TB drive you have to have gpt partitioning and then Windows only installs in UEFI mode.
Some drive mfg have some convoluted way to make MBR for XP compatibility and then Linux has issues as it is not standard.

I am thinking it must be some setting in UEFI.
Some laptops require you to put in passwork & then set trust on any added .efi files in the ESP to let UEFI boot them.

Your two boot files you want to use Windows & Ubuntu do not have the *. If I list mine, all entries have the *.

I have never needed to use it but efibootmgr has  a -a switch.
 [http://linux.die.net/man/8/efibootmgr](http://linux.die.net/man/8/efibootmgr)

**-a | --active** Sets bootnum active

I have not seen an example but it should be something like.
sudo efibootmgr -a 0002
And then list them to see if 0002 has *, then also do for Windows entry.

I might houseclean some older kernels.
With very large drives I also prefer to have smaller system partitions & larger data partitions. On the one system with Windows and a 1TB drive I have 50GB for Windows & 25GB for / (root) with all data in data partition(s) and space for other Ubuntu versions. Then hard drive does not have to jump all over drive to find system files. There used to be a bug where grub would not boot a kernel beyond some value like 650GB on a drive. The ext4 format can locate files anywhere in partition.

I do not suggest a separate /boot unless using LVM or maybe RAID. If a new user the separate /home is easier to set up as you can do that during install. But I use separate data partition for all my files using in /home and keep /home inside /.
 suggested partitions for just Ubuntu on 3TB drive.
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
Another advanced suggestion from TheFu with Multiple / (root) - Post #5 similar to what I actually do
[http://ubuntuforums.org/showthread.php?t=2170308](http://ubuntuforums.org/showthread.php?t=2170308)

---

### Post by Neko_no_Nya on 2015-09-25
Thank you for all your help so far. I feel like I am really close to getting this worked out. I added the boot flag to both the Windows and Ubuntu partitions like you said to do. I discovered that simply inputting > sudo efibootmgr -a XXXX didn't work. After looking around a bit in the command list I realized that you first have to use "-b" to specify the partition. So you end up with a command looking like > sudo efibootmgr -b XXXX -a. XXXX being the partition number. Using that command on both partitions I was able to boot into both Windows and Ubuntu again. But the system would automatically boot straight into Windows. GRUB wasn't coming up. Into order to pull up GRUB I had to pull up the boot device selector in the BIOS and then select Ubuntu.

So, while this method works, it is a little bit awkward. I found that when checking the boot order with efibootmgr showed Windows was set to boot first. I realized that I needed to change the boot order using efibootmgr if I wanted GRUB to come up. This is where things started to go wrong. I used the command > sudo efibootmgr -O -o X,X,X,X X again being the partition numbers. -O was to delete my boot order and -o is to designate a new one. This seemed to work. > sudo efibootmgr -v would now show my partitions that were designated to be bootable were int he proper order. Ubuntu was now first and still had * next to it. Windows was second.

I rebooted the system, fully expecting to see GRUB. Instead it booted straight into Windows again. I used the boot selector to pull up Ubuntu and typed > sudo efibootmgr -v in a terminal again. My boot order had reverted when I rebooted. Windows was once again set to boot before Ubuntu. I re-created this a couple of times. Basically, whenever I reboot, the boot order I set with efibootmgr reverts. I did some searching and found someone claiming that the BIOS can sometimes try to overwrite these settings and you need to manually set the boot order through it. I entered the BIOS and my boot order was correct. The weird thing was that my hard drive no longer just listed the make and model but now in addition had Ubuntu listed right after it. I found this to be very weird. Remember those BBS priorities I mentioned before? I checked them and now every single one is filled with Ubuntu instead of the last five. If I click one, there isn't anything else to select except Ubuntu.

With my BIOS, if you select something and don't actually change it but just re-select whatever was already selected, it still asks you to save your changes. I don't know why but I decided to say yes even though I know I didn't change anything. I'm glad I did this because I think it may shed more light on my situation. Once I rebooted I was back at that EFI shell screen again. So basically, what I realized is that every time I save changes (even if I didn't actually change anything), my UEFI boot settings get messed up/overwritten. That is why when I toggled my OC Genie and saved changes I was suddenly stuck at the EFI shell again. And like I said, this is a new problem. I have been toggling that button, saving changes, and hopping between operating systems for months without this problem.

I went back in using efibootmgr and made it so I can boot from both the Windows and Ubuntu partitions again. But changing the boot order still reverts upon reboot so I'm stuck using the boot device selector.

I'm not sure where to go from here other than just a new install but I really don't want to do that.

---

### Post by oldfred on 2015-09-25
I did not think Windows 7 reset boot order, but the newer versions of Windows do.
There are a variety of work arounds. 
If using mostly Windows you can add an entry to BCD.
If you want to usually boot Ubuntu you can copy grubx64.efi into /EFI/Boot and rename to bootx64.efi. Back up current copy of boox64.efi, but it probably is just a copy of Windows /EFI/Microsoft/bootmgfw.efi, you can check file size.

It does not look like you have a hard drive UEFI entry, just BIOS. Normally if you have bootx64.efi that is a default or fallback in UEFI to boot if nothing else boots.

Work arounds, also similar info in link in my signature.
 [http://ubuntuforums.org/showthread.php?t=2234019](http://ubuntuforums.org/showthread.php?t=2234019)
      
 As noted on the Arch UEFI site:
On some UEFI systems the only possible way to launch UEFI application on boot (if it does not have custom entry in UEFI boot menu) is to put it in this fixed location: <EFI SYSTEM PARTITION>/EFI/BOOT/BOOTX64.EFI (for 64-bit x86 system)
Users who manually moved efi files around see post #6
[http://ubuntuforums.org/showthread.php?t=2101840](http://ubuntuforums.org/showthread.php?t=2101840)
[http://ubuntuforums.org/showthread.php?t=2219452](http://ubuntuforums.org/showthread.php?t=2219452)

this assumes ESP is sda1 otherwise you have to add which drive, partition.
# You may need new hard drive entry:
 sudo efibootmgr -c -L "UEFI Hard drive" -l "\EFI\Boot\bootx64.efi"

---

