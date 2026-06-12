---
title: "Boot Problems with Ubuntu andWindows 11."
date: 2023-03-04
forum: General Help
---

### Post by mikodo on 2023-03-04
Hello everyone,   

After a year, I decided to go into my Windows 10 install in my multi-boot laptop to update Windows. After not being in it for a year, you can imagine there were a lot of updates. It also upgraded to Windows 11. 

 Then, I found my laptop would only boot to Windows 11 with no display of the grub menu.  

Steps I tried to rectify this:  

In Windows 11, I disabled 'fast startup'. That didn't help.

 In BIOS, I tried many times, to set the Boot Priority for Ubuntu to boot first, but it could not be done. (very annoying). 

 In BIOS, I disabled 'Secure Boot'. That didn't help. 

I turned 'Secure Boot' back on; EXCEPT, I couldn't boot from an Xubuntu live usb on a flash drive, UNLESS, I disabled Secure Boot again. This is new behaviour and also, (very annoying). Or, at least, I don't remember having to do this before with live cd's.  

I found when I press 'esc' during the booting process, I can go into 'Startup Menu' and of course the BIOS.  In 'Start Up Menu', if I choose 'Boot Device Options', I can change the Boot Order in the 'OS Boot Manager' to Ubuntu to boot first.  Then, when I continue on with booting, I am given the familiar 'Grub greeting', with Ubuntu on top, and boots to Xubuntu 20.04. Welcome Back! 

I never had to do this before, to get to the grub menu.  I am happy that I am able to get into the Grub prompt and boot into the OS I choose, but it annoys me that I have to do though these extra steps and that a Windows Upgrade has seemingly done this.  

I ran this from Ubuntu before and after Boot-Repair:  

```
sudo grub-install /dev/nvme0n1 

sudo update-grub  
```

Then after Boot repair this:  [https://paste.ubuntu.com/p/8KFkJvKBmY/](https://paste.ubuntu.com/p/8KFkJvKBmY/) 

 "In case you still experience boot problems, indicate this URL to:  [EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL] or to your favorite support forum.  You can now reboot your computer. Please do not forget to make your UEFI firmware boot on the Ubuntu 20.04.5 LTS entry (nvme0n1/efi/ubuntu/-grubx64.efi file).  If your computer reboots directly into Windows, try to change the boot order, change the default boot entry of the Windows bootloader.  

For example you can boot into Windows, then type the following command in an admin command prompt:  bdcedit /set {bootfmgr} path \EFI\ubuntu\grubx64.efi" 

 *I do not know how to do that!  

I changed the default boot entry of the Windows bootloader by running in an admin command prompt:

```
bcdedit /set {bootmgr} path \EFI\ubuntu\grubx64.efi

```

   My computer still boots *directly into Windows 11, *unless I do as above *each time I boot: 

Go to Start Up Menu, choose 'Boot Device Option' an change the Boot Order in OS Boot Manager to Ubuntu first. 

Then Grub present with Ubuntu first and boots into Xubuntu.  Is there anything more, than com be  done?  

Thank you.

---

### Post by oldfred on 2023-03-04
Please edit first post, difficult to read without paragraphs.

Many with HP find they have to set boot order in UEFI settings (not UEFI boot menu).
For whatever reason HP seems to be the only vendor that does not support UEFI changes with efibootmgr which grub uses to set boot order.

You show two installs. Boot-Repair always defaults to first, unless you use its advanced mode to choose which install to use.

Your fstab in p3 shows mount of data twice?

---

### Post by DuckHook on 2023-03-04
I'm not trying to be difficult, but I don't have the strength today to parse through your wall of text.

If you edit your post and split off the various thought threads into discrete paragraphs, it would be easier for others to help.

**EDIT**

Ninja'd by oldfred

---

### Post by mikodo on 2023-03-04
Thanks people. 

  For the life of me, I am not able to edit, so that it has paragraphs, and when I retyped the whole body of text over again with paragraphs, it still did the same thing.  I apologize.

Oh I see, I need to have Java Scripts available. duh!

---

### Post by DuckHook on 2023-03-04
Ah, so it's the posting settings. You can try changing your forum editor settings to "Standard Editor". Just click the "Settings" button at the top of the web page, then "General Settings" under "My Settings". The choice of editors is near the bottom. WYSIWYG is sometimes problematic. We staff are used to using Standard Editor which causes the least amount of trouble. Your browser can also sometimes be a problem. Mine will occasionally strip the paragraph character from my typing too. This can sometimes be solved with quitting/relaunching the browser, but sometimes not. 

Let's not worry about it for now.

I leave you in oldfred's very capable hands.

---

### Post by mikodo on 2023-03-04
> **oldfred said:**
> .

Many with HP find they have to set boot order in UEFI settings (not UEFI boot menu).

Please Fred, how do I do that? 

Please disregard this post Fred, 

I tried 4 different ways to do this from guides on the internet. None of the clicky click's worked. I guess I'm a quitter. At least I can get back into my Xubuntu installs.

Thanks again for your help!

---

### Post by tea for one on 2023-03-04
I saw your boot-repair report and noticed that you have two disks in your PC - nvme0n1 and sda.
Are these disks both internal devices?

I ask this question because it is more robust to have each OS on an individual disk with its own ESP.
Consequently this reduces the problems of OS updates interfering with bootloaders.

---

### Post by mikodo on 2023-03-04
Thanks for sharing the insights. You know, I didn't know I had two drives until you spoke of it here. Thanks for that and the robustness you spoke of.

I'll have to look into the laptops hardware.

---

### Post by oldfred on 2023-03-04
You did not mention which model HP.
HP - escape + F9 for UEFI boot menu, F10 for UEFI/bios settings

HP Zbook 15 NVRAM locked, install issues
[https://ubuntuforums.org/showthread.php?t=2482555](https://ubuntuforums.org/showthread.php?t=2482555)
hp 250 g3  Change boot order in UEFI settings
[https://ubuntuforums.org/showthread.php?t=2467077](https://ubuntuforums.org/showthread.php?t=2467077)
HP Envy - use UEFI to change boot order & f9 f10
[https://askubuntu.com/questions/1332255/dual-boot-only-booting-into-windows-no-option-to-choose-between-windows-or-ubun](https://askubuntu.com/questions/1332255/dual-boot-only-booting-into-windows-no-option-to-choose-between-windows-or-ubun)

---

### Post by mikodo on 2023-03-04
> **tea for one said:**
> I saw your boot-repair report and noticed that you have two disks in your PC - nvme0n1 and sda.
Are these disks both internal devices?

Yes, they are both internal. I haven't looked up the internals yet for this laptop, but I expect the sda is a platter drive. 

I forgot that I use it for my data,  that is symlinked with my $HOME.

---

### Post by yancek on 2023-03-05
Depending upon which HP you have, the options change as explained by oldfred in the earlier post.  You should have an option for BIOS Setup which would be a permanent change  to the boot order.  You should see a message in the lower left of the screen on boot telling you which key to use.  On my HP laptops (yours may be different), I can tap the Esc key and will then see several options including F9 for one time changes and F10 for permanent changes.  If this is the case with your HP, select F10 and go to UEFI Boot Order, then arrow down to OS Boot Manager to highlight it and hit the Enter key.  You should see both windows and ubuntu options so select ubuntu and use the F6 key to move an entry up or the F5 key to move it down.

If you don't have the same options, you need whatever key gives BIOS Setup.

---

### Post by mikodo on 2023-03-05
- double post -

---

### Post by mikodo on 2023-03-05
> **yancek said:**
> Depending upon which HP you have, the options change as explained by oldfred in the earlier post.  You should have an option for BIOS Setup which would be a permanent change  to the boot order.  You should see a message in the lower left of the screen on boot telling you which key to use.  On my HP laptops (yours may be different), I can tap the Esc key and will then see several options including F9 for one time changes and F10 for permanent changes.  If this is the case with your HP, select F10 and go to UEFI Boot Order, then arrow down to OS Boot Manager to highlight it and hit the Enter key.  You should see both windows and ubuntu options so select ubuntu and use the F6 key to move an entry up or the F5 key to move it down.

If you don't have the same options, you need whatever key gives BIOS Setup.

Thank you, for taking the time and for your effort to respond.

I seem to have the same settings as you.

I have been going into the BIOS,  f10 > BIOS Setup Utility > Boot Options > OS Boot Manager > Hit Enter > Highlight Ubuntu ... >  esc  > and no matter which of the settings next, Save changes and exit; Ignore changes and exit; or Load Setup Defaults, I still always boot into Windows.

I am grateful, I can still tap on f9 each time starting/rebooting the computer, to enter into the Boot Utility and choose Ubuntu to boot into. My only recourse without that, would be to install over Windows with Xubuntu. Something I most likely will do in a couple of years, if I still have this laptop.

Thanks again!

...

---

