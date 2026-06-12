---
title: "[SOLVED] Multiple distros (installations) luks encrypted LVM EFI grub2 os-prober"
date: 2018-02-21
forum: General Help
---

### Post by Lop3 on 2018-02-21
Wow, this was quite a mission to figure out, but the solution is epicly simple!

Through the journey I considered messing around with os-prober because I couldn't figure out why it "couldn't find" the other ubuntu installation.
I also considered manually adding stuff to /etc/grub.d/40_custom 41_custom or whatever.

I'm just posting this because I spent ages trying to get it working and want to help others who may have the same desire.
The goal is to simply run more than 1 ubuntu installation on the same hard drive. It doesn't work by default.
The reason I want to run more than 1 distro is because I've got a Microsoft Surface Pro 2 tablet. It's got an Intel i5 processor, and touch screen etc.
Because it's a portable computer it should be encrypted with luks. However the problem is grub doesn't support Microsoft HID (mouse) [stackoverflow]("https://stackoverflow.com/questions/15419236/adding-touch-sensitivity-to-grub-2-boot-loader") [askubuntu (more useful links)]("https://askubuntu.com/questions/267721/adding-touch-to-grub2") or have an on-screen keyboard which means it doesn't support entering the luks password on a tablet without a keyboard attached. So I want to install one ubuntu that's not encrypted with no password (or maybe onscreen keyboard at the login if that's possible) and one that's luks encrypted for more serious work, where I'll connect a keyboard.

I'll just tell you what I finally did and what works, and you can adapt it to your needs.
You'll need 1 ext4 formatted partition, at least 150MB, but 300MB is probably a good size to hold the encrypted ubuntu's grub. (lets call this sda1)
Then I have sda2 EFI
Then sda3 is the LVM physical volume and volume group.

First boot the ubuntu live USB.
setup LVM
make the volumes
ubuntu_noenc
ubuntu_enc

SWAP
Obviously for your encrypted ubuntu the swap should be encrypted, and it's most convenient to keep it inside the ubuntu_enc volume.
I prefer to use a file for swap vs a dedicated volume etc.
You don't need to setup swap during the installation. Swap files can be created turned on/off and deleted as you like/need, without rebooting, later.

Then first install ubuntu_noenc. Simply select this as your / mountpoint in the installer. (don't select a separate /boot etc)
Then after that's done it should reboot and bootup successfully in your unencrypted ubuntu on ubuntu_noenc
Then boot your ubuntu live USB.
Start the installer, select ubuntu_enc and press change > physical volume for encryption
Then tell the installer to format ubuntu_enc_crypt and mount it as /
Tell it to format sda1 as ext4 and mount it as /boot
***Here's the non-obvious part*** Select ubuntu_noenc and change it from "do not use" to "ext4" (or whatever filesystem it is) but do not tick format, and do not specify a mount (unless you want to)
The installer will warn you that you've selected ubuntu_noenc as ext4 but you've not specified format or a mountpoint so it's "not going to do anything with it". That's actually a lie. It will add it to the grub menu!!! (evil success laugh: haha!)

Now when you finish the installation and reboot, the ubuntu_noenc option will be available for you to boot.

Finishing off
Boot up in ubuntu_noenc and `apt-get remove --purge grub*`
You don't want it messing up your bootloader.
Then boot up in ubuntu_enc and change your default to be ubuntu_noenc in /etc/defaults/grub
And bobs your uncle.

The next question that comes to mind is:
"If I want to add yet another luks LVM volume, will it be possible to add that to grub?"
I don't actually want to or need to do this (yet)

But if I do, I would try:
1. Backup sda1 and maybe also the MBR or the GPT whatever thing (I've not gone deep with EFI yet)
2. Boot the ubuntu installer, select try ubuntu.
3. Mount ubuntu_enc using `cryptsetup luksOpen /dev/mapper/myvg-ubuntu_enc myvg-ubuntu_enc_crypt`
4. Tell the installer that myvg-ubuntu_enc_crypt is ext4 as above.
5. Remove grub packages from all distros except one (as above)

Hopefully that will work!

Caveats:
Whenever you update one of the distro's kernels, you need to run update-grub on the main one again.
Whenever you run update-grub (which can happen when you update the kernel etc), if you have other encrypted distros you need to mount them and then run update-grub (so you repeat it, if it happened automatically) ASSUMING the above 5 steps works.

---

