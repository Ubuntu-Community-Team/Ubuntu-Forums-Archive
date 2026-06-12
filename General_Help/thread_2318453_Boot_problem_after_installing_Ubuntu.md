---
title: "Boot problem after installing Ubuntu"
date: 2016-03-26
forum: General Help
---

### Post by mikiss on 2016-03-26
Hello, yesterday I installed ubuntu 15.10 (replace windows) on my acer laptop and facing the same problem:

[COLOR=#000000]"First, as I turn on, there is this blue screen error: "default boot[/COLOR]
[COLOR=#000000]device missing or boot failed. Insert recovery media and hit any key. Then[/COLOR]
[COLOR=#000000]select boot manager to choose a new boot device or boot recovery[/COLOR]
[COLOR=#000000]media". I can press "ok".[/COLOR]

[COLOR=#000000]Then, it comes a screen with Boot manager, with two choices:[/COLOR]
[COLOR=#000000]1 unknown device (WD10JPVX-22JC3T0)[/COLOR]
[COLOR=#000000]2 windows boot manager (WDC [/COLOR][COLOR=#000000]WD10JPVX-22JC3T0[/COLOR][COLOR=#000000])[/COLOR]

[COLOR=#000000]I choose 1.[/COLOR]

[COLOR=#000000]Finally it comes out Grub and I can start Ubuntu.[/COLOR]

[COLOR=#000000]Now, Ubuntu runs fine and I am happy, but the booting sequence is a little[/COLOR]
[COLOR=#000000]annoying and odd, definitely ankward. [/COLOR]

[COLOR=#000000]Besides, why there is still the windows boot manager if I have removed the original[/COLOR]
[COLOR=#000000]hard disk with windows? I can't understand, it is like the Windows Boot manager is still hidden in there somewhere."[/COLOR]

How can I fix it? Thanks.

[IMG]http://i1144.photobucket.com/albums/o481/mikiskis/20160325_222315_zpspmv4j2el.jpg[/IMG]

[IMG]http://i1144.photobucket.com/albums/o481/mikiskis/20160325_222346_zpslyngqwwn.jpg[/IMG]

[IMG]http://i1144.photobucket.com/albums/o481/mikiskis/20160325_222714_zpsiyx1zf2y.jpg[/IMG]

---

### Post by Uinthe on 2016-03-26
Hello. Did u try to change the boot preferences in BIOS/EFI? In order to let ubuntu run as a default u should move WD10...T0 device to the first string (Boot#1 or smthing like that).

---

### Post by mikiss on 2016-03-26
> **Uinthe said:**
> Hello. Did u try to change the boot preferences in BIOS/EFI? In order to let ubuntu run as a default u should move WD10...T0 device to the first string (Boot#1 or smthing like that).

Now it is on top of this list, but it does not help.
[IMG]http://i1144.photobucket.com/albums/o481/mikiskis/20160326_130443_zpshxv5srav.jpg[/IMG]

---

### Post by mikiss on 2016-03-26
Also enabled Boot meniu in BIOS, but when I go there by clicking F12 it shows just old windows boot manager.

[IMG]http://i1144.photobucket.com/albums/o481/mikiskis/20160326_130806_zpstezz7r1r.jpg[/IMG]

[IMG]http://i1144.photobucket.com/albums/o481/mikiskis/20160326_130545_zpsijhuzoud.jpg[/IMG]

---

### Post by Uinthe on 2016-03-26
Ok, now i see "Boot mode:UEFI". 
```
dpkg -l | grep -i grub
```
Use this command to get info about grub type.

---

### Post by mikiss on 2016-03-26
> **Uinthe said:**
> Ok, now i see "Boot mode:UEFI". 
```
dpkg -l | grep -i grub
```
Use this command to get info about grub type.

I hope this is what you asked for? :)

[IMG]http://i1144.photobucket.com/albums/o481/mikiskis/sc1_zpsncxyu4ha.png[/IMG]

---

### Post by Uinthe on 2016-03-26
[https://askubuntu.com/questions/700857/uefigrub-boot-repair-keeps-adding-mokmanager-efi-to-boot-menu]](https://askubuntu.com/questions/700857/uefigrub-boot-repair-keeps-adding-mokmanager-efi-to-boot-menu])
here is a possible solution.

---

### Post by oldfred on 2016-03-26
Please attach screen shots, not post in line.
You can easily attach with Forum's advanced Editor and paper clip icon.

All Acer with UEFI need you to create (at least temporarily) and set "trust" on the grub/shim EFI boot files.

       Acer Very latest UEFI/BIOS works, downgrade not required:
[http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141](http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141)
Acer E5-573G, downgrade UEFI, supervisor password & trust on Ubuntu efi boot files.
[http://askubuntu.com/questions/706912/getting-a-black-screen-when-installing-or-live-booting-ubuntu-any-version-in-m?noredirect=1#comment1039248_706912](http://askubuntu.com/questions/706912/getting-a-black-screen-when-installing-or-live-booting-ubuntu-any-version-in-m?noredirect=1#comment1039248_706912)
Acer Aspire E15 will not dual boot, many details
[http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot](http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot)
Acer Aspire E 15 Downgrade to older UEFI, password & trust (ACPI issues?)
[http://ubuntuforums.org/showthread.php?t=2298380&p=13403062#post13403062](http://ubuntuforums.org/showthread.php?t=2298380&p=13403062#post13403062)
Acer Aspire ES1-512-C39M Details on supervisor password and settings to enable trust on ubuntu entries Also R14 model same fix
One of several with more details:
[http://ubuntuforums.org/showthread.php?t=2297947](http://ubuntuforums.org/showthread.php?t=2297947)
[http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757)
[http://ubuntuforums.org/showthread.php?t=2291335](http://ubuntuforums.org/showthread.php?t=2291335)
[http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044](http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044)
[http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot](http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot)
[http://acer.custhelp.com/app/answers/detail/a_id/29349/](http://acer.custhelp.com/app/answers/detail/a_id/29349/)
[http://ubuntuforums.org/showthread.php?t=2290594](http://ubuntuforums.org/showthread.php?t=2290594)

---

