---
title: "Bug when installing Ubuntu 23.10 from Live USB to USB?"
date: 2023-11-09
forum: General Help
---

### Post by Niytro on 2023-11-09
I created a bootable USB with the Ubuntu 23.10 ISO, I load it up and plug in another blank USB drive (64GB MBR Formatted No Partitions) and start the installer. I make all the necessary selections, I choose to stay offline and to do a Default Installation with no extras and Manual Partitioning. Now, when I did this before I was able to select /dev/sdc (my blank USB) and at the bottom I select /dev/sdc for the Bootloader and it automatically creates a 1GB bootable EFI or UEFI partition and with the rest of the space available I create an Ext4 partition with / mount point. I hit next and it installs Ubuntu to the USB no problem. Well, I just tried doing this again but when I select the Bootloader location /dev/sdc it creates a blank 1.05MB partition...no EFI bootable nothing. It just says 1.05MB unformatted space. I have tried updating the installer, not updating the installer, internet, no internet, completely wiped USB, formatted USB with no partitions, and I can't get it to create that EFI partition like it had before for the bootloader.

The reason I am doing this install is to have more control over the system rather than doing a Rufus installation with Persistence. I like being able to have a complete system, change passwords, encrypt if I want. The Rufus way just makes the USB act like a Live USB but it saves my changes...it isn't that great.

Any help would be appreciated. Thanks!

---

### Post by Rubi1200 on 2023-11-09
Not sure if this is really what you want but perhaps try installing 23.04 using the legacy installer and then upgrade to 23.10?

More information here:
[https://ubuntuforums.org/showthread.php?t=1958073&page=123&p=14139809#post14139809](https://ubuntuforums.org/showthread.php?t=1958073&page=123&p=14139809#post14139809)

That entire thread is packed full of information from start to end so also worth taking the time to look through for more tips.

---

### Post by guiverc on 2023-11-09
Ubuntu 23.10 has many ISO to choose from, but which you used wasn't provided.

- Ubuntu Server 23.10 using the `subiquity` installer
- Ubuntu Desktop 23.10.1 using the `ubuntu-desktop-installer`
- Ubuntu Desktop 23.10 using the `ubiquity` installer (*legacy*)

It's unclear to me which you were using?  Due to a *translation bug* found in the `ubuntu-desktop-installer`, that ISO was respun, thus the .1 on the download; it installs the same Ubuntu Desktop as the *legacy* ISO, the .1 relates only to the installer being updated.

If you have problems with one installer, and you didn't specify which one you tried; have you tried using another?

FYI:  The install I'm using now was made with *mantic* (23.10) media; because I had issues with the `calamares` installer; I used another ISO which used the `ubiquity` installer to bypass my issue to get this system functional (*in mere minutes*)*.*

---

### Post by Niytro on 2023-11-09
I have been using the Ubuntu Desktop 23.10 64-bit. It worked before and now it doesn't and it's literally the same ISO. I used the torrent link to download it and I keep it queued up in my client because I always use it to verify the integrity of the data--and download any missing data if needed--right before I create bootable media or copy the ISO over somewhere. So, I don't get it, it's the exact same ISO, written to the same USB drive with the same Rufus...but the bug remains. I got this bug in the beginning too but all I remember doing to get it to make the EFI partition correctly was this: I formatted the target USB stick in MBR with no partitions, booted into the Live Session, selected "Try Ubuntu", plugged in the blank drive, started the installer, made the proper selections and chose Manual Partitioning where I clicked the top SDC line, it had the blank space on a line below, then clicked the drop-down menu for the Bootloader Install Location and selected SDC again and it created the Bootable EFI partition on its own, about a gigabyte in size. The remaining space I formatted Ext4 with / as the mount point and hit next. But before those exact steps it gave me the same problem where it made a little single megabyte partition of just blank space, not bootabale EFI or anything. I did the same steps like I did before to get it to work and now it won't work for nothin...

Really, it's fine, I will get over it, it's just frustrating when I tried to follow my exact same steps as before and I figured I would make a post to see if anyone had run into the same issue and had some insight. I want persistence on a Live USB drive but not the way Rufus does it. I'm sure some of you are familiar with how Rufus creates persistence, using a method that works well but each time you boot into the USB it's like you're loading up the Live Demo instead of your actual system. I have to wait for it to load up and then hit "Try Ubuntu" on the menu that pops up and I can't password my account or encrypt anything...I just want a full system on a USB.

Thanks for the replies, maybe someone will come through with a fix eventually or it will work itself out.

---

### Post by oldfred on 2023-11-09
Will you use external drive with other systems?
UEFI or BIOS install? How you boot install media, is then how it installs.

Best to use gpt partitioning, not very old MBR(msdos) partitioning.
But with gpt you need either a 1MB unformatted partition with bios_grub flag for BIOS boot or the ESP - efi system partition with boot,esp flags. When first starting conversion to UEFI, I added both partitions as first two on all new or revised drives.

If UEFI install with Ubiquity installer, you have this bug which is a minor issue on internal drives as just preference on which drive has boot files, but major issue on external drives.

Posted work around to manually unmount & mount correct ESP during install #55 or( #23 & #26)
 [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)
Others suggest disconnecting all other drives physically or logically in UEFI settings, so install drive is first drive.
Or removing boot flag/esp flag from first drive, so only ESP is install drive. 
Or if you have ESP on second or external drive, you can just reinstall grub, either manually or using Boot-Repair's advanced mode & full reinstall of grub to correct drive. 


While have many flash drives with full installs, now have SSD in USB/SATA adapter and that is almost as fast as internal SSD drive. Will not go back to slow flash drives for full installs. Will probably use just for some data storage.

---

### Post by sudodus on 2023-11-10
The alternative 'persistent live system' behaves as you describe (and is supposed to behave like that), but I think you want an **installed system**, in your case installed into an external drive but otherwise just like it were installed into an internal drive.

There are many ways to create such a system. I suggest an easy way:

- Start from a compressed image of Ubuntu Server, extract and clone it to the external drive where you want it (it will grab the whole drive) in the external drive.

- Boot into Ubuntu Server in the external drive and update & upgrade it and then install whatever program packages you want, maybe lubuntu-desktop or xubuntu-desktop which brings the graphical desktop environments of the light-weight Ubuntu family flavours Lubuntu or Xubuntu.

See [this link](https://ubuntuforums.org/showthread.php?t=2474692). Read the whole tread before starting to do anything.

---

