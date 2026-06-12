---
title: "boot repair problems"
date: 2014-05-06
forum: General Help
---

### Post by tyler36 on 2014-05-06
So i just installed ubuntu on my laptop today. Im trying to dual boot it with windows 8 but it always boots into windows and i have to go go through my advanced settings to get into ubuntu so i tried and run boot repair it always say it doesnt work and i get this error report [http://paste2.org/XEcNgwds](http://paste2.org/XEcNgwds) so Ive tried making a boot partition but it didnt seem to help. Im just wondering what i need to do?

---

### Post by oldfred on 2014-05-06
Do you have secure boot on. Often better with it off.
You do show signed kernel, but your ubuntu entry in UEFI is grub not shim(signed grub)?

```
 BootOrder: 3000,3001,2001,2002,2003
Boot0000* Windows Boot Manager HD(2,c8800,82000,44f6b28e-da0e-4902-bbea-4f1b13cb508f)File(EFIMicrosoftBootbootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}..._................
Boot0001* [COLOR=#ff0000]Ubuntu[/COLOR] HD(2,c8800,82000,44f6b28e-da0e-4902-bbea-4f1b13cb508f)File(EFIubuntu[COLOR=#ff0000]grubx64[/COLOR].efi)RC
Boot2001* USB Drive (UEFI)	RC
Boot2002* Internal CD/DVD ROM Drive (UEFI)	RC
Boot3000* Internal Hard Disk or Solid State Disk RC
Boot3001* Internal Hard Disk or Solid State Disk RC


```

A lot of HP users have issues.
       It seems hp firmware do not allow you to boot anything other than windows. Hence no ubuntu option in the UEFI. To work around it
1) press esc key while booting to access start up menu 2) press F9 for boot devices menu. 
[SOLVED] Trying to install Ubuntu as dual boot on Windows 8.1 desktop HP500
[URL="http://ubuntuforums.org/showthread.php?t=2218154"]http://ubuntuforums.org/showthread.php?t=2218154
[/URL]
 HP Manually renamed files to make it work.
[URL="http://ubuntuforums.org/showthread.php?t=2131886"]http://ubuntuforums.org/showthread.php?t=2131886
      [/URL]
 HP to get into UEFI/BIOS menu - escape then f10 as soon as it starts. Key board issues try differnet USB ports maybe  front.
[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079)

Sony's have similar issues:

 One Sony user
> The trick was to manually copy the ubuntu Boot directory in place of the \EFI\Boot Directory, and rename shimx64.efi to \EFI\Boot\bootx64.efi (not \EFI\Microsoft\Boot\bootmgfw.efi )

 
    [URL="http://ubuntuforums.org/showthread.php?t=2131886"]
[/URL]
 Users who manually moved efi files around see post #6
[http://ubuntuforums.org/showthread.php?t=2101840](http://ubuntuforums.org/showthread.php?t=2101840)
[http://ubuntuforums.org/showthread.php?t=2219452](http://ubuntuforums.org/showthread.php?t=2219452)
some find this changing this to be shim or grub /EFI/Boot/bootx64.efi 
Then booting device or hard drive works also.
[http://ubuntuforums.org/showthread.php?t=2221498&p=13012109#post13012109](http://ubuntuforums.org/showthread.php?t=2221498&p=13012109#post13012109)

[URL="http://ubuntuforums.org/showthread.php?t=2131886"]
[/URL]

[URL="http://ubuntuforums.org/showthread.php?t=2218154"]
[/URL]

---

### Post by tyler36 on 2014-05-07
Thanks for the help I appreciate it

---

