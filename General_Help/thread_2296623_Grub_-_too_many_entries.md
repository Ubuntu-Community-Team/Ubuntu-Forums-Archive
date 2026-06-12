---
title: "Grub - too many entries"
date: 2015-09-27
forum: General Help
---

### Post by tirafesi on 2015-09-27
Hello!
After changing the bios option of virtualization to enabled, my grub menu stopped showing.
In order to fix it, i ran the repair tool, which worked.
But now i have WAY TOO many entires. It shows almost 10 entries starting by EFI/something/something/something

Before i only had 4 entries. 2 for ubuntu and 2 for windows i think.

Is there a way to make it stop showing so many entries?
Also, what are all these new entries that it didnt show before?

Thnks in advance

---

### Post by ajgreeny on 2015-09-27
I imagine they are the entries for old kernels that are installed but probably no longer needed.

Show us the output in terminal of command ```
ls /boot | grep vmlinuz
```which will show us all you boot kernel entries.
You could also run command ```
sudo apt-get autoremove
```then run the first command again to see if it removed all but the last two kernels.

---

### Post by tirafesi on 2015-09-27
I wrote the 1st command, but it only shows 2 entries:
[http://i.imgur.com/WApOFvs.png](http://i.imgur.com/WApOFvs.png)

What should i do?

---

### Post by ajgreeny on 2015-09-27
In that case I am baffled as to what all those entries in your grub menu might be.

It may be worth using the Boot-Repair link in my signature but just running the boot-info script, not the actual repair at this stage.  Copy back here the pastebin link that will give you to a file with all the results of the script; it may give us more clues.

A screenshot of your grub menu will also help, though I realise you will need to do that with a camera or smartphone, download that to your hard drive, then add a thumbnail of the image as an attachment using the paperclip icon in the toolbar of the reply box.

---

### Post by tirafesi on 2015-09-27
Here: [http://paste.ubuntu.com/12593503/](http://paste.ubuntu.com/12593503/)

I'll try to post a picture of the boot menu as well in a sec

---

### Post by tirafesi on 2015-09-27
Here is a picture of the boot menu:
[http://i.imgur.com/PbsicUX.jpg](http://i.imgur.com/PbsicUX.jpg)

Hope it helps :3

---

### Post by ajgreeny on 2015-09-27
I see you are dealing with a UEFI system and it looks to me as though the /boot/efi/EFI/ folder that is used to store the bootloader files for each OS on the system has too many entries in it; they are not automatically removed as I understand the UEFI system, but may have to be removed manually.  I imagine these extra entries have appeared as a result of your changing the BIOS (actually UEFI, not BIOS) setup; what exactly did you do when you made those changes; what were they?

However, before you start rushing into activity now, wait for a while to see if anyone else who understands UEFI better than I passes by with a great deal more info than I can give you, (oldfred, where are you?).  I am not sure how to figure out which entry or entries you would need to remove as this is something I have never needed to do nor attempt to do.

---

### Post by tirafesi on 2015-09-27
Like i said, it was when changing the virtualization option in the BIOS that the grub menu stopped showing. After that i just googled for ways to make it show again.
What i recall doing was:
Going to windows and writting on the cmd bcdedit /set "{bootmgr}" path \EFI\ubuntu\grubx64.efi
Changing some stuff on the etc/default/grub (but then i changed them back to the default values)
But it was only after i ran the boot repair tool that it showed again, looking like that.

(sry i changed font midway, too lazy to change it back :/)

---

### Post by oldfred on 2015-09-27
Boot-Repair sees all those .efi entries in your ESP - efi system partition so it creates entries for them. Other vendors have a hidden partition for similar system files.
You probably do not need them in grub.

You can just turn off or edit all the entries in 25_custom that Boot-Repair created.
 # Edit 25_custom entries created by Boot-Repair:
sudo cp -a /etc/grub.d/25_custom /etc/grub.d/bkp25_custom
# turn off execute bit or it will run backup also
sudo chmod a-x /etc/grub.d/bkp25_custom
gksudo gedit /etc/grub.d/25_custom
# Then do:
sudo update-grub

If you do not want or need any of the entries in 25_custom
sudo chmod a-x /etc/grub.d/25_custom

---

### Post by tirafesi on 2015-09-27
It worked! It only shows the original entries i had before! Thank you :)

But now i've got another problem...
After booting into windows, the boot menu stopped showing again...
Now i need to force it into the boot menu by pressing F9 during start.
How can i make it appear again and prevent it from stopping appearing everytime i log into windows?

---

### Post by oldfred on 2015-09-27
HP is not friendly to anything but Windows. And they modify UEFI to use description as a check on what they allow to boot and of course the only valid description is "Windows". That is not per UEFI standard, and now that many vendors seem to be doing the same thing, it seems like Microsoft may be suggesting non-standard UEFI.

Work arounds for systems that only want "Wndows"
 [http://ubuntuforums.org/showthread.php?t=2234019](http://ubuntuforums.org/showthread.php?t=2234019)
Also more details in link in my signature.

Other HP users that did fixes. Most rename bootx64.efi, some like rEFInd, or adding an entry to Windows BCD which means you boot into Windows and use UEFI one time boot to reboot into Ubuntu.

      
 HP ProBook 450 G1 Custom UEFI boot or copy to bootx64.efi, delay of a so called "Express Multiboot menu"
[http://forums.linuxmint.com/viewtopic.php?f=46&t=164076](http://forums.linuxmint.com/viewtopic.php?f=46&t=164076)
HP 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
[URL="http://ubuntuforums.org/showthread.php?t=2131886"]http://ubuntuforums.org/showthread.php?t=2131886
[/URL]
 HP Envy 700-430QE desktop used bcdedit to dual boot
[http://ubuntuforums.org/showthread.php?t=2260681](http://ubuntuforums.org/showthread.php?t=2260681)

[URL="http://ubuntuforums.org/showthread.php?t=2131886"]
[/URL]

---

