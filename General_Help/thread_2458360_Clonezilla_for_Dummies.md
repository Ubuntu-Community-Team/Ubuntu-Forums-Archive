---
title: "Clonezilla for Dummies?"
date: 2021-02-22
forum: General Help
---

### Post by robert99999 on 2021-02-22
I've read that Clonezilla is the easiest application for cloning a hard drive. So, I went to their website, and tried to download it. I was met with a barrage of technobabble questions that I was required to answer in order to get the correct version of the software. I couldn't answer them, because I don't have a Phd in hardware and software design. Apparently, there are a thousand different versions of Clonezilla available, and the one that's appropriate for my computer can only be determined if I know every part number of every chip on my computer's mother board.

Example: menu choice of computer processors: AMD64, i686-pae, or i686. I'm pretty sure that it's not an AMD64 because my computer has an "Intel Inside" sticker. And I do know that it's 64-bit. But that's the limit of what I know about the processor.

Surely, there's got to be an easier way to clone a hard drive than having to wade through all of this mess of stupid questions.

---

### Post by tea for one on 2021-02-22
I would think that this iso is a good choice:-

[https://osdn.net/frs/redir.php?m=ymu&f=clonezilla%2F74520%2Fclonezilla-live-20210127-groovy-amd64.iso](https://osdn.net/frs/redir.php?m=ymu&f=clonezilla%2F74520%2Fclonezilla-live-20210127-groovy-amd64.iso)

If you haven't used Clonezilla before, please read the guides carefully

[https://clonezilla.org/clonezilla-live.php](https://clonezilla.org/clonezilla-live.php)

---

### Post by dbergst on 2021-02-22
If your computer is a 64-bit Intel, that qualifies as an AMD64 class machine.

---

### Post by robert99999 on 2021-02-22
Thanks for the replies.

Maybe I should take a step back and explain what I'm trying to do. I want to replace my internal HD with an SSD. So, I just need to copy the internal HD to the new SSD. I have the new SSD temporarily installed in an external drive box with USB interface.

From what I read on this forum, Clonezilla was recommended as being safer to use than dd. However, after reading some of the instructions on the Clonezilla site, I see a lot of warnings about how it can easily overwrite the wrong disk if everything isn't done exactly right. Given the rather disorganized nature of that site and its confusing instructions, I don't think I can trust Clonezilla now. Maybe I should just use dd and take my chances. Is it really any more dangerous than Clonezilla? After all, any disk copy program can overwrite the wrong disk if used incorrectly.

If I do decide to use Clonezilla, with the iso file that tea for one mentioned, do I just install it on a USB stick with Etcher, and it's ready to run?

---

### Post by rbmorse on 2021-02-22
IF...IF the new SSD is smaller capacity than the original HD, don't use Clonezilla to attempt the transfer.  It can do that, but the process is considered an "advanced operation" and probably not the best course of action for someone who is not comfortable with even the basic installation of Clonezilla.

take a look at "Rescuezilla"  It's a Clonezilla alternative that's fully GUI and I find it a lot easier to work with.  For info:

[https://sourceforge.net/projects/rescuezilla/](https://sourceforge.net/projects/rescuezilla/)  

There's a link to the github page there for the actual download.

---

### Post by C.S.Cameron on 2021-02-22
Clonezilla is too hard for me, 
I use Gnome-Disks which comes with Ubuntu to create image files.
Open Disks, select the drive to clone, click Drive Options icon and follow the instructions.
No need for special software when restoring the image.
In Ubuntu use mkusb, Disks, Etcher, MultiBootUSB or dd, etc. to flash the .img file to disk.
In Windows use Rufus, Etcher, Win32DiskImager, MultiBootUSB, etc. to flash the .img file to disk.

For more information see: [https://askubuntu.com/questions/1300540/how-to-duplicate-a-ubuntu-system-for-distribution](https://askubuntu.com/questions/1300540/how-to-duplicate-a-ubuntu-system-for-distribution)

---

### Post by robert99999 on 2021-02-22
The new SSD is 125GB. The existing internal HD is 85GB, which probably gives you some idea of how old this computer is (2007 HP Compaq notebook). Anyway, the new drive is bigger than the old one. So, I don't have to worry about that problem.

As I type this, I'm downloading Rescuezilla. I also had a look at the Gnome disk utility. I'm a bit confused (I'm easily confused). From what is see in both the Gnome disk utility and on the Rescuezilla webpage, regardless of which software I use, cloning the internal drive appears to be a two step process:
1. Create an iso image file of the disk to be copied.
2. Restore the image file to the new disk.
If that's the case, then where do I store the iso image file? It will be bigger than any spare media that I have, unless I burn it to a DVD. I don't think I've burned a DVD in the last 10 years.

Thanks for your patience.

---

### Post by C.S.Cameron on 2021-02-23
If you want to clone a disk to a larger disk directly, **dd** is the way to go.

The basic code is:

sudo dd if=/dev/sda of=/dev/sdb

Where sda is the disk you want to clone and sdb is the target disk.

Run dd from a Live Ubuntu USB or DVD, not from the disk you are trying to copy.

Do some research before using dd, a single typo can wipe out your operating system.

It is sometimes refereed to as **D**isk **D**estroyer.

---

### Post by robert99999 on 2021-02-23
I just tried dd using the dd command line from the previous post. It  copied all of the files, but the target disk is not bootable. When I use  the Gnome disk utility to compare it to the existing HD, I see that the  old HD has these partitions listed:
Filesystem Partition 1 537MB FAT
Filesystem Partition 2 538MB FAT
Filesystem Partition 3 79GB
Filesystem Partition 5 79GB Ext4

The new SSD just shows this:
Filesystem 120GB

So, apparently I need to do more than just use the above dd command.

---

### Post by sudodus on 2021-02-23
I use Clonezilla, but if I understand correctly, you want a *simple* cloning tool. Like C.S.Cameron I would recommend *Disks* alias *gnome-disks*, which is safer than using *dd* as the first choice. But it is possible with dd too. It will do the job, when you tell it what to do correctly.

But there are other obstacles too.

- The target drive's size should be smaller than that of the original drive. This is a problem for you.

- The physical sector size on the target drive, the SSD, should be the same as on the the original drive, the HDD.

- If the drive sizes are different, and the partition table is GPT, you must also repair the backup partition table at the end of the drive. (This is not necessary with the old MSDOS partition table.)

[This link](https://askubuntu.com/questions/958242/fastest-way-to-copy-hdd/958248#958248) can help you check the physical sector sizes and/or repair the backup partition table.

---

### Post by C.S.Cameron on 2021-02-23
537MB + 538MB + 79GB + 79GB is greater than 120GB.

Are you running Disks and dd from a Live Ubuntu USB? 

Running from the source disk will not work.

I assumed by HDD size the computer boots Legacy mode, if it boots UEFI mode see sudodus' link.

Edit:
@ajgreeny: Ahh yes, 537MB + 538MB + 79GB is less than 120GB. Good thinking.

---

### Post by ajgreeny on 2021-02-23
After all this angst and uncertainty in this thread I begin to wonder if it might not be many times simpler and quicker to backup all your personal files most of which are in your home and then simply install a new OS on the new SSD and restore those backed up home files.

I realise you will have to install any packages that are not in the default install but this may still be a faster way to get to your wanted end-point.

@C.S.Cameron
The disk size problem you mention will, I suspect be because this is a BIOS  disk and partition 5 is a logical partition sitting in partition 3, an extended partition.

---

### Post by mastablasta on 2021-02-23
> **robert99999 said:**
> 
Example: menu choice of computer processors: AMD64, i686-pae, or i686. I'm pretty sure that it's not an AMD64 because my computer has an "Intel Inside" sticker. And I do know that it's 64-bit. But that's the limit of what I know about the processor.


AMD64 = 64 bit CPU - AMD64  is in image name because AMD was the first to have such CPU on consumer market.
i686-pae = 32 bit CPU, but has 4 GB or more ram. it needs PAE (Physical Address Extension) kernel to recognise more than 4 GB ram (up to 64GB). same thing on windows.
or i686 = 32 bit CPU but has less than 4 GB ram and maybe is so old (or has some other limitation put on the CPU by manufacturer - e.g. Pentium M) that it does not support PAE kernel .

I believe it is same for windows. you need to know what kind of version will run and forcing a 64bit one on 32bit machine won't work. and if you have winxp 32 bit home, you need to add windows pae kernel to get 4 Gb ram (even on windows this means 1 GB is reserved for OS functions)

aside from what others already said if you still want to do disk to disk then this is the step by step by clonezilla: 
[https://clonezilla.org/show-live-doc-content.php?topic=clonezilla-live/doc/03_Disk_to_disk_clone](https://clonezilla.org/show-live-doc-content.php?topic=clonezilla-live/doc/03_Disk_to_disk_clone)

print and go -- step by step. no, interface is not the easiest.

i would do a new install on SSD and then just move over the data from hard disk. or you can buy a sata enclosure and use the hard disk as external data source. you need to setup trim on SSD.

---

### Post by robert99999 on 2021-02-23
After I made my last post late last night (early this morning), I came to the same conclusion as the above two posts: Just do a new install on the new SSD, and then manually copy the other files over. So that's what I did. However, I then spent hours today trying to set my preferences the way I had them on my original HD. Even though I've only been using Ubuntu on this machine for two months, it's amazing how many settings I've modified in that time. And trying to remember where to change them wasn't easy: Settings? Tweaks? or somewhere else? But the real showstopper was that I found there was no simple way to get all of my bookmarks and login passwords transferred over from the old Firefox installation to the new one. Similar problem with my email client. Couldn't figure out how to restore all of my emails. I thought maybe I could find where these files were located on the old HD and copy them over, but when I tried to do that, Firefox immediately had a hissy fit.

So, I decided to have another look at cloning the drive. When I used "Show Applications" to find Gnome Disks again, I saw the "Startup Disk Creator" app which I'd never noticed before. All it needed was an iso image of the disk to be copied. So, I fired up Balena Etcher to do that (thinking I'd just burn it to a DVD), but then discovered that Etcher was quite happy to do a direct image copy from the HD to the SSD without the need to make an intermediate iso file. So I did that. Twenty minutes later, I had the my old HD cloned onto the new SSD, and another 15 minutes to verify it. The only minor hitch was that the partitions were exactly the same size as the old HD, so the new SSD had an extra 40GB unassigned. All I had to do was run Gnome disks and expand the ext4 partition to take up the extra space. That was a two second operation. I'm now running from the new SSD and everything is exactly as I had it on the old HD, except of course the SSD is much much faster.

Thanks to everyone who responded. It is much appreciated.

---

### Post by CelticWarrior on 2021-02-24
> [COLOR=#000000]there was no simple way to get all of my bookmarks and login passwords transferred over from the old Firefox installation to the new one. Similar problem with my email client.[/COLOR]
The easiest way is to use sync with a Firefox account.
Without it and manually you can always copy over and replace the hidden folder where such settings are stored: [https://askubuntu.com/a/218451](https://askubuntu.com/a/218451)
Or [https://support.mozilla.org/en-US/kb/restore-bookmarks-from-backup-or-move-them](https://support.mozilla.org/en-US/kb/restore-bookmarks-from-backup-or-move-them)

---

### Post by ajgreeny on 2021-02-24
I can only assume that if all your configurations did not transfer to the new installation that you moved all your data but did not move all the hidden files and folders from your old home to the new one.

About 99% of all my personal settings and configs, including all the firefox and thunderbird folders and set up, including bookmarks, extensions, etc etc are transferred by moving all the hidden folders including the ***.mozilla*** and ***.thunderbird*** folders.
I use a separate /home partition so on reinstall everything is automatically used by the new OS; worth considering if you now have the space available.
Some users leave the home folder in the root partition but then use symbolic links to all the data which is in a separate /data partition; easy to do but a little more involved than a separate /home partition.

Assuming you still have all the old hidden folders from your /home you should still be able to restore all the old configs easily enough.

---

### Post by robert99999 on 2021-02-24
> **ajgreeny said:**
> I can only assume that if all your configurations did not transfer to the new installation that you moved all your data but did not move all the hidden files and folders from your old home to the new one.

Good point. When I did the transfer I just did a Select All, and dragged them over, but probably forgot to have the Show Invisibles option selected. Since I'm still quite new to Linux, I'm not yet familiar with the places where Linux keeps its various files

---

### Post by C.S.Cameron on 2021-02-24
You will also find that both your new and old drives now have the same UUID's, so it can be a little bit dangerous to operate the computer with both disks plugged in at the same time.
GParted has an option to create new UUID's. If you change the UUID of a root partition you may also need to update it's fstab and grub.cfg files also.

---

### Post by robert99999 on 2021-02-24
Thanks. That's good to know. I don't expect to have them both plugged in at the same time. I'll probably keep the old HD as an emergency backup for now. Once I get more familiar with how things work, and have more spare time, I'll probably reformat the old HD, and will deal with the uuid at that time.

> **CelticWarrior said:**
> The easiest way is to use sync with a Firefox account.
Yeah, I know. Every site on the planet wants me to sign up for an account, so that they can track my every move, and I'm to stubborn to submit.

---

### Post by cmcanulty on 2021-03-01
Also before you ditch the old setup go to synaptic and click file- save markings as and click the lower left box save full state . Name the file something you can find easily. Then after getting the new disk going find that file and in synaptic click file- read markings. Gets most programs and settings. it always misses chrome and google earth and a few others. But that is probably because I am missing something dumb. If someone knows how to include everything in that deal please post it here. really saves time and aggravation.And always have home in a separate partition makes this much easier.

---

### Post by VMC on 2021-03-02
Two files on Firefox has all your passwords:
under .mozilla/default-release
**key4.db** and **logins.json**

---

### Post by mastablasta on 2021-03-03
> **robert99999 said:**
> Good point. When I did the transfer I just did a Select All, and dragged them over, but probably forgot to have the Show Invisibles option selected. Since I'm still quite new to Linux, I'm not yet familiar with the places where Linux keeps its various files

it happened to me as well.

the think is that hidden folders are hidden because you usually do not need to see them. they just get in the way. but they are there if you want to access them (e.g. for some manual config).

When i upgrade with fresh install i would pick which hidden folder i will move and which ones i won't move and would use new config instead.  if oyu move them to upgraded version they might give problems. but on same version transfer you can just copy them over defaults

---

### Post by Paulgirardin on 2021-03-03
Chrome and google earth are installed via PPA not through Apt ,if I'm not mistaken,and that is why it won't reinstall them.

---

### Post by Paulgirardin on 2021-03-03
Firefox and Thunderbird stores the user profile (including mail) in the "defaults" directory (/home/your_name/.thunderbird/12345abc.default-release). Just copy it to the new install /home/your_name/.thunderbird directory.
In Thunderbird I think you need to note the name of the new installation "defaults" directory and rename it to something like "old12345abc.default-release" ,copy the one from the previous installation you wish to use ,then rename it to the name you took note of (12345abc.default-release).
This is what I do after every OS upgrade.

---

### Post by ajgreeny on 2021-03-03
> **Paulgirardin said:**
> Chrome and google earth are installed via PPA not through Apt ,if I'm not mistaken,and that is why it won't reinstall them.
PPAs still make use of apt; they are just additional repositories, and once enabled are seamless in their use.

Not sure about installing chrome or google-earth; I've never used either.

---

