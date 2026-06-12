---
title: "Dual boot problems"
date: 2023-03-18
forum: General Help
---

### Post by sfh1975 on 2023-03-18
Hi everyone
Sorry if this is the wrong forum, will appreciate if someone can direct me to the correct sub-forum. Thanks.

Using a laptop with dual boot (Win11 and Ubuntu 22.10), left the laptop in a running condition, not sure if it restarted overnight or if I turned it off, anyway the next day it failed to boot.
Tried many solutions (using live usb, solutions from within grub>) but none worked. Deleted the first partition and reinstalled grub, still no luck :(

I am able to reach till grub> but not sure what to do after that.
Also, I can boot using a live usb and use Boot repair but it is also throwing errors, such as "Please enable a repository containing the [grub-efi] packages in the software sources of Ubuntu 22.10 (nvme0n1p5). Then try again."

Here is the [pastebin]("https://paste.ubuntu.com/p/PjSsj8yKVV/")

Any help is greatly appreciated. Looking forward.
Thanks :)

---

### Post by yancek on 2023-03-18
Boot repair on line 287 shows Legacy windows detected.  You have an EFI partition showing info beginning at line 7 but no expected files are showing.  You also show no code in the MBR which would be necessary for windows if it is a Legacy/CSM install. You indicate you deleted the first partition but it still shows but contains no data per boot repair.  This is where all the EFI boot files would be for both windows and Ubuntu.

Line 83 of boot repair shows your drive is GPT and windows will only install in UEFI mode on a GPT disk.  You need to use a windows recovery disk to repair this, boot repair won't help then reinstall the Grub EFI files from the Ubuntu USB.

You indicate the computer was shut down overnight and when you tried to boot in the morning you got an error.  What error would be helpful to know.

---

### Post by sfh1975 on 2023-03-18
Thanks a lot,
I have done many things over the last two days, starting with a working dual boot to windows only to grub>
Anyway, now I have recovered the Windows boot up using a Win11 installation USB. I have also re-enabled secure boot. Windows seems to be working fine. This was a Win 10 upgraded to Win 11.
Tried repairing the grub again using Ubuntu live USB but got the same message "Please enable a repository containing the [grub-efi-amd64-signed] packages in the software sources of Ubuntu 22.10 (nvme0n1p5). Then try again."
I have now posted a new file on pastebin [https://paste.ubuntu.com/p/TwNrkhvQnX/](https://paste.ubuntu.com/p/TwNrkhvQnX/)
Any help is highly appreciated.
Thanks.

---

### Post by oldfred on 2023-03-18
If you want UEFI Secure Boot on, you have to have signed versions of grub, kernel & any drivers. Drivers you may have to sign yourself with MOK - machine owner key.

Suggested repair is to reinstall grub's signed version. Not sure if you have signed kernel or not. But you can use Boot-Repair's advanced mode to also choose to install latest kernel.

---

### Post by sfh1975 on 2023-03-18
Thanks, no I dont care if secure boot is enabled or not, I enabled it because I thought this was the default setting. I can disable it. I have no idea what MOK or anything like that is :)
I can try disabling the secure boot and post the results here again.
But before I do that, I am not sure if I need to do something that you said about installing the latest kernel. Do I have to do that before or after I disable the secure boot?
Many thanks.

---

### Post by oldfred on 2023-03-18
Since not sure which kernel you have, it will work with Secure boot off, even if the signed version.

If Secure boot is off, you do not have to sign drivers. That is most often the nVidia driver, if you have nVidia and sometimes a driver for WiFi. Ubuntu cannot sign binary blob which those drivers are, you just create your own key into system to say that you as user authorize that software as signed for Secure Boot.

---

### Post by sfh1975 on 2023-03-18
Thanks I have turned off the secure boot but it is now giving me error "Please enable a repository containing the [grub-efi] packages in the software sources of Ubuntu 22.10 (nvme0n1p5). Then try again."
Here is the pastebin in case anything has changed [https://paste.ubuntu.com/p/T98Kg4Gf4X/](https://paste.ubuntu.com/p/T98Kg4Gf4X/)
Any ideas?
Much appreciated.

ps: I also tried choosing the option for latest kernel, with the additional error "Please enable a repository containing the [linux-generic] packages in the software sources of Ubuntu 22.10 (nvme0n1p5). Then try again."

---

### Post by oldfred on 2023-03-18
Is Boot-Repair not mounting p5? So it can see the repository info?
Is it asking you to input commands & you are not correctly inputting them one at a time?

I might try fsck on p5. Run both commands and see  this if questions on parameters
man e2fsck

sudo e2fsck -C0 -p -f -v /dev/nvme0n1p5
sudo e2fsck -f -y -v /dev/nvme0n1p5 

If still not working you may need a full chroot & repair.
UEFI chroot, must include ESP - efi system partition
[http://askubuntu.com/questions/53578/can-i-install-in-uefi-mode-with-the-alternate-installer/57380#57380](http://askubuntu.com/questions/53578/can-i-install-in-uefi-mode-with-the-alternate-installer/57380#57380)

---

### Post by sfh1975 on 2023-03-20
Thanks, followed all the steps you suggested to no avail, so moved on to the link you shared. Couldn't chroot /mnt until I bound lib, lib32, lilb64.

After this, still getting error:
root@ubuntu:/# apt-get install grub-efi-amd64
E: Error reading the CPU table

Tried this:
root@ubuntu:/# sudo mount --bind /usr/share/dpkg /mnt/usr/share/dpkg

Now getting this:
sudo: error while loading shared libraries: libsudo_util.so.0: cannot open shared object file: No such file or directory

No idea how to proceed. Any suggestions? 
Many Thanks.

---

### Post by oldfred on 2023-03-20
It sounds like you install is not complete.
I have not seen anyone need to bind individual sub-directories over the default in the instructions.

You can do a "dirty" install or where you do not reformat drive.
That preserves all your data, but any system or user configuration  files you edited will be back to defaults. 
Best to still have good backups.

[https://help.ubuntu.com/community/UbuntuReinstallation](https://help.ubuntu.com/community/UbuntuReinstallation) & 
[http://ubuntuforums.org/showthread.php?t=1941872](http://ubuntuforums.org/showthread.php?t=1941872)

---

