---
title: "Help. Grub 2 from 14.04 replaced with grub 1.99 from 12.04"
date: 2014-07-15
forum: General Help
---

### Post by RedRat on 2014-07-15
OK, I screwed up. I had a dual boot going between 12.04 and 14.04 on my machine. Yesterday I was in 12.04 and made the mistake of using Synaptic to upgrade all installed programs. When I went to reboot instead of getting my very familiar grub 2 with the option of starting 14.04 (default) and 12.04, I got a very unfamiliar grub 1.99 and only could get 12.04. Stranger still, in the lower right corner is the Debian logo, which I have never seen before. 

How do I get back to my Grub 2 and the ability to have the choice between 12.04 and 14.04??? I can still see my 14.04 "partition" so it has not been wiped out. Is there a backup to Grub when this kind of thing happens?

***I think I have resolved this issue. Please look at my last post in this section.*****

---

### Post by yancek on 2014-07-15
Boot Ubuntu 12.04, open a terminal and run:  sudo update-grub.  Watch the output.  Your 14.04 should be detected and an entry created in the boot menu.  Reboot to verify.  If 14.04 boots, boot into it and install grub from 14.04 to the master boot record.  You haven't indicated if you have any other operating systems other than 12.04 and 14.04 installed nor the number of drives/partitions you have?  If you only have one drive then from 14.04, running:  sudo grub-install /dev/sda should put the 14.04 boot code in the mbr.  If you have multiple drives or other OSs you should post the output of:  sudo fdisk -l(Lower Case Letter L in the command) to get specific advice.  Also, since 12.04 is going to be supported for some time, you could just leave its Grub on the mbr if you are able to boot 14.04 from it.

---

### Post by RedRat on 2014-07-15
> **yancek said:**
> Boot Ubuntu 12.04, open a terminal and run:  sudo update-grub.  Watch the output.  Your 14.04 should be detected and an entry created in the boot menu.  Reboot to verify.  If 14.04 boots, boot into it and install grub from 14.04 to the master boot record.  You haven't indicated if you have any other operating systems other than 12.04 and 14.04 installed nor the number of drives/partitions you have?  If you only have one drive then from 14.04, running:  sudo grub-install /dev/sda should put the 14.04 boot code in the mbr.  If you have multiple drives or other OSs you should post the output of:  sudo fdisk -l(Lower Case Letter L in the command) to get specific advice.  Also, since 12.04 is going to be supported for some time, you could just leave its Grub on the mbr if you are able to boot 14.04 from it.

OK, When I installed 12.04, I wiped a Windows installation out. This is an HP Pavilion that came with Windows. When I added 14.04, I noted that there was a 5Gb partition hidden, I assume it is either there from the original Windows installation or from my 12.04 installation. Either way, there are three partitions: A 12.04 partition of roughly 300GB, a hidden 5Gb, and my newer 14.04 178Gb partition. I only want 12.04 and 14.04 and no other OS. These are the only ones I use. 

I just ran the fdisk command and this is what I get:

> Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00060cb8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   622178654   311088303+  83  Linux
/dev/sda2       622180350   976771071   177295361    5  Extended
/dev/sda5       969961472   976771071     3404800   82  Linux swap / Solaris
/dev/sda6       622180352   969961471   173890560   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xbc08dd54

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63  2930272064  1465136001    7  HPFS/NTFS/exFAT


---

### Post by RedRat on 2014-07-15
> **yancek said:**
> Boot Ubuntu 12.04, open a terminal and run:  sudo update-grub.  Watch the output.  Your 14.04 should be detected and an entry created in the boot menu.  Reboot to verify.  If 14.04 boots, boot into it and install grub from 14.04 to the master boot record.  You haven't indicated if you have any other operating systems other than 12.04 and 14.04 installed nor the number of drives/partitions you have?  If you only have one drive then from 14.04, running:  sudo grub-install /dev/sda should put the 14.04 boot code in the mbr.  If you have multiple drives or other OSs you should post the output of:  sudo fdisk -l(Lower Case Letter L in the command) to get specific advice.  Also, since 12.04 is going to be supported for some time, you could just leave its Grub on the mbr if you are able to boot 14.04 from it.

Ok, ran update-grub. Yes, at is all streamed by, it did see 14.04 on sd6 but it does not show up in the grub menu when I reboot. It did not create an entry. All that it shows is a whole slew of older kernels prior to the current one.

---

### Post by Bashing-om on 2014-07-15
RedRat; Well, Well,


Excellent advise, let me also do what I can to push this matter along
Certainly a curious turn of events, Let's do what we can to figure out what is going on. The update-grub command should have added 14.04 to the boot menu if you indeed booted from 12.04.
'sda1' is marked as the booting partition. which OS is installed there ? - do you have your partitions labeled ?
Show us the output of terminal command:
```

sudo blkid

```
Be aware, only one OS can be in control of the booting process, which one do you want to be that master ?
Next let's look at the file permissions on the respective grub config files to make sure there is nothing hindering the making up of the boot menu:
From the liveDVD ( either 12.04 or 14.04 release, does not matter in this instance):
let's mount the respective 'root' partitions on the installs and have a lookseee:
```

sudo mkdir /mnt/work1204
sudo mount /dev/sda1 /mnt/work12.04
ls -la /mnt/work1204/etc/grub.d
sudo umount /mnt/work1204

``` so we know all files are present and the permission on those files, particularly the file '30_os-prober' . As that is the tool that looks up other operating systems.

Now the same same procedure for whatever is installed to 'sda6' - as a current working hypothesis, 14.04:
```

sudo mkdir /mnt/work1404
sudo mount /dev/sda6 /mnt/work14.04
ls -la /mnt/work1404/etc/grub.d
sudo umount /mnt/work1404

```

Once we know what is installed where, we can try and boot to that desired primary Operating System from grub, (RE-)install grub and see that the alternate OS is picked up for grub's boot menu.

My method for fault isolation -> small steps , 1 step at a time ->
[INDENT][INDENT][INDENT]know what we are working with
[/INDENT][/INDENT][/INDENT]

---

### Post by deadflowr on 2014-07-15
Out of curiosity, what was the output of update-grub?

---

### Post by yancek on 2014-07-15
> Ok, ran update-grub. Yes, at is all streamed by, it did see 14.04 on sd6  but it does not show up in the grub menu when I reboot. It did not  create an entry

Stating the obvious here but, when you were at the boot menu, you used the down arrow key to go through the entire menu and still found no entry for 14.04?

---

### Post by oldfred on 2014-07-15
Related to above the "box" that shows the grub boot entries only holds so many entries. If you have a tiny arrow in the lower right corner (very tiny), then you can scroll down for more entries.
If you have that many entires it really is time to houseclean some older kernels out.

Grub remembers where to reinstall on major updates. You can change that setting. And if you do not want it to reinstall uncheck everything.
       #To see what drive grub2 uses see this line   - grub-pc/install_devices:
sudo debconf-show grub-pc
 sudo grub-probe -t device /boot/grub

   #to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc or dpkg-reconfigure grub-efi-amd64
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions
[http://ubuntuforums.org/showthread.php?t=2189643](http://ubuntuforums.org/showthread.php?t=2189643)

Do the dpkg update on 12.04 to get it not to reinstall and set 14.04 as boot in MBR.

You should be able to boot into 14.04 from your 12.04, but it will be the last or bottom entry in menu.
From working system only & if drive is only sda:
       sudo grub-install /dev/sda

            sudo update-grub

---

### Post by RedRat on 2014-07-15
Bashing-om

> sudo blkid

This gave me:
> /dev/sda6: UUID="3ea0680b-d6d9-46c1-a76d-4acc9366c54e" TYPE="ext4" 
/dev/sda1: UUID="2e9aef49-7d23-4275-8400-e333639f55ff" TYPE="ext4" 
/dev/sda5: UUID="fe738500-252a-425b-bedf-7b6bbb718a45" TYPE="swap" 
/dev/sdb1: LABEL="FreeAgent Drive" UUID="F8E09E2BE09DF05C" TYPE="ntfs" 

---

### Post by RedRat on 2014-07-15
> **yancek said:**
> Stating the obvious here but, when you were at the boot menu, you used the down arrow key to go through the entire menu and still found no entry for 14.04?

That is correct, I did not see any entry for 14.04.

---

### Post by RedRat on 2014-07-15
> Related to above the "box" that shows the grub boot entries only holds  so many entries. If you have a tiny arrow in the lower right corner  (very tiny), then you can scroll down for more entries.
If you have that many entires it really is time to houseclean some older kernels out.

I could not agree more! I did not realize that just about every kernel update is retained since I began running 12.04. How do I clean them out? Where are they stored?

Strangely, I got into 14.04 by accident. I scrolled through all the previous kernels in the list then at the very end, I hit the "right arrow" which took me into another very different screen. It allowed me to get into sda6 in "recovery mode" so the graphics were off a bit, i.e., something less than my normal 1900x1200 mode.

---

### Post by RedRat on 2014-07-15
I think I may well have solved this, all by accident. I went down the list immediately after the first kernel and selected one about 2 removed from the top kernel shown in grub. I made sure that it was not a "recovery mode" and used the right arrow. This got me into a boot for Ubuntu and it turned out to be 14.04. There was no identification of the version or disk position, i.e., sda6. It booted into 14.04 with correct graphics. 

When I was in 14.04, I went to Synaptic and then reinstalled all the grub entries, especially the one for the 2 version beta. They appeared to be reinstalled without incident. Then I re-booted and Grub2 came up as it did before! So far all is well. Grub2 looked as it did before my mistake and also has an entry for the old 12.04. Whew. 

I hearby resolve NOT to use Synaptic to update my software again!!! Especially while in 12.04.

---

### Post by Bashing-om on 2014-07-15
RedRat; Great !

synaptic is a great tool when used properly. However, once I learned to use 'apt-get', dpkg, and aptitude directly I no longer use synaptic ( in line with my KISS attitude ).

It is a prime importance to remove those old no-longer-needed kernels; either from the command line or with synaptic (complete removal of images and headers) will get the job done. If you require guidance, please open a new thread and we will be there.

[INDENT][INDENT]happy trials to you
[/INDENT][/INDENT]

---

### Post by RedRat on 2014-07-15
Bashing-om
OK started a new thread. Thanks for the help. I would like to know how to rid my self of those older kernels. I would like to retain perhaps two for 12.04 and a few for 14.04. Let me know how to do this with Synaptic.

---

### Post by Bashing-om on 2014-07-15
RedRat; Sure .

I will hunt you up in the new thread.

[INDENT][INDENT]ain't no step for a stepper
[/INDENT][/INDENT]

---

