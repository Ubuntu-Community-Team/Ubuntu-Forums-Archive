---
title: "MTP on Lubuntu"
date: 2013-03-03
forum: General Help
---

### Post by gotnexusbluz on 2013-03-03
Please don't tell me to go search the forum, I have been doing this all day through Google and I am starting to get very lonely!  

My Galaxy Nexus isn't much use to me when I cannot transfer files, and I'd much prefer not to boot Windows for this reason alone. My last favored OS was Xubuntu, and now I have the dirt on my new Galaxy Nexus's "feature" of ignoring all cables without MTP on both ends, which most of Linux isn't up for yet. Some OS reviewer proclaimed that LXDE (Lubuntu) has MTP, so I gave it a run. Unlike Xubuntu, it did give me the popup window with "you have a new device connected" with the invitation to open and view files on it. However, it failed to actually display any of the files on these drives. So it's not 100% MTP ready!

A few google searches indicate that some users know the missing software which makes Galaxy Nexus (or at least I think) talk to Lubuntu. I installed (or re-installed) a number of library files, including libmtp, libmagic, libfuse, and more, but still Lubuntu won't display my files (the file manager indicates a connection, but shows nothing within). Hours later, I have no idea what I was really doing, as nobody seems to have posted a walk-through for those of us who don't really have the software developer's understanding of how this system works. Can anyone explain what is missing and needs to be installed for the Nexus phone?

I am running Lubuntu on a Toshiba Satellite laptop, if that makes a difference.

---

### Post by duke.tim on 2013-03-04
I've been having problems with mtp too, not quite ready for linux.
I've included some useful instructions below the Manual Mounting section.


If you don't mind a little command line you can mount it like this:[SIZE=4][SIZE=5]
Manual Mounting Android MTP Devices[/SIZE]
Step 1![/SIZE]
Make sure you have libmtp
```
sudo apt-get install libmtp
```
> References
[http://packages.ubuntu.com/source/lucid/libs/libmtp](http://packages.ubuntu.com/source/lucid/libs/libmtp)
[http://packages.ubuntu.com/quantal/i386/mtp-tools/filelist](http://packages.ubuntu.com/quantal/i386/mtp-tools/filelist)

(This is what I do from Fedora, should be pretty similar to Ubuntu)
[SIZE=3]Step 2![/SIZE]
Find the MTP device
```
mtp-detect
```


[SIZE=3]Step 3![/SIZE]
Choose directory to mount to

In this case I make a directory
```
sudo mkdir /mnt/Android_Device
```

[SIZE=3]Step 4![/SIZE]
```
sudo mtpfs -o allow_other /mnt/Android_Device
```

Then I browse via the Shell, as it stops me when I try using nautilus.
[SIZE=3]I have not tried point and click browsing using nautilus on Ubuntu yet so try it before using the command line.[/SIZE]
[SIZE=4]
Optional step 5!
[/SIZE]Using the shell !!! (lots of exclamation points)
ChangeDirectory,Copy, Remove,Move file:
```
cd /mnt/Android_Device
cp /source/file /mnt/Android_device/Destination
rm /mnt/Android_device/Selection
mv /source/file /mnt/Android_device/Destination

```

[SIZE=4]
Step I'm Done![/SIZE]
To unmount try one of the following
```
umount -l /mnt/Android_Device
```

```
sudo fusermount -u /mnt/Android_Device
```




=======================================================================================================================================================
[SIZE=5]This Webpage looks helpful[/SIZE]


Also this web page looks very promising
[http://www.webupd8.org/2012/12/how-to-mount-android-40-ubuntu-go-mtpfs.html](http://www.webupd8.org/2012/12/how-to-mount-android-40-ubuntu-go-mtpfs.html)

It has you add a repository, and then install go-mtpfs
```
sudo add-apt-repository ppa:webupd8team/unstablesudo apt-get update
sudo apt-get install go-mtpfs
```

```
[COLOR=#000000][FONT=UbuntuBeta Mono]sudo apt-get install go-mtpfs-unity[/FONT][/COLOR]
```

The site does list some warnings!
> [B]Notes: 

[LIST]
[*]Unmounting the device via Nautilus does not work!
[*]Sometimes you may get an error if the device is locked, so unlock it before trying to mount it;
[*]When plugging in an Android device via USB, Ubuntu will try to mount it and it's a good idea to stop this by clicking the unmount icon in Nautilus.
[/LIST]
[/B]

---

### Post by dargaud on 2013-03-04
I've never been able to get MTP to work on my Galaxy II either. So I simply don't use it ! I configure the phone in mass storage mode: Settings | More | USB utilities | Connect storage to PC, then connect cable and click OK. I know some people who prefer to install a ssh server on their phone and do everything via wifi...

---

### Post by gotnexusbluz on 2013-03-04
Thank you for providing so much useful information!

I got everything installed, and ran your commands, which are similar in 'Buntu World. 

After everything was installed, I ran

mtp-detect
sudo mtpfs -o allow_other /mnt/Android_Device

I was able to mount my phone just once, and the first thing I did was test it with an ls command. Every folder with my stuff listed when I did a cd to one of two folders displayed, and that was Internal (I forgot the other already). An ls on this displayed the folders containing all of my stuff, but it also attempted to display what Verizon had locked up (unrooted phone, didn't think I would need to be rooted), reporting nasty errors for each such idem as they scrolled the screen. It listed some other errors before disconnecting my phone, which I think were the same ones which it lists every time that I try and connect with -o allow_other:

davepc@MyPC:~$ sudo mtpfs -o allow_other /mnt/Android_Device
[sudo] password for davepc: 
Listing raw device(s)
Device 0 (VID=04e8 and PID=685c) is a Samsung Galaxy Nexus/Galaxy S i9000/i9250, Android 4.0 updates.
   Found 1 device(s):
   Samsung: Galaxy Nexus/Galaxy S i9000/i9250, Android 4.0 updates (04e8:685c) @ bus 2, dev 16
Attempting to connect device
Android device detected, assigning default bug flags
Listing File Information on Device with name: (NULL)
fuse: bad mount point `/mnt/Android_Device': Transport endpoint is not connected
davepc@MyPC:~$ cd /mnt/Android_Device


These errors displayed after I unplugged the USB, trying to start over again - what do you think of this? 


> **duke.tim said:**
> I've been having problems with mtp too, not quite ready for linux.
I've included some useful instructions below the Manual Mounting section.

If you don't mind a little command line you can mount it like this:[SIZE=4][SIZE=5]
Manual Mounting Android MTP Devices[/SIZE]
Step 1![/SIZE]
Make sure you have libmtp
```
sudo apt-get install libmtp
```


(This is what I do from Fedora, should be pretty similar to Ubuntu)
[SIZE=3]Step 2![/SIZE]
Find the MTP device
```
mtp-detect
```


[SIZE=3]Step 3![/SIZE]
Choose directory to mount to

In this case I make a directory
```
sudo mkdir /mnt/Android_Device
```

[SIZE=3]Step 4![/SIZE]
```
sudo mtpfs -o allow_other /mnt/Android_Device
```

Then I browse via the Shell, as it stops me when I try using nautilus.
[SIZE=3]I have not tried point and click browsing using nautilus on Ubuntu yet so try it before using the command line.[/SIZE]
[SIZE=4]
Optional step 5!
[/SIZE]Using the shell !!! (lots of exclamation points)
ChangeDirectory,Copy, Remove,Move file:
```
cd /mnt/Android_Device
cp /source/file /mnt/Android_device/Destination
rm /mnt/Android_device/Selection
mv /source/file /mnt/Android_device/Destination

```

[SIZE=4]
Step I'm Done![/SIZE]
To unmount try one of the following
```
umount -l /mnt/Android_Device
```

```
sudo fusermount -u /mnt/Android_Device
```




=======================================================================================================================================================
[SIZE=5]This Webpage looks helpful[/SIZE]


Also this web page looks very promising
[http://www.webupd8.org/2012/12/how-to-mount-android-40-ubuntu-go-mtpfs.html](http://www.webupd8.org/2012/12/how-to-mount-android-40-ubuntu-go-mtpfs.html)

It has you add a repository, and then install go-mtpfs
```
sudo add-apt-repository ppa:webupd8team/unstablesudo apt-get update
sudo apt-get install go-mtpfs
```

```
[COLOR=#000000][FONT=UbuntuBeta Mono]sudo apt-get install go-mtpfs-unity[/FONT][/COLOR]
```

The site does list some warnings!

---

### Post by duke.tim on 2013-03-05
There seem to be some bugs with using MTP on Linux. You might want to check into what [COLOR=#000000]dargaud talked about.[/COLOR]

When using this method on my Android device I run into some weird errors, like it will only let me cp or mv one file, and then I have to reset the connection.
Sometimes cp will work but mv will not, and vice versa. (instructions to reset below)

[SIZE=3]Try the [/SIZE][COLOR=#000000]***[This Webpage looks helpful]("http://www.webupd8.org/2012/12/how-to-mount-android-40-ubuntu-go-mtpfs.html") ***Part that I posted.
The program it installs is [/COLOR][COLOR=#000000][FONT=Ubuntu Mono]go-mtpfs[/FONT][/COLOR]

I'm not sure about what to do with the nasty errors you get from Verizon and the locked down memory, It shouldn't be required to root your device since MTP ([s]Microsoft[/s]Media Transport Protocol) works on non-rooted devices on Windows. Usually android devices have a media, sdcard, or storage folder for where the user accessible memory is, not sure of what it is on the Nexus. Change directly to that path and you shouldn't have any problems with the restricted parts of your [COLOR=#000000]Nexus. might be (/mnt/sdcard)?

==============
[/COLOR][COLOR=#000000]==============
Reset
[/COLOR]```
[COLOR=#000000][FONT=Ubuntu Mono]*umount -l /mnt/Android_Device*[/FONT][/COLOR]
```[COLOR=#000000]
[/COLOR]```
[COLOR=#000000][FONT=Ubuntu Mono]*sudo mtpfs -o allow_other /mnt/Android_Device*[/FONT][/COLOR]
```
[COLOR=#000000]
Make sure that the device doesn't lock up
===================
===================


[SIZE=4]Alternate method[/SIZE]
================================================================================================================================================

libmtp has it's own way of accessing the device, it is a bit clunky though.

```
mtp-connect [command] options
```

[/COLOR]Usage: connect <command1> <command2>
Commands: --delete [filename]
--sendfile [source] [destination]
--sendtrack [source] [destination]
--getfile [source] [destination]
--newfolder [foldername]


Alternatively you can look at the list of included file in libmtp
[http://packages.ubuntu.com/quantal/i386/mtp-tools/filelist](http://packages.ubuntu.com/quantal/i386/mtp-tools/filelist)

And use the command
```
mtp-sendfile
usage: sendfile <local filename> <remote filename>
```



When I ran the command it spit out a bunch of errors but copied a file correctly.
> [Internal storage]# mtp-connect --sendfile /test.t /TestFolder/
libmtp version: 1.1.5


Device 0 (VID=0000 and PID=0000) is UNKNOWN.
Please report this VID/PID and the device model to the libmtp development team
PTP_ERROR_IO: failed to open session, trying again after resetting USB interface
LIBMTP libusb: Attempt to reset device
Android device detected, assigning default bug flags
Send file /test.t
Sending /test.t to /TestFolder/
Parent folder could not be found, skipping
Unknown options: /TestFolder/ 




This is the limits of my MTP knowledge, Hope it helps. 
Did you get go-mtpfs to work?

---

### Post by gotnexusbluz on 2013-03-05
> **duke.tim said:**
> There seem to be some bugs with using MTP on Linux. You might want to check into what [COLOR=#000000]dargaud talked about.[/COLOR]

When using this method on my Android device I run into some weird errors, like it will only let me cp or mv one file, and then I have to reset the connection.
Sometimes cp will work but mv will not, and vice versa. (instructions to reset below)

[SIZE=3]Try the [/SIZE][COLOR=#000000]***[This Webpage looks helpful]("http://www.webupd8.org/2012/12/how-to-mount-android-40-ubuntu-go-mtpfs.html") ***Part that I posted.
The program it installs is [/COLOR][COLOR=#000000][FONT=Ubuntu Mono]go-mtpfs[/FONT][/COLOR]

I'm not sure about what to do with the nasty errors you get from Verizon and the locked down memory, It shouldn't be required to root your device since MTP ([s]Microsoft[/s]Media Transport Protocol) works on non-rooted devices on Windows. Usually android devices have a media, sdcard, or storage folder for where the user accessible memory is, not sure of what it is on the Nexus. Change directly to that path and you shouldn't have any problems with the restricted parts of your [COLOR=#000000]Nexus. might be (/mnt/sdcard)?

==============
[/COLOR][COLOR=#000000]==============
Reset
[/COLOR]```
[COLOR=#000000][FONT=Ubuntu Mono]*umount -l /mnt/Android_Device*[/FONT][/COLOR]
```[COLOR=#000000]
[/COLOR]```
[COLOR=#000000][FONT=Ubuntu Mono]*sudo mtpfs -o allow_other /mnt/Android_Device*[/FONT][/COLOR]
```
[COLOR=#000000]
Make sure that the device doesn't lock up
===================
===================


[SIZE=4]Alternate method[/SIZE]
================================================================================================================================================

libmtp has it's own way of accessing the device, it is a bit clunky though.

```
mtp-connect [command] options
```

[/COLOR]Usage: connect <command1> <command2>
Commands: --delete [filename]
--sendfile [source] [destination]
--sendtrack [source] [destination]
--getfile [source] [destination]
--newfolder [foldername]


Alternatively you can look at the list of included file in libmtp
[http://packages.ubuntu.com/quantal/i386/mtp-tools/filelist](http://packages.ubuntu.com/quantal/i386/mtp-tools/filelist)

And use the command
```
mtp-sendfile
usage: sendfile <local filename> <remote filename>
```



When I ran the command it spit out a bunch of errors but copied a file correctly.


This is the limits of my MTP knowledge, Hope it helps. 
Did you get go-mtpfs to work?

For these mtp-sendfile and go-mtpfs, I'm getting the error
[SIZE=3]Unable to open ~/.mtpz-data for reading, MTPZ disabled.libmtp version: 1.1.4
[SIZE=2]also
[/SIZE][/SIZE]davepc@MyPC:/mnt/Android_Devices$ ls

[SIZE=3][SIZE=3]l[/SIZE]s: c[/SIZE]annot open directory .: Transport endpoint is not connected

Well, thanks again for trying!

go-mtpfs doesn't seem to be intended for use with anything other than the Ubuntu Unity interface, which Lubuntu doesn't have (nor should any system for a non-tablet device). At this point, I'm more willing to try a wifi file transfer method than to switch to deal with Unity's general awfulness!

---

### Post by gotnexusbluz on 2013-03-05
Update:  I don't know what (other than the creation of a folder called NexusDrive) which hadn't already been done, but it was after running the commands on this page that I now notice what seems to be a good connection (I can at least see my folders and files). 

[http://android.stackexchange.com/questions/30284/connecting-google-nexus-7-to-linux](http://android.stackexchange.com/questions/30284/connecting-google-nexus-7-to-linux)

---

### Post by duke.tim on 2013-03-06
That's actually pretty interesting, mounting the drive to the users home without the **allow_other **option.
I had no luck with using nautilus, but if it is working for you that's Great! Out of curiosity are you able to copy, and delete files?

---

### Post by buddy_t on 2013-03-07
[B]I have this on three machines, with 12.04 and 12.10 and it works great, no messy items at all, Galaxy SIII plugged in it automounts and I have access to internal and external SD Card. I will probably get in trouble for posting the link, sorry in advance.


[http://www.webupd8.org/2013/01/upgrade-to-gvfs-with-mtp-support-in.html](http://www.webupd8.org/2013/01/upgrade-to-gvfs-with-mtp-support-in.html)

Upgrade Gvfs in Ubuntu 12.10 and 12.04 to get Android 4.0 support for devices which don't support USB Mass Storage interface[/B]


**The packages in this PPA may be  unstable. Use the PPA at your own risk! There are instructions on how to  revert the changes at the bottom of the post.**

**1.** **To add the Gvfs (and libmtp) PPA created by the Gvfs MTP backend developer in Ubuntu 12.04 or 12.10, use the following commands:**

sudo add-apt-repository ppa:langdalepl/gvfs-mtp 
sudo apt-get update

**2. Then, launch Software Updater (previously known as Update Manager) and install the available updates**.


**3. **Once everything has been updated successfully,** restart your computer**, **unlock your Android device**, connect it via USB and it should show up in your file manager (tested with Nautilus and Thunar 1.6).

---

### Post by lykeion on 2013-03-07
I'm running Lubuntu and before I had a Nexus S and it worked just fine. But with my new Nexus 4, MTP just didn't work.
From [this thread]("http://code.google.com/p/android/issues/detail?id=32933#c7") I found out about gMTP, and using that [PPA version]("https://launchpad.net/~quadrispro/+archive/backports") of gMTP they reference in that thread, it works just fine. 

Hope it helps.

---

### Post by gotnexusbluz on 2013-03-08
> **duke.tim said:**
> That's actually pretty interesting, mounting the drive to the users home without the **allow_other **option.
I had no luck with using nautilus, but if it is working for you that's Great! Out of curiosity are you able to copy, and delete files?

Wish I understood how any of this works! I went through the first solution posted, and then I tried go-mtpfs, so it's a guess how just pointing mtpfs to the NexusDrive did the trick. It took a few minutes before my Nexus files were displayed, but after that it worded fine.

---

### Post by gimmerealroot on 2013-05-02
Try this:
[http://blog.itsbilal.com/2012/12/connect-an-android-4-0-phonetablet-to-ubuntu-the-reliable-way/](http://blog.itsbilal.com/2012/12/connect-an-android-4-0-phonetablet-to-ubuntu-the-reliable-way/)

---

### Post by shb79 on 2013-09-21
Well for me, the proper solution running on xubuntu 13.04 and using samsung galaxy with MTP on Android 4.0+ is:

1) install "libmtp" if not installed by default.
    sudo apt-get install libmtp9
2) install "gMTP" from Ubuntu Software store.
3) Run gMTP from Start->Mutimedia->gMTP
4) Click Connect...

and that's it!. Hope eveyone make it work now.

---

