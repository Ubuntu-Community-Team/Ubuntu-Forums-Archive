---
title: "how can i can create image disk using single command ?"
date: 2022-08-13
forum: General Help
---

### Post by chat-4432 on 2022-08-13
i need to create image disk 
and then restore this using pi imager
 any guide ?
how should i do this ??

---

### Post by TheFu on 2022-08-13
Forget "pi imager".  Any tool that does byte-for-byte copies can be used.  The more complex the tool, the more complicated the setup.
Also, most images aren't created using 1 command, but if you like, you can call hitting <enter> once, "one command".

Because a raspberry Pi doesn't have a BIOS, you'll need to mandate some specific things if you expect this to work on different Pi versions (Pi 2, 3, 4) or even the same version, but different hardware (Pi v3 A and Pi v3 B).

I happened to just install 22.04.1 today onto a Pi v2 because someone was having issues.  To create an image, just do the same steps, in the opposite order (compress rather than decompress), stuff like that.

Also, I don't know how to make this work for both microSD and USB storage, sorry.

Creating an image of the entire OS is easy.  
Step 1: Power off the r-pi and remove the microSD with the OS setup as you like it (this is critical). We cannot easily image a running OS without risk of corruption.  
Step 2: Take that microSD card and connect it somehow to another Unix-like OS. Basically, anything that isn't MS-Windows, but still a desktop or server OS.  It can even be another raspberry Pi.
Step 3: Determine the device name for the microSD card with the OS you want to clone.  On Ubuntu, I'd run 'dmesg -w' before inserting the microSD into the system and the messages that show up in that log will have something like 
```
[779895.274902] sd 16:0:0:0: [sdc] 62521344 512-byte logical blocks: (32.0 GB/29.8 GiB)
[779895.276445] sd 16:0:0:0: [sdc] Write Protect is off
[779895.276448] sd 16:0:0:0: [sdc] Mode Sense: 21 00 00 00
[779895.278441] sd 16:0:0:0: [sdc] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[779895.309238]  sdc: sdc1 sdc2 sdc3
[779895.342324] sd 16:0:0:0: [sdc] Attached SCSI removable disk
```
The important lines are 'sdc', so the device file for the entire storage, which has 3 partitions is /dev/sdc
Step 4: Copy 'sdc' to a file (somewhere the size of the entire microSD card), using byte-for-byte copy.  That can be dd, ddrescue, cat, cp, more, or any other Unix tool that won't molest the bytes. We are cloning the entire device, so empty space is being cloned too, even if it isn't allocated.  May want to use just 4G or 8G microSD cards for the OS, to keep the image manageable.   Example commands are:
```
$ sudo cp /dev/sdc /some/where/with/enough/space/my-OS-v0.001.img
```
or 
```
$ sudo ddrescue  /dev/sdc /some/where/with/enough/space/my-OS-v0.001.img  /tmp/log
```
or
```
$ sudo dd   if=/dev/sdc of=/some/where/with/enough/space/my-OS-v0.001.img bs=4M
```
But there are lots and lots of options.  Do not use mv.
Step 5: Because the microSD probably wasn't fully used, so the img file is also probably full of unused space, compressing the file is a good idea.  To make the compression even better, it would be smart, before starting to even install the OS on the SOURCE microSD BEFORE any steps, to write the entire drive with zeros. Those compress really well.  Remember, this is a bit-for-bit copy of all space on the storage device, even unused, unallocated, whatever, so any non-consistent unused storage will make compression less great.  Anyway, there are lots of compressors.  gzip, compress, bzip, xz, arj and a bunch more.  Today, I saw that Ubuntu was using xz, which I don't really use much, so I had to look up the uncompress command, unxz.  Lacking any critical reason to pick something else, I'd use gzip.
```
$ sudo gzip /some/where/with/enough/space/my-OS-v0.001.img 
```  The resulting file will be  /some/where/with/enough/space/my-OS-v0.001.img.gz
That should get at least 50% compression, which is probably good enough.
Step 6: Create a sha256sum file for the compressed image, so people can validate they got the download correctly.

So, if you put all those steps into a script, then you can have 1 command with 1 <enter>.  Figuring out the device name is likely the hardest part of those steps to script.  If you want a bulletproof tool, that means lots of error checking and available storage validation, whereas for a personal use script, I wouldn't bother. Humans can make those decisions trivially, so there is little to be gained by adding them to a script, IMHO, especially when a 10 line script would likely balloon to a 30-50 line script to protect against stupid users.  What do they say?  "No matter how much idiot proofing there is, Dog will make a bitter idiot to break the code."

Plus, in scripting a little tool like this, you'll really learn how each step really works. We cannot program something, without knowing how to do it.  Same as teaching, I suppose. We cannot teach a subject without a good understanding of that subject.

Steps 4 and 5 can be merged into a pipeline pretty easily - to drastically reduce the amount of available storage needed in the target file system.  You can probably make a % completed output for these steps too, but inserting 'pv' in the middle of the imaging and compression pipes. People seem to like that. Just need to get the size of the input storage as an option to the pv command. That's not hard. Use 'stat'.  See how a little 2 command script becomes larger and larger as more things to make humans happier are added?

This method of scripting is why Unix-like OSes are so very powerful. We have all these tiny tools, which are designed to be used together, in a pipeline, to create a specific outcome.  This is very different from MS-Windows. They have very different core philosophies.  The real power comes by making these things automated so they happen over night or when we are away for something else and not waiting for the final result.  Scheduling something like this to happen, perhaps once a week, wouldn't hard, provided we remember to pull the microSD card out and leave it connected to a different system where the script runs automatically.

If you are doing this for backups, I'd say this is the hard way, though at least a r-pi OS image won't be more than 8G of storage, so it isn't THAT bad.  OTOH, my file-based backups easily hold 90 days of daily backups in 1.3x the original storage that is backed up. I actually don't backup the OS at all. There's no need. I do backup the OS and personal settings, lists of installed packages, and OS and personal data.  Typically, that saves 8-20G of data that doesn't need to be included in backups.

But people like to have images and images do have a place too, even if they aren't very flexible.

Anyway, hope this is helpful.

---

### Post by HermanAB on 2022-08-14
In general, something like this is all you need to make an image, and restoring it is simply the reverse:
$ sudo cat /dev/sda > /dev/sdd

Where sdd or whatever is the device name of the destination removable media, which you can see with dmesg.

For this to work on a regular system, you need to have booted off install media. You cannot do it while running the regular system, since then the disks are mounted and in use.

As for a Rpi, if it is running off a SD Card, simply copy the card on another system.

---

### Post by TheFu on 2022-08-14
> **HermanAB said:**
> $ sudo cat /dev/sda > /dev/sdd
 

Will that work?  The redirection will be running under the normal userid, so I suspect 
```
$ sudo cat /dev/sda | sudo tee  /dev/sdd
```
is the command needed, but I haven't tried it.  cp is easier to me.  Only the root account and write directly to disk device files, right?

And the typical warning about ensuring that "sdd" is the correct output device to be overwritten applies.  If that is the wrong device, it will be a very, very, bad day, with massive data loss.

---

