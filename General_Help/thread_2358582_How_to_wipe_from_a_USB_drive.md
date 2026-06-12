---
title: "How to wipe from a USB drive"
date: 2017-04-14
forum: General Help
---

### Post by allenpcarlson on 2017-04-14
I'm completely new to Ubuntu and I want to wipe a few drives using a bootable USB with Ubuntu. I've looked at several videos and done what I could googling, but the command lines I write in the terminal aren't working. So I either need to use 
shred, 
sudo shred, 
something with -vz, 
I need to put in /dev/sdc1 somewhere
dd if=/dev/sdX bs=512
dd if=/dev/urandom of=/dev/sda bs=1M

The last two seem to be my best bet... I think... it tells me it doesn't know which drive it's supposed to be deleting. I want it to delete my C:. If anyone wants to tell me what specific command line I should write in to wipe my C: with 0's, that's all I really need. On a side note, I'm kinda liking this Ubuntu thing. It runs very quickly. I might just switch over. In any event thanks guys!

---

### Post by yetimon_64 on 2017-04-15
> **allenpcarlson said:**
> I'm completely new to Ubuntu and I want to **wipe a few drives** using a bootable USB with Ubuntu. I've looked at several videos and done what I could googling, but the command lines I write in the terminal aren't working. So I either need to use 
shred, 
sudo shred, 
something with -vz, 
I need to put in /dev/sdc1 somewhere
dd if=/dev/sdX bs=512
dd if=/dev/urandom of=/dev/sda bs=1M

The last two seem to be my best bet... I think... it tells me it doesn't know which drive it's supposed to be deleting. **I want it to delete my C:**. If anyone wants to tell me what specific command line I should write in to wipe my C: with 0's, that's all I really need. On a side note, I'm kinda liking this Ubuntu thing. It runs very quickly. I might just switch over. In any event thanks guys!
To accurately identify the drives use the following command in a terminal ...
```
sudo parted -l
``` It will show you the device description in the header of each drive eg. /dev/sda etc and the partition numbers down the left hand side of the partition details.

It will depend on the level of security you need with respect to "wiping" a drive as to what I would recommend. If you need high data security protection I'd use something like secure delete or hdparm. 

If you are only "cleaning off" old used drives in a maintenance sense, with no need for high data security but to reuse the drive from a clean start, I'd look at using shred; **be extremely careful with using dd** as the input file (if) and output file (of) settings are very easy to confuse/mix-up with disastrous results if the wrong partition descriptor (/dev/sdX) is used. Think how you would react if [s] your root or home or even[/s] your media storage partition/s are accidentally wiped with absolutely NO chance of file recovery when overwritten with such tools. **edit: **just noted you are running from a live boot, you won't likely have a root or home partition to worry about but you may have windows data partitions with files/media in that this could apply to.

I do not generally use such tools for secure deletion but for maintenance/cleanup usage and when I do such preparatory work I do use the shred command as follows...

[U][I]**To reset a complete drive (as per the first bolded bit of your post above)...**
[/I][/U]
```
sudo shred -fvzn0 /dev/sd**X** 
``` where /dev/sdX is the drive to be prepared/cleaned out.
**Note the code above will wipe all of the drive including****[B] the boot sector**[/B]**[B],** and the EFI system partition as well[/B] on more modern hardware, **if you accidently use it on /dev/sda**, requiring the re-installation of the boot sector and the efi partition of the drive.  

An explanation for the switches in use in the command above ...
```
f = force
v = verbose
z = zero   # performs a single pass of zeros written to the drive sometimes referred to as a "factory reset".
n0 = 0 iterations   # which means do not do any passes using random data. This is very low data security but speeds up the resetting process drastically. Increase this value for higher data security protection if needed. If this value is NOT set then shred by default will do 3 passes of random data (very slow for the command to complete its run).

```
 
Please let us know how important data security is in the case of your windows data.

_ **To reset an individual partition *(as per the second bolded bit of your post above) ...***_
To reset individual partitions only, as your opening post suggests you need to do with "C:/ drive", use the device file for the specific partition eg. /dev/sdX# where # is the partition number (1,2,3 etc ).

The command would be (for a simple partition reset, NOT for data recovery protection) ...
```
sudo shred -fvzn0 /dev/sd**X#** 
``` where **X#** is the specific partition letter/number of the windows "C:/ drive" (eg. /dev/sd**a2**). 
Use the first code box above to find the windows partition details specifically, post the output of that command here IF you need help to specifically identify the windows partition in code tags please (see the red link on the right of my post signature below for how to use code tags). This can be adjusted for any specific partition as needed.

One final note, if you only want to delete C:/ and reformat the partition for ubuntu/linux use without the need for wiping data; a GUI tool called "Gparted" can do so easily. You can just right click on the windows partition and delete it then right click the cleared partition and choose to reformat it very easily then reuse it as a data partition or whatever else it is needed for. The terminal tools above are generally used where sensitive data may need to be permanently and unrecoverably erased. Gparted is installed by default in the ubuntu live dvd/usb image, but has to be installed from the repositories if needed in a final installation. The next code will install it if it suits your data needs ...
```
sudo apt-get install gparted
```**Edit: **not needed from a usb live boot.

Regards, yeti.

---

### Post by C.S.Cameron on 2017-04-15
To set your C drive to zeros using Terminal run:
```
dd if=/dev/zero of=/dev/sda
```
While booted from a Live Ubuntu flash drive.
This can take a long time.
If you prefer a GUI try mkusb:
[https://help.ubuntu.com/community/mkusb/wipe](https://help.ubuntu.com/community/mkusb/wipe)

---

### Post by gordintoronto on 2017-04-15
To securely wipe a hard drive, most people use DBAN. Make sure the only hard drive which is connected, is one you want to wipe.

---

### Post by yetimon_64 on 2017-04-15
> **C.S.Cameron said:**
> To set your C drive to zeros using Terminal run:
```
dd if=/dev/zero of=/dev/**sda**
```
While booted from a Live Ubuntu flash drive.
This can take a long time.
If you prefer a GUI try mkusb:
[https://help.ubuntu.com/community/mkusb/wipe](https://help.ubuntu.com/community/mkusb/wipe)
As is above that will not work as it requires sudo usage. If sudo is used with it the OP will also lose the boot records of the drive and the EFI partition if one is present, not just the windows partition.

@ OP, be aware dd is often referred to as "data destroyer" or in this case could also be nicknamed "disk destroyer". I would advise extreme care with that command as it is currently given. 

I will add a "+1" to the use of mksub as it is a wrapper to the dd command and such is regarded as a much safer option to using dd by itself.

---

### Post by allenpcarlson on 2017-04-17
> **C.S.Cameron said:**
> To set your C drive to zeros using Terminal run:
```
dd if=/dev/zero of=/dev/sda
```
While booted from a Live Ubuntu flash drive.
This can take a long time.
If you prefer a GUI try mkusb:
[https://help.ubuntu.com/community/mkusb/wipe](https://help.ubuntu.com/community/mkusb/wipe)

I'll give the GUI a try. I tried your command and it told me I didn't have permission to do that...


BTW, after I wipe the hard drive, I can reinstall Windows/Ubuntu, correct?

---

### Post by C.S.Cameron on 2017-04-17
Command needs to be run as root in Ubuntu:

[HTML]sudo dd if=/dev/zero of=/dev/sda[/HTML]

---

### Post by raleigh3 on 2017-04-17
I wonder if formatting to 2 different file system would work ?

---

