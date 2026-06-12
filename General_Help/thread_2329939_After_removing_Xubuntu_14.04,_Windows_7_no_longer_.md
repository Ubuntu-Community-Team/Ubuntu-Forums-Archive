---
title: "After removing Xubuntu 14.04, Windows 7 no longer boots, broken WUBI detected"
date: 2016-07-06
forum: General Help
---

### Post by marcinoo on 2016-07-06
Hello,

I'm not sure if this is a correct forum section to post about broken WUBI, if not, please move the thread then. Also sorry for my crappy english slang, as I'm not natively english. My Windows 7 is completely broken and unbootable, I already spent almost 2 days to fix it, with no success. I currently write my post from booted rescuse CD Rescatux which has build-in internet browser. (which is almost unusable btw, I'm happy I even could get to register on the forums). And now the dramatic horror story...:o

I had a working dual-boot Windows 7 64bit UEFI GPT + WUBI Xubuntu 14.04 UEFI 64bit over it, for some time (installed as a standalone application under Windows 7 on the Windows 7 partition), but two days ago I decided to remove Xubuntu from my computer, so I booted to Windows 7 and entered into Add/Remove Programs panel and clicked on uninstall Wubi Xubuntu, but that did not want to uninstall - just a some window appeared + a rotating circle (of a mouse cursor), like something is being uninstalled and going on, but after several seconds the window and the circle have disappeared, and Xubuntu still has not been uninstalled and still was visible in Add/Remove programs and Xubuntu folder was still existing on HDD, no confirmation like "uninstall successfull or "error", just nothing. So I had repeat the uninstallation several times but every time the same thing happens, the just refuse to uninstall with no kind of a feeback. So as it was unable to uninstall itself...I helped it a bit to do so by removing Xubuntu folder manually from the Windows 7 partition, and then I rebooted the computer... and there is where the problem begins.. I can no longer boot Windows 7, some error appeared - white font on black screen:

>  Minimal bash-like line editing is supported for the first word tab list possible command completions. Anywhere else TAB lists possible device od file.

grub> _


So I started to google and tried various solutions found on various forums:

- booting Windows 7 ISO, use "Fix boot" and then restarting the computer, but that didn't help, so I continued:

- booting Windows 7 ISO and entering the command line "bootrec / fixmbr" and then "bootrec / fixboot" - in both cases I received feedback:

> Result: The operation completed successfully

and then restarting the computer, but that didn't help too, so I continued:

- booting Windows 7 ISO and entering the command line "bootsect / nt60 C:" and then restarting the computer, but that didn't help too, so I continued:

- booting Windows 7 ISO and entering the command line "bootsect / nt60all / mbr" and then restarting the computer, but that didn't help too, so I continued:

- booting Windows 7 ISO and entering the command lines:

> 
diskpart
list disk
select disk (I choosed Windows 7 disk)
list partition
select partition (I choosed Windows 7 partition)
detail partition (it was unactive, so)
active

but I received a feedback:

> The selected disk is not a fixed MBR disk. Only on fixed MBR disks it's possible to mark a disk as active.
so I continued:

- booting Windows 7 ISO and entering the command line "bootsect /rebuildbcd" - I received a feedback:
about unable to locate my Windows 7 installation and something about partition being locked (I don't remember exactly the "locked" message):

> The drive where Windows is installed is locked.
"Successfully scanned Windows installations.
Total identified Windows installations: 0
The operation was completed successfully."

and then restarting the computer, but that didn't help too


Meanwhile during subsequent boot tries the above-mentioned commands in all the above mentioned ways, Windows 7 still does not get up and just changed error messages:

> Insert a boot disk and press any key

> Reboot and Select proper Boot device or Insert Boot Media in selected Boot device and press a key

> No partition is active

and finally I'm stuck with:

> Missing operating system

So finally I downloaded and booted from:

> Rescatux Rescue CD [http://www.supergrubdisk.org/rescatux/](http://www.supergrubdisk.org/rescatux/)

which just serves to fix such problems with booting and I chosed "Repair" however instead fix, Rescatux told me to use:

> Boot Rescue Disk 64bit" [https://sourceforge.net/projects/boot-repair-cd/](https://sourceforge.net/projects/boot-repair-cd/)

so I did so, downloaded, booted and chosed "Repair" and then restarted the computer, but that didn't help too , however that generated a usefull log:

> [http://paste.ubuntu.com/18521712](http://paste.ubuntu.com/18521712)

another log:

> [http://paste.ubuntu.com/18519581](http://paste.ubuntu.com/18519581)

So I posted my problem on:

> [http://ubuntu.pl/forum/viewtopic.php?f=133&t=180033](http://ubuntu.pl/forum/viewtopic.php?f=133&t=180033)

But the guys were unable to help me, so I decided to post here.

Meanwhile I also removed some 2 files from Windows 7 partition, something like wubildr.efi + another one but that didn't help too. I also realised myself that all the bootrec /fixmbr like commands are not applicable for GPT.

My Windows 7 is completely unbootable now. I also still have Xubuntu entry in BIOS and also in BIOS boot list (when pressing F12). When I'm booting Xubuntu from the inside of BIOS, a black screen appears for 1 second, and it gets back to BIOS. I guess that's because it fails to find Xubuntu on Windows 7 partition because Xubuntu has been removed. When I'm booting Xubuntu from outside the BIOS, from BIOS boot list (when press F12), a mainboard logo appears for 10 seconds and then an error appears "Missing operating system" but I suppose the error message in this case is not because of booting Xubuntu, but because of alternatively booting a Windows 7 HDD as NONUEFI (PO SAMSUNG EVO 850 120GB) which is a second boot option after Xubuntu, I mean after Xubuntu fails to load, it tries to load the second option which gives the error. So Xubuntu boot gives black screen + return. The third boot option is UEFI Samsung 850 EVO 120GB which used to successfully boot Windows 7, before all got broken, but now it gives "Missing operating system" too.

At the end of logs there is:

> A broken Wubi has been detected. Please fix it this way:
[https://wiki.ubuntu.com/WubiGuide#Cannot_boot_into_Ubuntu](https://wiki.ubuntu.com/WubiGuide#Cannot_boot_into_Ubuntu)

Please help me to fix broken WUBI, clean Xubuntu entries from BIOS, and bring back Windows 7 working. My Win7 is dead.

---

### Post by howefield on 2016-07-06
Welcome to the forums.

Duplicate thread closed, it is better to use the report button to get a thread or post moved.

---

