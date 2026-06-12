---
title: "Ubuntu 17.10 Not Working After Running Bleach Bit On My Laptop"
date: 2018-05-20
forum: General Help
---

### Post by mogruith2 on 2018-05-20
Hi, today I chose to use Bleach Bit to clean up various junk on my laptop (which has Ubuntu 17.10 preinstalled) 

I selected the option of cleaning 'free space' on the drives.

The program ran fine but on reaching 99% complete it just hung, so I eventually opted to close it, for whatever reason that did not complete.

So I decided to power-down the laptop and reboot it, **now** all that shows on the screen is about forty lines of code.beginning with: 

[B][ok] created Slice User SLice of gdm 

[/B]and after a series of other lines ends with[B], 

**[ok] Started Hostname Service.ager Dispatcher Service....ystem changes.pp link was shutdown**[/B]

Has anyone else had this issue? Can someone please offer a solution?

Thanks in hope

mogruith

---

### Post by HermanAB on 2018-05-20
The best way to recover is to re-install.  It only takes about 30 minutes or less.

---

### Post by #&amp;thj^% on 2018-05-20
I'm not one that recommends a Reinstall but in this case I would.
When using BleachBit I always run it in the terminal. When it runs in a terminal, it prints extra information to the console. Some of this information may be useful for troubleshooting.
But powering down forcefully while it is writing over the disk is never a good practice. :(
When you enable the "free disk space" cleaning option under "system," filling the disk is normal. That's how it wipes the free disk space. However, freezing the system is of course not normal. Normally the free disk space slowly approaches 0 bytes free, but once it reaches 100% full, the large file is quickly deleted.
Wish I had better news to report for you. :(
```
bleachbit --help
Usage: bleachbit [options] cleaner.option1 cleaner.option2

Options:
  -h, --help            show this help message and exit
  -l, --list-cleaners   list cleaners
  -c, --clean           run cleaners to delete files and make other permanent
                        changes
  --debug-log=DEBUG_LOG
                        log debug messages to file
  **-s, --shred           shred specific files or folders**
  --sysinfo             show system information
  --gui                 launch the graphical interface
  -p, --preview         preview files to be deleted and other changes
  --preset              use options set in the graphical interface
  -v, --version         output version information and exit
  -o, --overwrite       overwrite files to hide contents

```

---

### Post by mogruith2 on 2018-05-20
Thanks for your kindness in responding, I'm hoping if it is at all possible to avoid having to reinstall as I am concerned at losing items and maybe bookmarked sites

---

### Post by mogruith2 on 2018-05-20
I'm wondering if maybe I could boot my system via the BIOS? If so can you advise what the procedure would be once I had access to BIOS?

---

### Post by #&amp;thj^% on 2018-05-20
> **mogruith2 said:**
> Thanks for your kindness in responding, I'm hoping if it is at all possible to avoid having to reinstall as I am concerned at losing items and maybe bookmarked sites

You can try to recover your files that you want/need with a LiveCd/USB installer..
Have a look here: [https://help.ubuntu.com/community/LiveCdRecovery](https://help.ubuntu.com/community/LiveCdRecovery)

---

### Post by mogruith2 on 2018-05-22
An update, I created a bootable USB flash drive to install Ubuntu 18.04. I managed to get that running and at present I'm at the stage of installation where it's saying:

'Erase Ubuntu 17.10 and reinstall' or 'Install Ubuntu 18.04 alongside 17.10'

My laptop's manufacturer advised that: [I]"select the 'Erase Disk and install Ubuntu' option. Regarding backing up your data. You would have to reboot and boot into  the USB drive again, once here select the Try Ubuntu without installing  option. Once this has booted up you can mount your hard drive and copy  you data over to another storage device. Once this has been done you can proceed with the reinstall and erase all data  on the device.".
[/I]
[FONT=Calibri,Helvetica,sans-serif][SIZE=3][COLOR=black] I rebooted and booted into the USB drive, I am though not seeing any option to 'Try Ubuntu without installing option'

So I am wondering how to progress this now,  as[/COLOR][/SIZE][/FONT] the manufacturer says that[I] "Please assure that all your files are backed up before performing this  as it will erase all data on the device and you will not be able to get  them back."
[/I]
But I'm guessing that such a backup (if I knew how to do that prior to installing Ubuntu 18.04) would not save any Apps which I had with 17.10, nor save bookmarked sites. Is that right? If so what's the point of me trying to do a backup, could I not jusy install and delete what's on there and start afresh?

Any thoughts advice on this would be a real help

---

### Post by #&amp;thj^% on 2018-05-22
Your right this won't save installed apps, and that is as it should be. Hope that makes sense. (Drivers, 3rd party sources etc. etc.)
But you can backup all the rest EG: Documents, Pictures, Video's, and Yes you can recover your Bookmarks also and ".conf"
Curious though as to why you don't see Try Ubuntu option? :confused: 
But if this is to difficult to follow, then yes you could just wipe and install a fresh.
But it would be a great chance for you to expand your skills to try to back up what I've listed above.

---

### Post by mogruith2 on 2018-05-22
Hi 1fallen

Me being the eejit I am the option of 'using Ubuntu without installing' was there all the time, doh!

Ah well, I was able to get there eventually, now I have managed to locate files, images and downloaded apps 
and copied them to an external hard drive. So there safely secured.

My question is now, since I have those can I just go ahead an install Ubuntu 18.04 (using the erase and install option)
or do I still need to mount the hard drive on my laptop before such an installation?

Again any help and advice on this would be really welcomed.

---

### Post by #&amp;thj^% on 2018-05-22
You are NOT a eejit nobody knows all this that is Linux. ;)
If you now have all you wanted backed up then you can now proceed with the wipe and install Ubuntu now.
May all go well for now. :)

---

### Post by mogruith2 on 2018-05-22
1fallen, I am very grateful for your kindness and advice, Happy to say that I have now installed Ubuntu 18.04 onto my laptop, suffice to
say I shall not be using again Bleach Bit to clean the disks! I'm hoping the various gremlins some have mentioned with respect to this
latest version do not cause me any undue inconvenience. Regards :)

---

### Post by #&amp;thj^% on 2018-05-22
That's Great News! :)
good work mogruith2 and you are well on your way to a better understanding of your system.
Just post new problems you encounter here in the proper forums.
Kind Regards

---

