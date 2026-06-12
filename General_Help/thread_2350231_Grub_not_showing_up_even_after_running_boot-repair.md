---
title: "Grub not showing up even after running boot-repair and disabling secure boot"
date: 2017-01-22
forum: General Help
---

### Post by aewhatley on 2017-01-22
I was able to succesfully dual boot Ubunt 16.10 with Windows 10. However, the grub menu is not showing up, even after running boot-repair and disabling fast startup and secure boot. The pastebin report from boot-repair is here: [http://paste2.org/C6WbWxA5](http://paste2.org/C6WbWxA5)

---

### Post by oldfred on 2017-01-22
You have an HP. 
They are not Dual boot friendly. They violate UEFI spec that says NOT to use description as part of boot.
And of course only allowed description is "Windows Boot Manager".

There are multiple work arounds.
Boot-Repair mentions one at the end of the report.
Some just use the one time boot key, f9 ? with HPs? As that should show the ubuntu entry.

If in Boot-Repair's advanced options you can check "use the standard efi file"
That copies shimx64.efi to /EFI/Boot/bootx64.efi. And that file is a fallback or hard drive boot entry that will also work.

Older posts where users manually copied shim.
 Copy to /EFI/Boot/bootx64.efi
[http://ubuntuforums.org/showthread.php?t=2247186](http://ubuntuforums.org/showthread.php?t=2247186)
[http://askubuntu.com/questions/150174/sony-vaio-with-insyde-h2o-efi-bios-will-not-boot-into-grub-efi](http://askubuntu.com/questions/150174/sony-vaio-with-insyde-h2o-efi-bios-will-not-boot-into-grub-efi)
Sony, HP & others:
[http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789](http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789)
[http://askubuntu.com/questions/582073/dual-boot-but-only-windows-boots/582114#582114](http://askubuntu.com/questions/582073/dual-boot-but-only-windows-boots/582114#582114)
Rename bootx64.efi
[URL="http://ubuntuforums.org/showthread.php?t=2234019"]http://ubuntuforums.org/showthread.php?t=2234019

[/URL]
 HP Check if Customized UEFI settings available like this  HP ProBook 4340
[https://ubuntuforums.org/showthread.php?t=2332681&p=13527216#post13527216](https://ubuntuforums.org/showthread.php?t=2332681&p=13527216#post13527216) 

[URL="http://ubuntuforums.org/showthread.php?t=2234019"]
[/URL]

---

