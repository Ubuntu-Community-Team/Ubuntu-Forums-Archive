---
title: "Need help getting files on Linux KDE Ubuntu computer"
date: 2018-06-23
forum: General Help
---

### Post by darkcyber on 2018-06-23
I have a computer running KDE Ubuntu 14.04 LTS and I cannot get my NTFS hard drives to be seen by the OS. So, I need some other way to load my tons of .wav music files onto this computer from my Windows 10 computer. Any suggestions would be greatly appreciated. I am new to Linux, but have over 40 years on Windows based systems.

---

### Post by HermanAB on 2018-06-24
Do you have ntfs-3g installed?

Anyhoo, all versions of Windows supports Anonymous FTP natively and the latest Win10 also supports SSH.  Therefore transferring data to a Linux machine should be fairly simple.  Set up an Anonymous FTP server on the Linux machine and use the file browser (or FileZilla Client) to connect.

---

### Post by SeijiSensei on 2018-06-24
So, to be clear, the NTFS hard drives are mounted in a different machine than the one running Linux?  Is that machine exporting these files using Windows filesharing (known these days as "CIFS")?

If they are on a separate, networked Windows computer, try opening Dolphin, then double-click in the address bar at the top of the window to enable text input.  Enter the URL "smb://server/share" in the address bar, replacing "server" with the name of the Windows machine and "share" as the name of the fileshare to which you are connecting.  You should be prompted to enter your username and password on the Windows system. If you cannot reach the server by name, replace "server" in that URL with the IP address of the Windows machine.

If you can establish a connection, then I suggest hitting the "Spilt" button in Dolphin.  This will open two windows.  Repoint one of them to the location on the Linux machine to which you want to copy the files, then drag-and-drop them from one window to the other.

If you've moved the physical disks into the Linux box, we need to walk through a different set of steps.

---

### Post by darkcyber on 2018-06-24
Actually, I have a Western Digital 4 TB external USB hard drive. I just used it out of the box to backup all of my .wav music files. It shows the drive is NTFS with 3.63 TB of space. I downloaded all my music from my Windows 10 computer onto this drive. Now, I am connecting that drive to my Ubuntu 14.04 computer and trying to get it to see the drive so I can copy all of that music onto the Ubuntu computer. ntfs-3g is supposed to be installed in this version by default. I have also tried to install it manually and get an error that it is already installed. When I hook up the drive to the Ubuntu computer the only drive I see is my internal 1 TB hard drive and nothing else. Thus, this is where my problem is...I cannot get the Ubuntu computer to detect/see the external drive. I have also tried a 1 TB external drive as well and can't get it to see it either. The main thing I was working for was to get Ubuntu to detect/see the external 4 TB drive hooked to it so I could easily download my file onto the Ubuntu computer.

On another note, I have tried going across my network to download them from my Windows 10 computer. I can see the Windows 10 computer from my Ubuntu computer, but when I click on the computer icon in networking it will not bring up anything. It gives some kind of a timeout error. Will try your suggestions. Thanks!

---

### Post by SeijiSensei on 2018-06-24
Usually KDE will pop up a notification box when you connect a USB device and ask you what you want to do with it.  

Let's try a couple of things at the terminal.  Unplug the USB drive and any other USB devices like thumbdrives.  Open Konsole, then type "lsusb" at the dollar-sign prompt.  You will get a list of all the USB devices the OS sees.  Now plug in the drive, and run the lsusb command again.  Does the drive not appear in the list?

If the drive appears, then run "sudo blkid -l" and enter your password when prompted. You'll get a list of all mountable filesystems. An edited list from my system here looks like:

```

/dev/sdb1: UUID="44f3b810-50e3-48dd-9880-ca18d86b9c19" TYPE="ext2" PARTUUID="fb4ac0b6-01"
/dev/sdb3: UUID="1E1E81AF1E81808F" TYPE="ntfs" PARTUUID="fb4ac0b6-03"
/dev/sdb5: UUID="5ad2f16e-6c75-46c2-85de-dc101803ae91" TYPE="ext4" PARTUUID="fb4ac0b6-05"

```
This shows the boot partition, which I format with ext2, an NTFS partition, and the main ext4 system that is the root of my filesystem.   Do you see the USB filesystem listed there?  If so, use the device identifier at the beginning of the line that corresponds to the USB drive, and enter
```
sudo mount /dev/sdxn /mnt
```
where /dev/sdxn would be something like /dev/sdc1. Does it throw an error?  If not, what do you see when you type "ls /mnt"?

Does the drive use USB 3.0, but you have it connected to a USB 2.0 port? I don't think that matters, but you never know.

---

