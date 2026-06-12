---
title: "Rejecting I/O to offline device"
date: 2007-12-11
forum: General Help
---

### Post by starfleetcaptainrob on 2007-12-11
Anyone ever seen anything like this before?

Rejecting I/O to offline device

[43134767.380000]  EXT3 - FS error (Device SDA1)
EXT3 - read dir: direction [variable number] contains a hole at offset [variable number]

I didn't see this first hand, my coworker did, but I'm hoping that someone's seen this before.  We're running a Ubuntu server 6.06.  This message fills the screen and we're unable to control the server.  Our only option is to reboot.  This has happened twice in the last week...

---

### Post by Dryw Paulic on 2007-12-11
Hey Star Fleet Captain!

Couple questions with regards to your setup:

[LIST]
[*]Are you using any type of RAID?
[*]If so, is the RAID dirty?
[*]Is the problem intermittent?
[*]Did this just start happening recently or has the server always been having issues?
[/LIST]

My recommendation would be to run e2fsck to ensure that there is no corruption on the disk. One word of caution - - **DO NOT** run e2fsck on a mounted filesytem, as it can cause issues. I suggest booting up from a livecd and running something like the following command:

```
e2fsck -cc -b 32768 -y /dev/dryw
```

**-b** Uses an alternative superblock to the main superblock, just in case it is corrupted. The location of the superlblocks on your drive will be dependent on the overall block count. You can figure out the superblock locations by doing a "tune2fs -l", grabbing the block count and then making a file with the same block count/filesystem type. When you create the file it will tell you the superblock locations :). You can omit this option if you would like, since if your superblock was corrupted you would not be able to mount the filesystem.

**-cc** Makes e2fsck run badblocks using a non-destructive read-write test. 

**-y** Run non-interactively.

After you run that, you can run something like Bonnie++ to benchmark the drive to see if the drives performance looks proper. I would recommend that you do this test at off hours as it puts a lot of strain on the system:

```
bonnie++ -d ~/testdir -s 2016M -n 10:102400:1024:1024 -m Oblivion -q > bonnie_test.csv
```

**-d** Test Dir. Just needs to be writable by the user.
**-s** File size in MB. Should be twice the amount of ram in the machine or so. 
**-n** File creation options: File Size (in MB):Max-Files:Min-Files:Number of directories
**-m** Machine name. Just makes it easier to remember :)
**-q** Quiet Mode


And finally, redirect to a nice CSV that a spreadsheet program can open. Let me know how everything goes!

---

### Post by pbr6891 on 2008-04-20
I am having a very similar situation ....

USB attached drive go offline while transfering (reading) from drive ...
Drive appears to be clean (e2fsck) and performing well when it works ...

The is no RAID array on my system ...

I have tried changing the USB2.0 PCI card in the computer (Pentium 3 800Mhz with 256M ram) , it looked better for about day (managed to copy 3 250G drives without issues) and then the drive offline issue came back ...

The drive I am trying to read is a 250G PATA with a PATA-USB2.0 adapter ....

The drive mounts properly, and I can read/write to it until it goes offline... I can cause the drive to go offline by starting a copy of the content using wget ... It seems to be locking up after various amounts of data is transfered (usually 10's of GB before locks up.)

Help !

---

