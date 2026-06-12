---
title: "Can not write to /dev/sdc, not a directory"
date: 2017-02-12
forum: General Help
---

### Post by chrisjimbo on 2017-02-12
Hi All,  

I am having a problem writing three Debian .iso's to a USB. 

I have attempted   

sudo cp debian-8.7.1-amd64-DVD-1.iso debian-8.7.1-amd64-DVD-2.iso debian-8.7.1-amd64-DVD-3.iso /dev/sdc  

And I get   

cp: target '/dev/sdc' is not a directory  

Debian directs you to unmount the USB, and input the above into the terminal.  

Have attempted on ext4, FAT32, and unallocated.   

I have also tried /dev/sdc1, I get a similar error.  

Am I being thick? Did I miss something?  

Thanks in advance for your help!

---

### Post by yancek on 2017-02-12
You need a mount point (directory) for the usb to copy to as explained in the error message.  Create a mount point, as an example:  sudo mkdir /mnt/sdc1 (you can change the directory name 'sdc1' to whatever you want.  Then mount it:  sudo mount /dev/sdc1 /mnt/sdc1  For that to work, you would need to have the partition 'sdc1' on the USB drive.  If you get an error, you may need to specifiy the filesystem type.

---

### Post by chrisjimbo on 2017-02-12
Thanks for the reply.

That all makes sense, but why do Debian advise to unmount? 

If directory /dev/sdc/ exists in disk utility and gpart, why can't I just copy to it?

---

### Post by lisati on 2017-02-12
It's not really a directory in the same sense as you'd think of a directory in Windows, it's more like a "special file."

Have a look [here]("http://www.tldp.org/LDP/intro-linux/html/sect_03_01.html") for an explanation of some aspects of the file system used in *nix systems.

---

### Post by &amp;KyT$0P# on 2017-02-12
> **chrisjimbo said:**
> I have attempted   

sudo cp debian-8.7.1-amd64-DVD-1.iso debian-8.7.1-amd64-DVD-2.iso debian-8.7.1-amd64-DVD-3.iso /dev/sdc  

And I get   

cp: target '/dev/sdc' is not a directory  

Debian directs you to unmount the USB, and input the above into the terminal.
What directions are you following?

---

### Post by pqwoerituytrueiwoq on 2017-02-12
[FONT=courier new]/dev/sdc[/FONT] is not a directory it is a file, you can copy to it but you need to do so with **a** disk image
for example i needed to do a server install so i did this only cause it does not work from a multiboot usb setup and i don't have cds/dvds lying around
[FONT=courier new]sudo cp Downloads/ubuntu-16.04.1-server-amd64.iso /dev/sdc[/FONT] [COLOR=#ff0000]**MAKE SURE YOU KNOW WHAT DISK /dev/sdc IS BEFORE DOING THIS YOU COULD _WIPE YOUR SYSTEM_**[/COLOR], use [FONT=Courier New]sudo parted -l[/FONT] to find out what is what
you can also use [FONT=courier new]/dev/urandom[/FONT] or [FONT=courier new]/dev/zero[/FONT] as a source to wipe drives (use [FONT=courier new]urandom[/FONT] for mechanical drives (3 times would be secure), [FONT=courier new]zero[/FONT] for flash memory)
[FONT=courier new]/dev/sdc[/FONT] is the drive itself, this holds all the partition info, files, formats info, etc. think about it like your HDD in binary format

---

### Post by Dennis N on 2017-02-12
> If directory /dev/sdc/ exists in disk utility and gpart, why can't I just copy to it?

You can use the **file** command to see what kind of file something is:

```
dmn@Sydney ~ $ file /dev/sda
/dev/sda: block special 

dmn@Sydney ~ $ file /bin
/bin: directory 

```
/dev/sda is a block special file. I found this definition for you: "Block special files or block devices provide buffered access to hardware devices".
and
/bin is a directory.

---

### Post by chrisjimbo on 2017-02-13
The directions on Debian's website, under creating bootable USB. 

I wanted to use all three .Iso's so I do not need a network connection, and I assumed I could copy all three at the same time as the last two contain packages etc.

Their instructions are;

cp image.iso /dev/sdc
sync

Debian state the drive /dev/sdc must be unmounted, which has confused me.

---

### Post by chrisjimbo on 2017-02-13
So I can't copy multiple files with one command?

---

### Post by howefield on 2017-02-13
> **chrisjimbo said:**
> So I can't copy multiple files with one command?

Yes you can, mount the USB first.

---

### Post by chrisjimbo on 2017-02-13
> **howefield said:**
> Yes you can, mount the USB first.

Again, this makes sense, and thank you.

Why do the Debian team ask to ensure the USB is unmounted, if you can't copy to an unmounted drive?

---

### Post by howefield on 2017-02-13
> **chrisjimbo said:**
> Why do the Debian team ask to ensure the USB is unmounted, if you can't copy to an unmounted drive?

Well, you 'd need to share the link to the documentation that you are using so that others can see exactly what it says.

I'd unmount and use /dev/sdc (or whetever the path the device was) if I were creating a bootable USB but if I wanted to copy some files I'd mount it and use /media/$USER/USB/ (or whatever the path to the mount was).

---

### Post by pqwoerituytrueiwoq on 2017-02-13
@[**[COLOR=#990303][B]howefield**[/COLOR][/B]]("https://ubuntuforums.org/member.php?u=186490") that does not make sense 
OP is writing a disk image to the usb if you were to copy multiple files only the last one would be usable, right?
a disk does not need to me mounted when writing to it in this manner, you can leave it mounted but don't edit the content of it while doing this and after you will need to unmount/mount it anyway
moreover looking at Ops command he is using he is trying to put the same disk image on the drive 3 times or is that a 3 part dvd? ok it is a 3 parts disk image totaling 12.3GB
i know what op is doing works with 1 image, i am actually curious if [FONT=courier new]/dev/sdc[/FONT] even exist, if op would show us what the command [FONT=courier new]sudo parted -l[/FONT] gives that would be helpful

---

### Post by howefield on 2017-02-13
> **pqwoerituytrueiwoq said:**
> @[**[COLOR=#990303][B]howefield**[/COLOR][/B]]("https://ubuntuforums.org/member.php?u=186490") that does not make sense

Quite possibly :)

which is why I asked for the specific documentation.

---

### Post by chrisjimbo on 2017-02-13
> **howefield said:**
> Quite possibly :)

which is why I asked for the specific documentation.

Hi again,

Link to document;

[https://www.debian.org/releases/jessie/amd64/ch04s03.html.en](https://www.debian.org/releases/jessie/amd64/ch04s03.html.en)

Quote from document;

The CD or DVD image you choose should be written directly to the USB stick, overwriting its current contents. For example, when using an existing GNU/Linux system, the CD or DVD image file can be written to a USB stick as follows, after having made sure that the stick is unmounted:

 I should have mentioned, I am trying to create bootable USB with all three iso's.

They are available from Debian as dvd1 etc.

Thanks again &#128512;

---

### Post by yancek on 2017-02-13
There are a number of posts at the Debian forums dealing with the  command above but none involving putting 3 iso files on a flash drive  and having all them be bootable.  This method is similar to using the dd  or cat commands and is meant to be used with with one iso.      Copying to /dev/sdc as explained in the link you posted, I would expect it will have the second iso overwriting the first and the third overwriting the second.  If you want three separate bootable  Debian iso files on the same flash drive you would need to first create a partition and then install Grub2  to the MBR of the flash drive and manually create a grub.cfg file with  proper menuentries.  Then simply copying each iso to that or another partition on the  flash drive would enable you to boot them.  You can put as many iso files on the drive as you have room for and boot them all in this manner.  

The link below to the Ubuntu documentation on booting iso files has some example entries:

[https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)

---

