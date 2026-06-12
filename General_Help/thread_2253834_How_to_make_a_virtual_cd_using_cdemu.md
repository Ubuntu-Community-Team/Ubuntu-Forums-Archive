---
title: "How to make a virtual cd using cdemu"
date: 2014-11-22
forum: General Help
---

### Post by Ralph L on 2014-11-22
I am trying to make a virtual cd from a game disk that needs to be in the cd drive to run.  I got cdemu installed, but I can't make it "load" the game disk.  Here is what I tried that didn't work:
1.  Ran System Tools>gCDEmu.  It put an icon in my task panel.
2.  Clicked the cdemu icon in the task panel, selected Device #00 Empty, and it brought up a window.
3.  Clicked the Load button and it brought up a window title "open file", and allowed me to select any file my system.
4.  On the left panel I selected the cd in my cd drive that I wanted to become a virtual cd.  It listed all the files on the cd and wanted me to select one of them.  However, I don't want just one file.  I want to load the entire cd, which it won't do.

What am I doing wrong?  I don't know what kind of cd it is--ISO, other???  Everything I see about creating a virtual cd talks about ISO cds--whatever they are.  Mine is just a game cd that my wife puts in a drive on her windows system, executes a file called "setup.exe" and the game runs.

Any help appreciated.

---

### Post by Ralph L on 2014-11-23
I answered my own questions.  To use a hard disk file as a virtual cd apparently requires that an iso 9660 copy of the cd be made on the hard disk.  [http://kvz.io/blog/2007/08/01/make-iso-images-on-linux/](http://kvz.io/blog/2007/08/01/make-iso-images-on-linux/) explains how to do this.  It is simple.  Put the cd in the drive, let the system discover it, and execute the command: ```
sudo dd if=/dev/cdrom of=cd.iso
``` In this case the iso file created will be "cd.iso" in the home directory.  Then cdemu can be used to mount it:  go to Main menu>System Tools>gCDEmu and launch it.  This puts an icon in the task panel.  Click on the icon and select "Device #00 empty" and a window comes up.  Click on the Load button and select the file "cd.iso".  Nautilus will now show a new device in the left pane called cd.iso.  Since I have wine installed on my system, I just double clicked the new device (cd.iso) (in Nautllus) and the various files were display in the right pane.  I right clicked the .exe file, selected open with wine and my game installed itself in wine.  To actually run the game I went to Main menu>wine>Browse C: Drive, which brought up Nautilus on the ~/.wine directory.  I found my game under Program Files.  I right-clicked the .exe file, selected Open with Wine, and the game ran.

As explained in [http://kvz.io/blog/2007/08/01/make-iso-images-on-linux/](http://kvz.io/blog/2007/08/01/make-iso-images-on-linux/) cdemu isn't necessary to mount an iso file for use by the system.  Instead of using cdemu I could just have executed ```
mkdir -p /mnt/isoimage
mount -o loop -t iso9660 cd.iso /mnt/isoimage
```
Then I would have opened the new device (cd.iso) with Nautilus and proceeded as above.  I don't know if it will be necessary to fiddle with /etc/ftab in order to have the game always available after system startup.

---

### Post by coldraven on 2014-11-23
You can also create .iso files with just about any disc burning program. Instead of using the "Copy Disc" option you use the "Burn Image" option. Then instead of burning to a blank disc choose "Save Image".

---

