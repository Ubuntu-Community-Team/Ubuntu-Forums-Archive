---
title: "o grub menue at boot up"
date: 2015-10-05
forum: General Help
---

### Post by gordon33 on 2015-10-05
Hello All

No Grub menu at boot up.  Tried typing in the terminal: sudo update-grub

For the last year or 2 I have had a dule boot on my HP lap top.  Did a repair of the windows 8 and after that  for the last few days I have been unable to get Ubuntu to work.  With help from a previous   thread I was able to get Ubuntu back:  [http://ubuntuforums.org/showthread.php?t=2297249&highlight=gordon33](http://ubuntuforums.org/showthread.php?t=2297249&highlight=gordon33)


Gordon33

---

### Post by gordon33 on 2015-10-05
Hello All

What I have to do to get Ubuntu is make the selection from the bios.

What do I need to do to get grub at boot up?

Gordon

---

### Post by Ben_Shaver on 2015-10-05
I believe what you need is an Ubuntu boot repair, for this you'll need an Ubuntu/derivative live USB. Further instructions can be found here: [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
Hope this helps! :)

---

### Post by gordon33 on 2015-10-05
Hello  Ben_Shaver

I went througt the boot repair a day or  two ago.  Still I re-did the repair.  Here is the link [http://paste.ubuntu.com/12694398/](http://paste.ubuntu.com/12694398/)

Gordon33

---

### Post by oldfred on 2015-10-05
You have an HP.

HP is not UEFI boot friendly for anything but Windows.
Many with HP have had to do a work around.
Most copy /EFI/ubunutu into /EFI/Boot and rename shimx64.efi to bootx64.efi. Then set hard drive as default boot entry. You probably will have to create the UEFI: Hard drive boot entry with efibootmgr.
Others have used efibootmgr to change boot order. But Windows may reset it.
Others have added grub entry to Windows BCD.
And some have used rEFInd.

More details in link in my signature.
       [URL="http://ubuntuforums.org/showthread.php?t=2234019"]http://ubuntuforums.org/showthread.php?t=2234019
      [/URL]
 HP ProBook 450 G1 Custom UEFI boot or copy to bootx64.efi, delay of a so called "Express Multiboot menu"
[http://forums.linuxmint.com/viewtopic.php?f=46&t=164076](http://forums.linuxmint.com/viewtopic.php?f=46&t=164076)
HP 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
[URL="http://ubuntuforums.org/showthread.php?t=2131886"]http://ubuntuforums.org/showthread.php?t=2131886
[/URL]
 HP Envy 700-430QE desktop used bcdedit to dual boot
[URL="http://ubuntuforums.org/showthread.php?t=2260681"]http://ubuntuforums.org/showthread.php?t=2260681
      [/URL]
 Envy M6 Change boot order sudo efibootmgr -o 2,1 post #23
[http://ubuntuforums.org/showthread.php?t=222789]("http://ubuntuforums.org/showthread.php?t=2227889")      [ ]("http://ubuntuforums.org/showthread.php?t=2260681")  [ ]("http://ubuntuforums.org/showthread.php?t=2131886")      [ ]("http://ubuntuforums.org/showthread.php?t=2234019")

---

### Post by gordon33 on 2015-10-06
Hello oldfred 

Thank you for the reply and all the links. This will be a challenge to get all the codes correct.

Gordon

---

