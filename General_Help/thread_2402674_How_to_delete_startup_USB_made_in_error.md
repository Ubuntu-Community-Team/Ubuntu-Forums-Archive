---
title: "How to delete startup USB made in error?"
date: 2018-10-03
forum: General Help
---

### Post by Richard_York on 2018-10-03
I intend to install Ubuntu 18.04 LTS on a new to me/2nd hand desktop machine.  I accidentally downloaded the Server image rather than the desktop image - please be kind to me, I'm doing this with a foul cold and not concentrating well! - and got as far as making a start up USB with Startup Disk Creator before I realised my mistake.
Having downloaded the proper desktop image on the old 32-bit desktop machine, running 14.04, I thought to use the same USB stick, deleting the wrong data in the process. When I try this, I get this message: 
<starts>
org.freedesktop.DBus.Python.gi._glib.GError: Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/dbus/service.py", line 707, in _message_cb
    retval = candidate_method(self, *args, **keywords)
  File "/usr/share/usb-creator/usb-creator-helper", line 237, in Format
    part.call_set_type_sync('0x0c', no_options, None)
gi._glib.GError: GDBus.Error:org.freedesktop.UDisks2.Error.Failed: Error setting partition flags on /dev/sdc2: Command-line `sfdisk --change-id "/dev/sdc" 2 0x0c' exited with non-zero exit status 1: 
WARNING: GPT (GUID Partition Table) detected on '/dev/sdc'! The util sfdisk doesn't support GPT. Use GNU Parted.

Use the --force flag to overrule this check.  
<ends>
I can use a fresh USB stick to make my startup disc but hate wasting the other one - how can I clear and if need be, re-format the whole thing, please?
Thanks for any help, preferably in slow and patient explanations!

---

### Post by westie457 on 2018-10-03
Take a look at this. [https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

---

### Post by again? on 2018-10-03
I've had the best success just using the dd command.
First vid gives a GUI method using etcher.
The second video in this playlist explains how to use dd. (turn on subtitles as he has a strong accent).
The third video shows how to use commands to restore a usb if dd is not working.
[https://www.youtube.com/playlist?list=PLSmXPSsgkZLvWbJ9XwZn-PohZxLhZcQOv](https://www.youtube.com/playlist?list=PLSmXPSsgkZLvWbJ9XwZn-PohZxLhZcQOv)

---

### Post by Richard_York on 2018-10-03
Thanks for these. The most immediately relevant and which I thought I could understand seems to be the second video, on how to restore a usb stick.

 As on his video, my stick is identified as /dev/sdb on my machine (I'm working on a ancient Toshiba laptop with Xubuntu 16 on for this, as it's 64bit) 
I've copied what I get. I don't know why it's identified as busy - I only plugged it in so the machine could delete it, and haven't opened it up at all.
 
I'm usually OK at following instructions I don't understand as long as they're in simple steps, but have no concept of what to do when things happen differently! It's quite possible that feeling grotty, as mentioned earlier means I'm simply not spotting something obvious, too.

Disk /dev/sdb: 7.2 GiB, 7746879488 bytes, 15130624 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x5072b7db

Device     Boot   Start     End Sectors  Size Id Type
/dev/sdb1  *          0 1662975 1662976  812M  0 Empty
/dev/sdb2       1590408 1595079    4672  2.3M ef EFI (FAT-12/16/32)
richard@richard-Satellite-Pro-A300:~$ sudo wipefs --all /dev/sdb
wipefs: error: /dev/sdb: probing initialisation failed: Device or resource busy
richard@richard-Satellite-Pro-A300:~$ ^C



Thank you for any clarification and advice.

---

### Post by again? on 2018-10-03
I keep reference notes and I have used the method in the video.

These are my notes from the video which may help.
_Restore your USB flash drive_
Unmount (no sudo) drive before running wipefs:
```
umount /dev/sdx#
```
where /dev/sdX# is your flash drive **partition**. (eg /dev/sdd1)

Clean your flash drive:
```
sudo wipefs --all /dev/sdX
```

Create a new partition:
```
sudo cfdisk /dev/sdX
```
&#8227; select dos
&#8227; select new partition 
&#8227; Press Enter when size shown
&#8227; Select Primary
&#8227; Select Bootable which marks *Boot
&#8227; Select write and type "yes" to confirm
&#8227; Select Quit to finish

And format this partition as FAT file system:
```
sudo mkfs.vfat -n 'yourlabel' /dev/sdX1
```

..and my notes for writing with dd
_Write ISO to your USB flash drive:_

```
sudo dd bs=4M if=/path/to/iso of=/dev/sdX status=progress && sync
```
Replace /dev/sdX with your device name.

To find out the device name:
```
sudo fdisk -l
```

---

### Post by Richard_York on 2018-10-03
Thank you again, this should really help. To show how basic my ignorance is... how do I identify my flash drive partition. (eg /dev/sdd1)?   I've got as far as realising the drive is sdb2, but that's the limit of my knowledge here.

---

### Post by sudodus on 2018-10-03
> **westie457 said:**
> Take a look at this. [https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

You can use a cloning tool, which will simply overwrite whatever is on the USB flash drive. You can use **mkusb** as suggested by westie457, and you can use the Ubuntu **Startup Disk Creator** (of Ubuntu 16.04 LTS and newer versions, but the version in 14.04 LTS is buggy). So clone from the Ubuntu desktop iso file, and you'll get what you want :-)

mkusb and the Startup Disk Creator will help you identify the target drive (the flash drive).

[hr][/hr]
You can also use dd, but it is more risky because there is no final checkpoint (where you can double-check that everything is correct), and if you have bad luck and make a minor mistake, you might overwrite another drive, where you store valuable data.

---

### Post by C.S.Cameron on 2018-10-03
I usually use mkusb for USB work as Sudodus suggests.
If I am in a hurry to restore a device, I use "Disks" to unmount the device and then gparted to create a new partition table and format.

---

### Post by Richard_York on 2018-10-04
Thanks - please forgive a pause, the bugs (my health, not computer) are wrecking brain function. I'll come back to this soon.

---

### Post by Richard_York on 2018-10-06
Re-emerging into the land of the living after the worst of my bug, but no cleverer than I was before.... 

I am working here using an ancient laptop with Xubuntu 17 - I don't think it's up to running 18 - on the grounds that it contains no vital information and if I do the wrong thing and wreck it, it's no great loss compared with messing up the family desktop machines, either the current outdated one or the newer one which will be running Ubuntu 18 soon, I hope. 
I've still got this USB pendrive where I wrongly installed Ubuntu 18 Server version, not Desktop. 

 I installed GParted onto Xubuntu  and under "Device" menu asked it to create a new partition table on the USB, as suggested on [https://wiki.ubuntu.com/Win32DiskImager/iso2usb/FormatHelp](https://wiki.ubuntu.com/Win32DiskImager/iso2usb/FormatHelp), from the link given earlier in this thread.

The top panel there now reads "unallocated  7.21 GiB" and "Device Information " down the side lists Partition Table as msdos, Heads 255, sectors/track 63, Cylinders 941, total sectors 15130624, sector size 512.
I've read through the instructions on[SIZE=2]  "Restore the pendrive to a storage device with mkusb or mkusb-nox" but my two problems are i) it's beyond my comprehension and ii) my software updater does not find mkusb or mkusb-nox as available. I tried the risky move of copying some of the suggested lines into the terminal to install it, but it comes back "unable to locate package mkusb" or "mkusb-nox"
So I'm stuck on that one.

Tried Guber2's method, where I'm grateful for steps being so helpfully laid out. This worked until I got to a screen where the options differed from the list shown on the instructions, and I was about to copy what I got when....

Meanwhile I'd mentioned this to another friend who suggested [https://www.wikihow.com/Format-a-USB-Flash-Drive-in-Ubuntu](https://www.wikihow.com/Format-a-USB-Flash-Drive-in-Ubuntu) where method 2 worked up to a point - it's apparently formatted, but as "read only" so I can't yet write to it.  

That's currently as far as I've got.

[/SIZE]

---

### Post by The Cog on 2018-10-06
Late to the party, but..
Are you trying to restore the drive to being a normal usable pen drive e.g. for putting photos on, or are you trying to turn it into an Ubuntu installer stick?

---

### Post by sudodus on 2018-10-06
> I've read through the instructions on "Restore the pendrive to a storage device with mkusb or mkusb-nox" but my two problems are i) it's beyond my comprehension and ii) my software updater does not find mkusb or mkusb-nox as available. I tried the risky move of copying some of the suggested lines into the terminal to install it, but it comes back "unable to locate package mkusb" or "mkusb-nox"

If you run standard Ubuntu live, you need an extra instruction to get the repository Universe. (Kubuntu, Lubuntu ... Xubuntu have the repository Universe activated automatically.)

```
sudo add-apt-repository universe  # only for standard Ubuntu
```

Otherwise it is enough with the following command lines to install mkusb. You need a PPA in order to install mkusb:

```
sudo add-apt-repository ppa:mkusb/ppa  # and press Enter
sudo apt-get update
sudo apt-get install mkusb mkusb-nox usb-pack-efi
```

I think it is easiest to copy and paste the command lines from here to a terminal window and press the Enter key to run the commands.

---

### Post by Richard_York on 2018-10-06
Hi, just trying to restore the stick for use as normal storage. I had another stick handy which I have made into an installer stick. When we get a new graphics card in the desktop machine I'll see how well that works :-)
And re-reading my original post, with apologies, the bug was obviously winning and I didn't make it clear enough then that my aim is not to create a bootable drive on the problem stick, just restore it to use as general storage. 
Serves me right for trying to work under the influence of bugs. I'm sorry if I've had you working on a false premise.
But I've made definite progress using these instructions!

---

### Post by oldos2er on 2018-10-06
> I am working here using an ancient laptop with Xubuntu 17 Neither 17.04 nor 17.10 is supported anymore. If you don't intend to give the computer 'net access this shouldn't be a problem, but I would use a supported version if you're going to use it for internet--the risks are too great otherwise.

For a lighter desktop environment try [Lubuntu]("https://lubuntu.me/downloads/").

---

### Post by Richard_York on 2018-10-06
THat's probably very good advice. Thanks! I'm hanging on with it until I've got the desktop machine working, then will try upgrading this machine, or switching to Lubuntu. I should probably pose the question of whether this one, listing what it's got, would be up to handling Xubuntu 18, on a separate thread, so I'll not go there just now.
Back to the USB stick....

---

### Post by Richard_York on 2018-10-06
Thanks to all - solved!! I followed Sudodus' latest advice to get mkusb, and it worked a treat. 
Truly a helpful forum, and much appreciated.

---

