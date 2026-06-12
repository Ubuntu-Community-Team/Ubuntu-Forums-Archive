---
title: "Ubuntu 14.04"
date: 2015-10-02
forum: General Help
---

### Post by gordon33 on 2015-10-02
Hello All

I had  my HP lap top set up for a dule boot.  Yesterday went to clean up some problems with windows by resetting the windows.  This took hours.  This morning I restarted the computer and the boot up screen was gone and the computer went strait  to windows.  It was set up to go strait to Ubuntu.  All the important files / folders were saved on Ubuntu.  _What do I need to do to get the Ubuntu back?_



Gordon33

---

### Post by westie457 on 2015-10-02
This is a good place to start using the media you did the installation with.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by gordon33 on 2015-10-02
Hello westie457

Thank you for the reply.

I will start on this as soon as I can.

Gordon33

---

### Post by gordon33 on 2015-10-02
So I looked at the link provided.  step 1 said 

"Remark : it is recommended to install the ISO on a live-USB (eg via UnetBootin or LiliUSB or Universal USB Installer). Do not burn it on a DVD if your computer has Windows8 pre-installed, or if your boot is in EFI mode. "

The lap top came with Windows 8.  my plan was to do a save and then save to a usb stick and then see if it would install.  I have ben unable to find the boot-repair if it is getting saved.  I did not vind it doing a search or in the download folder.  I have ben unable to save it to the usb stick.

Gordon

---

### Post by gordon33 on 2015-10-02
I have been able to find the Boot-Recovery in the download folder.  So I saved it to the usb stick.  

Changed the bios : disabled the Secured Boot and then picked the USB to boot first.  Since their were 2 USB's to pick I chose one then the other.  

No luck in getting the USB with Boot Recovery to boot first.  Any help of ides?

Gordon33

---

### Post by gordon33 on 2015-10-02
Hello

I really am missing Ubuntu.

Gordon33

---

### Post by westie457 on 2015-10-04
I have always found it easier to use a Live DVD/USB of Ubuntu and use option 2 in the link posted earlier.
For best results the Live media should be the one you used for the installation.
Before allowing any repairs to the boot select the 'Boot Report' option. Post the generated link so we can peruse the report and offer further advice.

---

### Post by gordon33 on 2015-10-04
hello  westie457's 

Thank you for the direction.  As you said choosing the second option proved to be the easiest approach to getting the repair program.

 I have been able to get the Ubuntu 14.04 to show up again.  

At the end of the repair the following URL was given: [http://paste.ubuntu.com/12686784/](http://paste.ubuntu.com/12686784/) as a link for others to provide additional direction if needed.

Thank you again.

Gordon33

---

### Post by westie457 on 2015-10-05
Is everything now working as expected?

You have a situation that may be problematic in the future. > [COLOR=#000000]The disk contains an unclean file system [/COLOR][COLOR=#666666]([/COLOR][COLOR=#000000]0, 0[/COLOR][COLOR=#666666])[/COLOR][COLOR=#000000].[/COLOR]Metadata kept in Windows cache, refused to mount.
Failed to mount [COLOR=#BB4444]'/dev/sda1'[/COLOR]: Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully [COLOR=#666666]([/COLOR]no hibernation or fast restarting[COLOR=#666666])[/COLOR], or mount the volume
[COLOR=#AA22FF]read[/COLOR]-only with the [COLOR=#BB4444]'ro'[/COLOR] mount option.
mount -t ntfs-3g -o remove_hiberfile /dev/sda1 /mnt/boot-sav/sda1
This becomes an issue if you to write files from Ubuntu/Linux to an NTFS partition. The files will not show after Windows is booted.
 You can either run the suggestion in the quote (I am not sure if they have to be run for every NTFS partition) or you can follow these links.
[URL="http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html"]
http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html[/URL]
[URL="http://www.sevenforums.com/performance-maintenance/254655-remove-hibernation-file-hiberfil-sys.html"]
http://www.sevenforums.com/performance-maintenance/254655-remove-hibernation-file-hiberfil-sys.html[/URL]

They work for Windows 10 also.

---

### Post by gordon33 on 2015-10-05
Hello westie457

The only thing I see, is I do not have the grub menu at boot up.   So, I have to go into Bios to select Ubuntu.

Thank you for checking the information over.  I will look at the links provided as soon as I have time.

Gordon33

---

