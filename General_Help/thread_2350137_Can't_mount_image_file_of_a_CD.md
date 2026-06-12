---
title: "Can't mount image file of a CD"
date: 2017-01-21
forum: General Help
---

### Post by Ralph L on 2017-01-21
I have an old game CD (Bicycle Bridge).  I am running it under Wine and it runs reasonably well (with a few aborts, but that's another problem).  Bicycle Bridge requires that the CD be mounted in order to run.  I used Brasero to make an image file of Bicycle Bridge, selecting Disk Copy, and then selecting "Image file" under "Disk to write to".  The file name of the image file came out as BBRIDGE.toc.bin.  I then installed, from a ppa, gcdemu.  This mounts the image file fine (as /media/ralph/BBRIDGE).  So I know the image file can be mounted.
Using gcdemu leaves me with a problem:  I want to do the mount from the launch command in Menu Editor so I can't use the gcdemu gui.  I have been trying to use the "mount" command, but can't seem to make it work.  I tried the following and got an error:```
ralph@Tosh:~$ sudo mount ./BBRIDGE.toc.bin /media/BBRIDGE -o loop
mount: wrong fs type, bad option, bad superblock on /dev/loop0,
       missing codepage or helper program, or other error

       In some cases useful info is found in syslog - try
       dmesg | tail or so.


```I also tried a bunch of other mount commands, but I was just groping in the dark.  I don't understand what kind of a file Brasero created.  Is it an iso9660 file??  Or is it some other file type with a .toc.bin suffix??  Also, I don't know what a "loop" file is, and I don't know what the option "-o loop" does?

Any help appreciated.....

---

### Post by SeijiSensei on 2017-01-21
You can try adding "-t iso9660" to the mount options and see if that helps.

Usually disk images are written to files ending in .iso like the various [Ubuntu installation images]("http://cdimage.ubuntu.com/ubuntu/releases/16.04/release/").  I'd usually try making the copy from the command prompt with the dd command:
```
dd if=/dev/sr0 of=/path/to/bicycle_bridge.iso
```

I happen to have a copy of Bicycle Bridge and just installed it under wine after making a copy using dd.  It complained about some bad sectors, copy protection no doubt, but it mounted fine with "sudo mount /path/to/bicycle_bridge.iso /mnt".  I navigated to the directory where setup.exe was stored, ran "wine setup.exe", then ran "wine BRIDGE.EXE" from ~/.wine/drive_c/Program Files/Expert Software/Bicycle Bridge®/.  It worked fine.

---

### Post by Ralph L on 2017-01-22
Thank you very  much for your response, but still no joy.
> You can try adding "-t iso9660" to the mount options and see if that helps.
This didn't work on the image file BBRIDGE.toc.bin created by Brasero.
I tried your suggestion of copying the file with dd:```
ralph@Tosh:~$ dd if=/dev/sr0 of=bbridge.iso
dd: error reading '/dev/sr0': Input/output error
86912+0 records in
86912+0 records out
44498944 bytes (44 MB, 42 MiB) copied, 27.4932 s, 1.6 MB/s

```
The size of BBRIDGE.toc.bin created by Brasero is 139,697,040 bytes, so the dd copy didn't complete.  I googled the error message and found that some people think that error is because of data protection built into the CD, but it worked on your Bicycle Bridge and Brasero was able to make a successful copy.  Any other thoughts on what I can do???
Also, you say your Bicycle Bridge works fine.  Mine aborted during installation, but still runs. Did your install abort?? Also, mine aborted once while I was looking at Help, but I haven't been able to make it abort again.  I have a dump of that abort also.  Oh, I wanted to use the latest stable copy of Wine, so I installed Wine 1.8.5 using the instructions for version 1.8.5 given here: [http://www.tecmint.com/install-wine-on-ubuntu-and-linux-mint/](http://www.tecmint.com/install-wine-on-ubuntu-and-linux-mint/) .  I'd like to hear about any problems/fixes you have for Wine/Bicycle Bridge, since my wife practices on it a lot and I get flack whenever it doesn't work right.

---

### Post by SeijiSensei on 2017-01-23
I got about the same results using dd, about 45 MB, and the image mounted successfully with
```
sudo mount /path/to/bicycle_bridge.iso /mnt
```
I didn't have any problem running "wine setup.exe" from the appropriate directory under /mnt.  It brought up the installer, and I went from there.

After "wine BBRIDGE.EXE" the program loaded and dealt me a hand.  The audio worked as well.  

This was on a machine running a fairly vanilla version of Kubuntu 14.04 with the repository version of wine.

---

### Post by Ralph L on 2017-02-13
Thanks SeijiSensei for taking your time to help me.  I decided to take a little different approach than you, but it worked.  Knowing that gcdemu could load the special .toc.bin image file that Brasero created, I looked for and found a command line version of cdemu called cdemu-client, using Synaptic, in the standard repository for cdemu.  This allowed me to mount the .toc.bin file at startup by adding 2 commands to Main menu>Settings>Session and Startup>Application Autostart (Add is at the bottom of the window).  The two commands were:```
cdemu add-device
cdemu load any /home/ralph/Documents/Wine_storage/bicycle_bridge/bbridge.toc.bin
```(Note: Documents is my separate Data disk partition that makes it easier for me to install and run multiple OSs).  I tried to put both commands on one Autostart entry separated by &&, but it wouldn't work.
With the bbridge image file loaded all the time, Bicycle Bridge starts from the Main menu without having to insert the CD or do anything special.

---

