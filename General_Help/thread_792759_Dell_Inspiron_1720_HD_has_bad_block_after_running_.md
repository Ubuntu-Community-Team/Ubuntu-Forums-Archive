---
title: "Dell Inspiron 1720 HD has bad block after running Ubuntu 8.04 from CD"
date: 2008-05-13
forum: General Help
---

### Post by vinciepoo on 2008-05-13
Hi folks,

I am not an Ubuntu user, and joined the forum just to ask this question. My wife has a Dell Inspiron 1720 (not the N model), with Windows Vista Home Edition. My stepson, being the curious type, decided without our knowledge to try to run Ubuntu 8.04 from the disk. He swears he didn't install anything. Anyhow, long story short, when my wife tried next to use the machine, it gave a warning on startup, and Vista strongly suggested running the HD check utility, which my wife did. By morning, Vista wouldn't even kick in on startup, going instead to a black screen with a blinking cursor. The pre-boot utility and System Tree diagnositc tool both revealed a single bad block on the HD.

My stepson says this has to be a coincidence because he didn't install anything (i.e., the hard drive was going to go bad anyway). So my question to the forum is whether it is possible or even likely that this bad block resulted directly from running Ubuntu 8.04 from the live CD (he downloaded and burned it himself), or indirectly from all the diagnostics ran afterwards. I don't know enough to judge, although I have seen other posts elsewhere that make me wonder (e.g., Vista+Ubuntu=Death).

Thankfully the machine is still under warranty, and Dell is sending a replacement HD; but my wife had some work-related files on there that hadn't been backed up in a while, and we've been unsuccessful recovering them.

We're contemplating whether my stepson should be grounded for doing what he did without our permission, and I will take your comments in consideration; so thanks very much in advance for whatever insight you can offer!

---

### Post by rbmorse on 2008-05-13
Bad Blocks just happen. Really. 

The CD your stepson downloaded has a feature called "liveCD" that enables the operating system on the CD to boot the computer and execute application programs from the O/S on the CD (in this case Ubuntu) entirely from the CD...not the host computer itself.  It really does not install anything to the hard drive, until you tell it to do so. 

Of course, once booted you can do all kinds of stuff to the host computer if you want, but without further evidence or indications what your stepson told you is entirely plausable. 

In fact, the kid may save your rear end. One of the things you can do from the CD is boot the computer and see if it will mount the hard drive and read the files that are undoubtedly still on it. 

You will need:

1. the kid 

2. some sort of file storage device (flash drive, floppy drive, hard drive) that connects via a USB port.

3. Boot the machine from the Ubuntu CD.  When it's fully loaded, click on the "places" menu and see if the hard drive was automatically detected and mounted. If it was you can connect the USB device and copy off the files you need to save.  If it wasn't: 

4. open a terminal window from the menu (Applications > Accessories > terminal)

4. enter the following at the terminal prompt  (don't include any phrase  that starts with a # character):

cd /media
sudo mkdir harddrive    #<-- forum: does he need sudo here with the LiveCD?
sudo mount -t ntfs /dev/sda1 /media/harddrive     #<-- or here?
cd harddrive
dir

Do you see a list of files and directories? If so, that's the data on the hard drive.

The easiest thing to do at this point is to close the terminal and connect the USB storage device. Give it a minute to load and mount (should happen automagically) then use the graphical file manager (click on "places" in the menu, find "hardrive" in the listing of devices and click on it) and copy the files you need to save to the USB storage device. It should work just like Windows Explorer for this purpose).

When you get the new hard drive installed and and configured (good luck with that) you can copy the data files from the USB device into the new Windows environment.

---

### Post by vinciepoo on 2008-05-19
Thanks a bunch for the suggestions! :KS  The only thing I didn't agree with was #1, as I decided to do this without the kid's further assistance.  :)  I did, however, borrow the liveCD he had burned, and successfully used Ubuntu 8.04 to get files off the bad drive, which did mount automatically. 

Unfortunately, most of the files of interest had been tucked away by CheckDisk in a directory called found.000. So I have a bunch of .chk folders and files to try to make sense of. I did get some files off completely intact, but those weren't the files we really wanted. Anyhow, at least I do have something to work with, and I was able to move found.000 to a "safe" hard drive for further analysis.

I've tried something called Undelete 5, which did piece together one folder for me (again, not the files I really wanted). I'm going to try another utitlity on the rest of the mess. Not sure which one to try first, but there seem to be several out there.

Of course, my stepson has been cleared of any wrongdoing, although we do want him to do his experimenting on his own machine, or at least ask first before getting his mother's laptop involved. That's another talk show. Still, in some sense I'm glad this happened, as there were a number of lessons in it for me. Now I know another approach to take when faced with a drive going bad.

Thanks again for the help! :KS   I wish I had thought of trying to do this the last time I had a bad hard drive.

---

