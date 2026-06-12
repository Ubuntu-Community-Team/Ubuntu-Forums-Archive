---
title: "I was able to restore Grub to a partition from a copy of the EFI Grub folder"
date: 2020-09-03
forum: General Help
---

### Post by Cavsfan on 2020-09-03
@Fred (oldfred),
I learned this trick from you back some time ago. This is the first time I've used it and it worked great.
When you install a new Ubuntu version, you should make a copy of your **/boot/efi/EFI/ubuntu** folder for backup.

I had Bionic Beaver 18.04 installed, then also installed Focal Fossa 20.04 and the devel  version Groovy 20.10.

With each install the **/boot/efi/EFI/ubuntu** folder was written over.

After I installed each I made a backup of the folder before I installed another version of Ubuntu.

I would use super user privileges to make a backup folder and copy the folder contents with the cp -r parameter:
From the man page:
```
-R, -r, --recursive
       copy directories recursively

```
```
cavsfan@bionic:~$ sudo su
[sudo] password for cavsfan: 
root@bionic:/home/cavsfan# cd /boot/efi/EFI

root@bionic:/boot/efi/EFI# ls -lA
total 44
drwx------ 3 root root 4096 Apr 29  2018 [COLOR=#0000cd]Arch_grub[/COLOR]
drwx------ 2 root root 4096 Apr 22 14:36 [COLOR=#0000cd]Boot[/COLOR]
drwx------ 5 root root 4096 Sep  4  2018 [COLOR=#0000cd]EFI[/COLOR]
drwx------ 3 root root 4096 Sep  2 19:33 [COLOR=#0000cd]fedora[/COLOR]
drwx------ 4 root root 4096 Apr 12  2018 [COLOR=#0000cd]Microsoft[/COLOR]
drwx------ 4 root root 4096 Dec 26  2018 [COLOR=#0000cd]opensuse[/COLOR]
drwx------ 4 root root 4096 Sep  1 11:59 [COLOR=#0000cd]ubuntu[/COLOR]
drwx------ 4 root root 4096 Sep  1 11:43 [COLOR=#0000cd]ubuntu-bionic[/COLOR]
drwx------ 4 root root 4096 Sep  1 11:56 [COLOR=#0000cd]ubuntu-focal[/COLOR]
drwx------ 4 root root 4096 Sep  2 23:15 [COLOR=#0000cd]ubuntu-groovy[/COLOR]

```
Then upon rebooting Bionic was the Grub screen I had.

But, I learned that you need to boot into the system you copied  and install Grub on that partition or your 2nd boot won't be into that same Grub.
```
sudo grub-install --target=x86_64-efi --efi-directory=/boot/efi/EFI/ubuntu --bootloader-id=ubuntu
```
I believe it goes back to where it was installed or updated. You have to physically be on the partition and install it there for it to be good to go.

---

### Post by oldfred on 2020-09-03
I still backup ESP, but now just edit /EFI/ubuntu/grub.cfg with correct UUID for my main working install. The grub.cfg normally gets overwritten with every new Ubuntu install.
Still have to use efibootmgr to change boot order back to my main working install after any new test install.

I also now have the work around to get Ubuntu's Ubiquity to install to my backup ESP on sdb, and now use that most of the time. Because I use grub2's loopmount for my install ISO, some of the other work arounds do not work for me.

Posted work around to manually unmount & mount correct ESP during install #23 & #26
 [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)
Others suggest disconnecting all other drives physically or logically in UEFI settings, so install drive is first drive.
Or removing boot flag/esp flag from first drive, so only ESP is install drive. (I have not had that work, but others have.)
Or if you have ESP on second or external drive, you can just reinstall grub, either manually or using Boot-Repair's advanced mode & full reinstall to correct drive.

---

### Post by oldfred on 2020-09-03
You have lots of entries in grub.
I like to add several spacer lines, just to have some visual separation. But I go back to days old green bar paper with every 3 lines a different color for separation.
Once I accidentally set default boot to the spacer line and wondered why it would not boot. :)

```
# spacer line
menuentry " " {
set root=
}

menuentry "System restart" {
echo "System rebooting..."
insmod reboot
reboot
} 

menuentry "System shutdown" {
      echo "System shutting down..."
      insmod halt
      halt
}

```

---

### Post by Cavsfan on 2020-09-04
I have not been successful using the efibootmgr command to change the boot order. It works for informational purposes. Could have been user error. :P

I thought it was good I caught the entire original EFI grub folder of each when they were booting initially. Copying them works every time: you are saying it is just the grub.cfg file in there that needs copying?

Copying the folders are necessary for Ubuntu. The BIOS will also change the partition that boots from grub. Which is the easiest method, if your BIOS supports this.
On my computer I have:
[LIST=1]
[*]Arch Linux
[*]Fedora 32
[*]openSUSE Tumbleweed
[*]Bionic Beaver 18.04.5 LTS
[*]Focal Fossa 20.04.1 LTS
[*]Groovy Gorilla 20.10 (devel version)
[*]Windows 10
[/LIST]
The 1st 3 has it's own unique folder.

> **oldfred said:**
> Once I accidentally set default boot to the spacer line and wondered why it would not boot. :)


I can't count the number of wrong trees I've climbed up. What is most painful is re-learning something you absolutely know but, haven't used in a while. :)

---

### Post by oldfred on 2020-09-04
Some systems, particularly HP, so not seem to support the changes made by efibootmgr. They only work from within UEFI.

I thought Fedora had its own efi folder. But all the Ubuntu flavors and many based on Ubuntu seem to just use /EFI/ubuntu. 
I have changed the distribution in /etc/default/grub and get new entry in UEFI when I reinstall grub. But it did not used to have its own grub.cfg and only used the one in /EFI/ubuntu. So was not able to create unique UEFI boot entries for different installs. My latest focal is only kubuntu:
GRUB_DISTRIBUTOR=kubuntu
I had this for example, but it did not seem to be used.
/efi/bionic1804/grub.cfg 
And this was always used, but have not tested recently to see if still the same.
/efi/ubuntu/grub.cfg

Are the others just using /EFI/grub?
Some also seemed to not have a grub.cfg in the ESP like Ubuntu. They seem to embed the way to find the full grub.cfg in the install partition somewhere in the .efi boot files.

I often let a new version install to my default ESP, just to have latest grub efi boot files. But then just edit grub.cfg back to configfile to my main working install. Have yet to have any version issues with that, but part of reason I have backup. Or know how to reinstall grub if necessary.

---

### Post by Cavsfan on 2020-09-07
I have been letting grub install on all Ubuntu versions when a new update installs and moves grub. But, then I boot into Bionic and copy the whole **ubuntu** folder, it's easy and serves the purpose.

All versions of Ubuntu overwrite that ubuntu folder; same with **fedora**; I had more than one version installed for a while. Debian will do the same with a **debian** efi folder.

Here are the folders in my **/boot/efi/EFI/** folder

```
[COLOR=#0000CD]Arch_grub[/COLOR]  Boot  EFI  [COLOR=#0000CD]fedora[/COLOR]  Microsoft  [COLOR=#0000CD]opensuse[/COLOR]  [COLOR=#0000CD]ubuntu[/COLOR]  ubuntu-bionic  ubuntu-focal  ubuntu-groovy
```
I believe I named the Arch_grub folder. Arch Linux and openSUSE Tumbleweed are both rolling distros.

That [COLOR=#000000]**/efi/ubuntu/grub.cfg** file is what I check to verify the UUID matches.

Fedora does boot from the efi grub.cfg not the normal one in [/COLOR]/boot/grub/.
Fedora's update-grub:
```
sudo grub2-mkconfig -o /boot/efi/EFI/fedora/grub.cfg
```

Reinstalling Fedora grub is not simple. There is no grub install command nor can you use efibootmgr to change it.
Here's [[COLOR=blue]how to reinstall EFI Grub in Fedora[/COLOR]]("https://forums.fedoraforum.org/showthread.php?313609-How-to-reinstall-Grub-EFI-in-Fedora-with-Fedora-Workstation-Live-media&p=1783554#post1783554").
Trust me I [[COLOR=blue]asked[/COLOR]]("https://forums.fedoraforum.org/showthread.php?320033-Is-there-an-easy-way-to-re-install-EFI-grub-on-Fedora").

---

