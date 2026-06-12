---
title: "Ubuntu 19.10 very slow"
date: 2020-04-29
forum: General Help
---

### Post by ogola89 on 2020-04-29
Hi Guys,  My Ubuntu, especially of late, has been very slow. Freezing a few times an hour for a few minutes (even just froze while typing this out) - to the point where the mouse is unresponsive and alt+f2 or any other commands do not work until the system is back. I have a swap size of 18gb, RAM is 8GB, intel i5 processor and integrated Skylake GT2 HD Graphics 520 graphics card. Having read around, some graphics card driver incompatibilities can be the issue, but I think mine is fine. When I type ```
lshw -c video 
```I get the following output:  (


```

base) Ubuntu:~$ sudo lshw -c video   
*-display                         
description: VGA compatible controller        
product: Skylake GT2 [HD Graphics 520]        
vendor: Intel Corporation        
physical id: 2        
bus info: pci@0000:00:02.0        
version: 07        
width: 64 bits        
clock: 33MHz        
capabilities: pciexpress msi pm vga_controller bus_master cap_list rom        
configuration: driver=i915 latency=0        
resources: irq:127 
memory:f0000000-f0ffffff memory:e0000000-efffffff ioport:4000(size=64) memory:c0000-dffff  
```


This freezing occurs often when I have a browser open (currently using firefox with about 14 tabs. However I use NoScript to disable JavaScript resources on most pages). All I have open is the browser, R-studio and the terminal open but yet it is very slow.  Compared to the same machine when I dual boot into windows (I must say that windows is on SSD and Ubuntu on an external HD) - the difference is immense. I can have 5 different IDEs open, about 4 different browser windows with 50+ tabs open and multiple processes and it doesn't get slow. I love Ubuntu, and was very quick at the beginning, but it seems when it is pushed even slightly it hangs and freezes.  Is there a way to diagnose the cause and what to do about it?  I know there are many similar posts, but following the instructions haven't been able to help me

---

### Post by CelticWarrior on 2020-04-29
> I have a swap size of 18gb
This is an absurd waste of space and a contributing factor.

---

### Post by oldfred on 2020-04-29
May be best to see details, use ppa version with your live installer (2nd option) or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

I typically only open 3 or 4 tabs at once. But just added new NVMe drive over older standard smaller SSD. My z170 system now is very fast. Something about space between keyboard and chair gets slower every year, though.

---

### Post by ogola89 on 2020-04-29
> **oldfred said:**
> May be best to see details, use ppa version with your live installer (2nd option) or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

I typically only open 3 or 4 tabs at once. But just added new NVMe drive over older standard smaller SSD. My z170 system now is very fast. Something about space between keyboard and chair gets slower every year, though.

Here is the link:
[https://paste.ubuntu.com/p/VhrT8gWs5n/](https://paste.ubuntu.com/p/VhrT8gWs5n/)

---

### Post by ogola89 on 2020-04-29
> **CelticWarrior said:**
> This is an absurd waste of space and a contributing factor.

What's a good amount for swap? I have a 4tb HD (2TB allocated to Ubuntu). I did this so I could handle large genetic files.

Also, the freezing was worse without swap, as about a week or two ago, I realised I had set a swap partition but it was off all the time. Those times, it would just freeze and would require a hard reboot. The swap has given the ability for it to come out again.

---

### Post by Impavidus on 2020-04-29
Instead of listing the applications you run that shouldn't cause too much memory usage, have a look at actual memory usage:```
free -m
```You can also get data per process using```
top
```Use < > to select the column to sort, q to exit. Interpretation may not be straightforward, as some applications (web browsers in particular) may consist of multiple processes and memory can be shared by multiple processes.

---

### Post by CelticWarrior on 2020-04-29
> **ogola89 said:**
> What's a good amount for swap? I have a 4tb HD (2TB allocated to Ubuntu). I did this so I could handle large genetic files.

Also, the freezing was worse without swap, as about a week or two ago, I realised I had set a swap partition but it was off all the time. Those times, it would just freeze and would require a hard reboot. The swap has given the ability for it to come out again.

As a general "rule" for general usage, the more RAM you have the less swap is needed, but it's always good to have some. For general use with 8GB RAM (and not hibernating, something you shouldn't do anyway) no more than 2GB swap is needed. Now, swapping to an external HDD is the worst possible scenario.

And unless your SSD is too small, as in 64GB small, you would be better installing both OSes on the SSD and use the external 4TB HDD for data only with one single shared NTFS partitions or different partitions with different file systems for optimization, it all depends on specific usage scenarios.

You can't compare between OSes when Windows has the best possible situation - system partition and pagefile in a fast internal SSD - and Ubuntu in the worst - system partitions and swap in a slow external HDD -.

---

### Post by oldfred on 2020-04-29
Most UEFI will not work with more than one ESP - efi system partition per device. I believe technically UEFI does allow it.
Ever case I have seen where users want two ESP, they just create a second FAT32 partition and move boot flag/esp flag back & forth. Actually grub does not care and will find boot files in the FAT32 and boot them. Really on seen two FAT32 where user wanted two separate installs of Windows & direct boot from grub.

Or remove boot/esp flags from sda6, you want sda1 as ESP on sda drive.
You have a bios_grub partition, sda5 on sda also. That is only for BIOS boot of grub from a gpt partitioned drive. You can delete that also.
You also have Windows BIOS boot loaders in gpt's protective MBR. That will never be used, or should not as long as you do not attempt to boot in BIOS mode. Windows only boots in UEFI mode from gpt partitioned drives.

I do like to have an ESP on every drive.
Windows typically installs it UEFI boot files into the drive (ESP) selected as default boot in UEFI.
Ubuntu installs UEFI boot files into ESP on first drive usually sda or first NVMe drive. You often have to disconnect or in UEFI disable first drive, if you want grub on second drive. Or:
Posted work around to manually unmount & mount correct ESP during install #23 & #26
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)
Ubuntu Installer uses wrong bootloader location for USB/sdb UEFI installs 
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1173457](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1173457)

You also have grub installed to PBR - partition boot sector of sda8. That will never be used.
You should always select a drive in UEFI boot mode, so grub installs into the ESP on that drive.
Only issue has been Ubiquity installer only uses first drive. But reinstall or manual install of grub in UEFI mode can be to any drive's ESP.

Line 683 in report:
> The disk contains an unclean file system (0, 0).
Metadata kept in Windows cache, refused to mount.
Falling back to read-only mount because the NTFS partition is in an
unsafe state. Please resume and shutdown Windows fully (no hibernation
or fast restarting.)

You need to turn off Windows fast start up if dual booting.
Fast Start up off (always on hibernation), note that Windows turns this back on with updates, SHIFT + Shut down button
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)
[https://www.windowscentral.com/how-disable-windows-10-fast-startup](https://www.windowscentral.com/how-disable-windows-10-fast-startup)

---

### Post by ogola89 on 2020-04-30
> **oldfred said:**
> Most UEFI will not work with more than one ESP - efi system partition per device. I believe technically UEFI does allow it.Ever case I have seen where users want two ESP, they just create a second FAT32 partition and move boot flag/esp flag back & forth. Actually grub does not care and will find boot files in the FAT32 and boot them. Really on seen two FAT32 where user wanted two separate installs of Windows & direct boot from grub.Or remove boot/esp flags from sda6, you want sda1 as ESP on sda drive.You have a bios_grub partition, sda5 on sda also. That is only for BIOS boot of grub from a gpt partitioned drive. You can delete that also.You also have Windows BIOS boot loaders in gpt's protective MBR. That will never be used, or should not as long as you do not attempt to boot in BIOS mode. Windows only boots in UEFI mode from gpt partitioned drives.I do like to have an ESP on every drive.Windows typically installs it UEFI boot files into the drive (ESP) selected as default boot in UEFI.Ubuntu installs UEFI boot files into ESP on first drive usually sda or first NVMe drive. You often have to disconnect or in UEFI disable first drive, if you want grub on second drive. Or:Posted work around to manually unmount & mount correct ESP during install #23 & #26[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)Ubuntu Installer uses wrong bootloader location for USB/sdb UEFI installs [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1173457](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1173457)You also have grub installed to PBR - partition boot sector of sda8. That will never be used.You should always select a drive in UEFI boot mode, so grub installs into the ESP on that drive.Only issue has been Ubiquity installer only uses first drive. But reinstall or manual install of grub in UEFI mode can be to any drive's ESP.Line 683 in report:You need to turn off Windows fast start up if dual booting.Fast Start up off (always on hibernation), note that Windows turns this back on with updates, SHIFT + Shut down button[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)[https://www.windowscentral.com/how-disable-windows-10-fast-startup](https://www.windowscentral.com/how-disable-windows-10-fast-startup)This might be a bit of a silly question, but does the grub menu and boot configuration affect the performance once booted? Just saying that it's not the startup I am worried about, it's the actual running once booted.Today for example, I had a complete crash with just 4 tabs open (3 were just pure text no ads) and opened visual studio. Now I know that windows is on an SSD and you cant compare their performances to be anywhere near equal, but what causes my laptop to crash is magnitudes less in Ubuntu than in Windows (which seems to almost never crash nomatter how much abuse I heap on it).

---

### Post by oldfred on 2020-04-30
Booting is different than running.
Only issue in booting may be if your system needs a boot parameter.
Have seen systems that overfilled log files without boot parameter.

What brand motherboard?
What specific model video card.

---

### Post by ogola89 on 2020-04-30
> **oldfred said:**
> Booting is different than running.
Only issue in booting may be if your system needs a boot parameter.
Have seen systems that overfilled log files without boot parameter.

What brand motherboard?
What specific model video card.

Yea I can deal with the booting as it is just a one off. I don't mind waiting 3 minutes to boot if it means I don't get regular hangs of 3< a few times an hour [https://ubuntuforums.org/images/smilies/icon_razz.gif](https://ubuntuforums.org/images/smilies/icon_razz.gif)

Short summary of my machine:

System Model    HP ProBook 450 G3
System Type    x64-based PC
System SKU    2SY41ES#ABU

BIOS: N78 Ver. 01.17 (type: UEFI)

Processor: Intel(R) Core(TM) i5-6200U CPU @ 2.30GHz (4 CPUs), ~2.4GHz

Memory: 8192MB RAM

Graphics:
Card name: Intel(R) HD Graphics 520
Manufacturer: Intel Corporation
Chip type: Intel(R) HD Graphics Family
Display Memory: 4172 MB
Dedicated Memory: 128 MB
Shared Memory: 4044 MB


The above can be seen in my system information output:
[HTML]https://gist.github.com/ogola89/5d0cf4b9b774b8ce6e8798a9798464f2/raw/1c8592c6e1b611b5f89973032977d2bcd5ce8cd4/System%2520Information[/HTML]

and my dxdiag output:
[HTML]https://gist.githubusercontent.com/ogola89/826bb236a3ccdd26f4af1de5cb0a55da/raw/6b6fb2f5b6feb21ca6afed3f78431f115f468d85/DxDiag-Output[/HTML]

if you want to dig deeper.

Thanks!

---

### Post by oldfred on 2020-04-30
Do you have latest UEFI that HP has for this system?

Only one older thread for this model, and that was Mint & boot issue:
HP ProBook 450 G1 Custom UEFI boot or copy to bootx64.efi, delay of a so called "Express Multiboot menu"
[http://forums.linuxmint.com/viewtopic.php?f=46&t=164076](http://forums.linuxmint.com/viewtopic.php?f=46&t=164076)

With 8GB of RAM, you should not be having issues.
Have you run top or htop (you have to install it, but slightly better)?

Serveral years ago I had issues with tracker running & it took awhile to find out what was happening.
I kept system monitor & htop running to see what was happening.

I installed Ubuntu fallback/gnome-panel as lightweight gui on my 2006 Toshiba laptop with 1.5GB of RAM. And as long as I only load one larger app & several smaller apps, it runs well. With more loaded it does then go to swap which is on an old slow 5400RPM drive and screen turns gray for several seconds during swapping.

---

### Post by ogola89 on 2020-05-14
Hi guys,

So I decided to take the opportunity to do a fresh install to 20.04 to see if this would clear my problems. So I did a complete wipe and reinstall. It was great at first, I could run Firefox + 4 code editors (r studio, vscode, octave and atom) but a few days on and the problems have returned. I even tried installing falkon and was only using vscode with it but it froze. This happens every time I use ubuntu within 2 hours I will have a freeze that requires a hard reset or reisub. This has given me a huge distaste for using it right now as I just can't get much headway with projects and tasks. I don't know why the performance is so poor and I don't know how to fix it. &#55357;&#56862;&#55357;&#56862;

---

